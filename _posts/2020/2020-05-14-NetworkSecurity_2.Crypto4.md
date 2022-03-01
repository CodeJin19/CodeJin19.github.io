---
title: "네트워크보안 2.암호화3"
categories:
  - school
tags:
  - school
  - network_security
  - crypto
date: 2020-05-14 17:26:54 +0900
last_modified_at: 2020-05-14 17:26:54 +0900
---

# 암호화

## Taxonomy of Cryptanalyses

 - Ciphertext Only

   - 대부분의 공격 상황
   
   - Ciphertext만 알고 있는 상황에서 Plaintext를 찾거나, 나아가 Key값을 찾는 것이 목표

 - Known Plaintext

   - Ciphertext 중 일부의 Plaintext를 알고 있는 경우

 - Choosen Plaintext

   - Lunchtime Attack이라고도 한다

   - 공격자가 입력한 Plaintext에 대해 암호화한 결과 Ciphertext, 두 가지를 아는 경우

 - Adaptively Choosen Plaintext

   - Choosen Plaintext와 같은 상황

   - Choosen Plaintext는 딱 하나의 Plaintext의 암호화한 값을 아는 상황이지만, Adaptively Choosen Plaintext는 두 쌍 이상의 Plaintext와 Ciphertext를 아는 상황이다

<br>

위 리스트에서 아래로 갈수록 공격자가 공격하기 쉬운 상황이다.

<br>

## Related Key

통신하는 데이터의 양이 많아지면, 데이터를 나누어 다수의 키로 암호화한다. 이 때 각 키들은 서로 연관성이 없어야 한다.

<br>

## Forward Search (Public Key Crpto)

사용자 A가 사용자 B에게 "Yes"를 B의 Public Key로 암호화해서 전송했다.

$$\left\{ M \right\}_B$$

공격자 T는 위의 ciphertext를 얻었고, plaintext가 "Yes", "No" 둘 중 하나라는 것을 안다. B의 public key로 암호화하는 것은 누구나 할 수 있으므로, 공격자 T는 "Yes"와 "NO"에 대해 B의 public key로 암호화한다. 이렇게 얻은 두 ciphertext를 위의 ciphertext와 비교하여 plaintext가 "Yes"임을 알 수 있다. 송신자가 제한된 값 중 하나를 수신자의 public key로 암호화하여 보낼 때, 공격자가 모든 경우의 수를 비교하여 plaintext를 알아내는 것을 forward search라 한다.

<br>

그렇다면 forward search는 어떻게 막을 수 있을까. A가 B에게 데이터를 전송할 때, plaintext 뒤에 쓰레기 값을 추가함으로써 forward search를 막을 수 있다.

$$\left\{ M + g \right\}_B$$

쓰레기 값을 추가하여 암호화한 결과는 공격자 T가 만든 $$\left\{ ``Yes" \right\}_B$$와 $$\left\{ ``No" \right\}_B$$와는 다르기 때문에 공격자 T는 A가 B에게 "Yes"를 보냈는지 "No"를 보냈는지 알 수 없다.