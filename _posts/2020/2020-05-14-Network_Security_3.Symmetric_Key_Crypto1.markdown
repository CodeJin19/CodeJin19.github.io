---
layout: post
title: "네트워크보안 3.대칭키 암호화1"
date: 2020-05-14 17:47:17 +0900
categories: school
author: "CodeJin19"
---

# 대칭키 암호화

## Symmetric Key Crypto

 - Stream Cipher

   - One-Time Pad와 비슷한 개념이다

   - Key를 입력받아 특정 알고리즘을 사용하여 keystream을 만든다

   - 생성된 keystream으로 plaintext를 암호화한다

 - Block Cipher

   - Codebook과 비슷한 개념이다

   - 수 많은 codebook들이 있으며, 이 때 key는 이 중 한 codebook을 가리킨다

   - key로 지정된 codebook을 활용하여 block 단위의 plaintext를 ciphertext로 암호화한다

<br>

## Stream Cipher

### RC4

RC4는 일련의 무작위 숫자를 생성하는 알고리즘이다. RC4는 한 번 연산한 결과값으로 숫자를 하나 출력하는데, 이를 n번 반복하여 n Byte의 key를 생성한다. 또한, RC4가 생성하는 숫자는 0 ~ 255 사이의 숫자이기 때문에 이 값은 1 Byte에 대응할 수 있다. RC4의 첫 번째 출력값부터 256번째 출력값까지는 보안에 취약하다는 사실이 밝혀졌지만, 257번째 출력값부터는 안전하다고 한다. 만드는 코드는 스킵하겠다.

<br>

그렇다면 RC4를 어떻게 활용하는 걸까. 통신하려는 쌍방이 같은 key값을 RC4에 입력하여 같은 keystream을 얻는다. 한 쪽은 이 keystream으로 암호화하고, 반대쪽은 이 keystream으로 복호화한다.

<br>

### Block Cipher

RC4가 반복하여 keystream을 생성했다면, Block Cipher는 암호화를 반복하여 cipher block을 생성한다. Block cipher는 n번의 라운드를 반복하여 암호화를 진행한다. 첫 라운드에서는 plaintext와 key를 입력받아 암호화한다. 이후 두 번째 라운드부터 매 라운드 key와 이전 라운드의 출력값을 입력받아 암호화한다. 
