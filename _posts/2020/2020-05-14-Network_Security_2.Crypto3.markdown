---
layout: post
title: "네트워크보안 2.암호화3"
date: 2020-05-14 16:01:35 +0900
categories: school
author: "CodeJin19"
---

# 암호화

## Symmetric Key

앞으로 살펴볼 대칭키 암호화 (Symmetric Key) 는 지난 번에 공부했던 Substitution과 Transposition을 활용한 암호화 방법이다.

<br>

## One-Time Pad

One-Time Pad에서는 암호화에 xor($$\oplus$$) 연산을 사용한다. xor 연산의 특징은 원문에서 같은 값으로 xor 연산을 두 번 하면 원문으로 돌아온다는 점이다. 이를 활용하여 암호화와 복호화를 진행한다.

<br>

$$\oplus$$연산 논리표

||0|1|
|0|0|1|
|1|1|0|

<br>

예를 들어 "heil hitler"라는 평문을 암호화하는데, 이 때 각 알파벳은 다음의 비트로 인코딩한다고 하자.

<br>

|e|h|i|k|l|r|s|t|
|000|001|010|011|100|101|110|111|

<br>

암호화

||h|e|i|l|h|i|t|l|e|r|
|platin text|001|000|010|100|001|010|111|100|000|101|
|key|111|101|110|101|111|100|000|101|110|000|
|cipher text|110|101|100|001|110|110|111|001|110|101|
||s|r|l|h|s|s|t|h|s|r|

<br>

복호화1

||s|r|l|h|s|s|t|h|s|r|
|platin text|110|101|100|001|110|110|111|001|110|101|
|key|111|101|110|101|111|100|000|101|110|000|
|cipher text|001|000|010|100|001|010|111|100|000|101|
||h|e|i|l|h|i|t|l|e|r|

<br>

복호화2

||s|r|l|h|s|s|t|h|s|r|
|platin text|110|101|100|001|110|110|111|001|110|101|
|key|101|111|000|101|111|100|000|101|110|000|
|cipher text|011|010|100|100|001|010|111|100|000|101|
||k|i|l|l|h|i|t|l|e|r|

<br>

복호화3

||s|r|l|h|s|s|t|h|s|r|
|platin text|110|101|100|001|110|110|111|001|110|101|
|key|111|101|000|011|101|110|001|011|101|101|
|cipher text|001|000|100|010|011|000|110|010|011|000|
||h|e|l|i|k|e|s|i|k|e|

<br>

우선 암호화와 복호화1을 보면, One-Time Pad가 어떻게 암호화와 복호화를 하는지 알 수 있다.

<br>

복호화2와 복호화3을 보면, One-Time Pad의 특징을 알 수 있다. One-Time Pad의 특징으로는 key값을 적절하게 조절함으로써 주어진 Cypher Text로부터 어떠한 Plain Text도 만들어낼 수 있다는 것이다. 다른 암호화 알고리즘의 경우, Cypher Text를 다양한 키로 복호화한 결과들 중 어떤 하나는 다른 결과들보다 더 그럴듯한 Plain Text가 되기 때문에, Plain Text를 유추할 수 있다. 하지만 One-Time Pad는 다양한 Plain Text가 될 수 있기 때문에, 어떤 Plain Text가 맞는 것인지 알 수 없다. 따라서 One-Time Pad 알고리즘은 Provably Secure하고, 이 특징은 xor 연산 덕분이다.

<br>

One-Time Pad는 Secure함이 증명됐음에도 불구하고 잘 사용하지 않는다. 왜냐하면 One-Time Pad를 제대로 사용하기 위해서는, 매 통신마다 random한 Key값을 생성하여 한 번 쓰고 버려야 하기 때문이다. 키를 재사용할 경우의 문제점을 다음 상황을 통해 알아보자.

<br>

A가 B에게 $$P_1$$을 키 K로 암호화한 $$C_1$$ ($$C_1 = P_1 \oplus K$$)과 $$P_2$$를 같은 키 K로 암호화한 $$C_2$$ ($$C_2 = p_2 \oplus K$$)를 보낸다. 이 때, $$C_1$$과 $$C_2$$에 공격자 T가 접근했다면, 공격자 T는 $$C_1$$과 $$C_2$$를 갖고 다음 작업을 할 수 있다.\

<br>

$$
\begin{align*}
C_1 \oplus C_2 = \left( P_1 \oplus K \right) \oplus \left( P_2 \oplus K \right)
\end{align*}
$$

$$
\begin{align*}
C_1 \oplus C_2 = \left( P_1 \oplus P_2 \right) \oplus \left( K \oplus K \right)
\end{align*}
$$

<br>

같은 값으로 xor연산을 두 번 하면 상쇄되므로,

<br>

$$
\begin{align*}
C_1 \oplus C_2 = \left( P_1 \oplus P_2 \right)
\end{align*}
$$

<br>

공격자 T는 $$P_1$$과 $$P_2$$의 xor 연산의 결과를 얻게된다. 공격자는 Plain Text를 바로 알 수는 없지만, $$P_1$$이나 $$P_2$$에 중 하나라도 안다면 나머지 Plain Text들은 손쉽게 볼 수 있다. 결국 One-Time Pad는 키를 재사용할 수 없다는 큰 단점이 있다.

<br>

One-Time Pad는 통신하는 양측이 같은 키를 타인에게 누출되지 않고 안전하게 공유해야하며, 매 통신마다 새로운 키를 공유해야한다. 그런데 문제는, 키의 크기가 통신하는 데이터와 같은 크기여야 한다는 것이다. 결국, 통신하는 데이터와 같은 크기의 키를 매번 안전하게 공유하는 과정이 필요한데, 이 때 키가 아닌 데이터를 안전하게 공유하면 된다는 문제가 생긴다. 이런 모순 때문에 One-Time Pad는 잘 사용하지 않는다.

<br>

## Codebook Cipher

One-Time Pad나 Substitution은 알파벳을 알파벳으로 1대1 치환하는 방식이고, Trnasition은 알파벳의 위치를 섞는 방식이라면, Codebook Cipher는 알파벳이 아닌 단어를 숫자에 1대1 대응 시키는 방식이다. 예를 들어, "안녕하세요, 여러분"에서 "안녕하세요"를 10, "여러분"을 27이라 한다면, 암호문은 "10, 27"이다. 이 방법은 통신하는 쌍방이 같은 사전(Codebook, 숫자와 단어가 정리되어 있는 책)을 공유하고 있어야 한다.

## Summary

 - Symmetric Key (대칭키)

   - 암호화, 복호화에 사용하는 키가 같은 암호화 방식

   - Stream Cipher

     - AES

   - Block Cipher

     - One-Time Pad와 비슷

     - random에 가까운 Key Stream을 만들어 활용

     - Key Stream을 생성하는 알고리즘을 공유함으로써 One-Time Pad의 단점을 극복했다.

 - Asymmetric Crypto (비대칭키)

   - Public Key와 Private Key, 두 가지 키를 사용

   - Private Key로 암호화하는 것을 서명한다고 한다