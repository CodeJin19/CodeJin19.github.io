---
layout: post
title: "네트워크보안 3.대칭키 암호화2"
date: 2020-05-17 16:39:15 +0900
categories: school
author: "CodeJin19"
---

# 대칭키 암호화

### Feistel Cipher

 - Feistel cipher는 블록 암호화의 한 종류이다.

 - Encryption

   - Plaintext를 두 부분으로 자른다 $$P = (L_0, R_0)$$

   - 매 라운드 계산은 다음과 같다

    $$L_i = R_{i - 1}$$

    $$R_i = L_{i - 1} \oplus F(R_{i - 1}, K_i)$$

   - 이 때 F는 round function이고, $$K_i$$는 subkey다

   - n번의 계산 후, ciphertext $$C = (L_n, R_n)$$를 얻는다

 - Decryption

   - $$C = (L_n, R_n)$$으로 시작한다

    $$R_{i - 1} = L_i$$

    $$L_{i - 1} = R_i \oplus F(R_{i - 1}, K_i)$$

   - 마찬가지로 n번의 계산 후, plaintext $$P = (L_0, R_0)$$를 얻는다

   - 함수 F가 어떤 함수여도 Feistel Cipher는 작동하지만, 특정 함수만이 취약점이 없다

<br>

## Data Encryption Standard

1971년에 IBM사에서 개발한 Lucifer 암호 알고리즘을 개량하여 만들었고, 미 국가안보국이 검증하여 국가 표준 암호 알고리즘으로 사용됐다. DES의 바탕이 되는 알고리즘이 Feistel cipher며, 64비트 블록 길이에 키는 56비트다. DES에서는 S-Box라는 치환 단계가 있는데, DES의 보안이 S-Box에 의존한다.

<br>

DES 발표 당시, 미 국가안보국이 키를 56비트로 줄이면서 많은 사람들이 DES에 취약점이 있을 것이다고 의심했다. (보통 키의 길이가 늘어야 보안이 강화되기 때문에) 그렇게 30년이 넘게 DES의 취약점을 찾았지만 이렇다 할 취약점은 찾지 못했다고 한다.

<br>

## Notation

앞으로의 설명을 쉽게 하기 위해 표기법을 정리하겠다.

 - $$P$$ : Plaintext block

 - $$C$$ : Ciphertext block

 - $$C = E(P, K)$$ : Plaintext P를 키 K로 암호화한 ciphertext C

 - $$P = D(C, K)$$ : Ciphertext C를 키 K로 복호화한 plaintext p

 - $$P = D(E(P, K), K)$$ : 같은 키 K로 plaintext를 암호화하고 복호화하면 다시 plaintext p를 얻을 수 있다

 - $$C = E(D(C, K), K)$$ : 반대도 마찬가지

 - 단 위의 두 식은 암호화와 복호화에 사용하는 키 K가 같아야 한다

<br>

## Triple DES

간단히 말해서 DES를 3번 더 하는 것이다.

$$
\begin{align*}
C = E(D(E(P, K_1), K_2), K_1)\\
P = D(E(D(C, K_1), K_2), K_1)
\end{align*}
$$

triple DES 공격을 위해서는 $$2^{112}$$가지의 키를 모두 찾아야 하는데, 오늘날에는 $$2^{112}$$는 충분히 공격할만한 크기기 때문에 공격에 취약하다

<br>

### Why 2 keys?

키를 두 가지로 쓰는 이유는 single DES만 구현된 곳과 triple DES가 구현된 곳이 서로 통신할 때를 위해서이다. 이 경우, triple DES 연산에서 암호화, 복호화, 암호화 연산을 하나의 키로만 하면 암호화 복호화가 상쇄되어 single DES가 된다.

$$
\begin{align*}
C = E(D(E(P, K_1), K_2), K_1)\\
C = E(D(E(P, K_1), K_1), K_1)\\
C = E(P, K_1)
\end{align*}
$$

<br>

### Why not $$C = E(E(P, K), K)$$?

같은 키로 double DES를 하는 경우, 우선 키의 전체 경우의 수인 $$2^{56}$$가지의 탐색을 하고, 각각의 키에 대해 암호화를 한 번 더 연산하면 된다. 즉 같은 키로 double DES를 할 때, 찾아야 하는 키의 길이는 $$2^{56} \times 2^{56} = 2^{112}$$가 아니라, $$2^{56} \times 2 = 2^{57} \approx 2^{56}$$이 된다.

<br>

### Why not $$C = E(E(P, K_1), K_2)$$?

Double DES가 아닌 triple DES를 사용하는 이유는 known plaintext attack 때문이다. 글로만 설명하면 복잡해지기 때문에 결론만 말하자면, known plaintext attack을 통해 double DES의 연산 횟수는 $$2^{56} \times 2^{56} = 2^{112}$$이 아니라, $$2^{56} + 2^{56} = 2^{57}$$이고, 같은 공격이라도 triple DES의 경우에는 $$2^{112}$$이기 때문에 double DES는 사용하지 않는다.