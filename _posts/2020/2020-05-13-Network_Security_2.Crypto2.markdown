---
layout: post
title: "네트워크보안 2.암호화2"
date: 2020-05-13 20:45:36 +0900
categories: school
author: "CodeJin19"
---

# 암호화

## Secure & Insecure

 - Secure Cypher

   - 어떤 암호 알고리즘을 공격할 때, 가능한 모든 키를 대입하는 방법 (브루트 포스) 만이 유일한 공격 방법인 경우, 이 암호는 Secure하다고 한다.

 - Insucre Cypher

   - 어떤 암호 알고리즘을 공격할 때, 브루트 포스 방법보다 효율적인 방법이 있는 경우, 이 암호는 Insecure하다고 한다.

<br>

## Is all insecure cipher is easier to break then secure cipher?

그렇다면 Secure Cypher는 모든 Insecure Cypher보다 안전할까?

<br>

당연히(?) 답은 "아니다"이다. 예를 들어 Secure Cipher A와 Insecure Cipher B가 있다고 가정하자. A의 키 사이즈는 128비트이다. 그러면 128비트로 만들 수 있는 키의 개수는 $$2^{128}$$이다. B의 키 사이즈는 256비트로, 키의 개수는 $$2^{256}$$이다. A는 Secure Cipher이기 때문에, $$2^{128}$$가지를 모두 시도해야한다. 하지만 B는 Insecure Cipher라 어떤 천재 학자가 $$2^{256}$$가지를 모두 시도하는 대신, $$2^{230}$$가지를 시도하는 알고리즘을 찾았다. 이 경우, B는 Insecure Cipher지만 A보다 키의 개수가 훨씬 많다는 것을 알 수 있다. 즉, 어떤 Insecure Cypher는 Secure Cypher보다 더 안전할 수 있다.

<br>

## Double Transposition

저번 포스트에서 봤던 Substitution은 문자를 치환하여 암호화하는 알고리즘이었다. Transposition은 문자의 위치를 변환하는 암호화 알고리즘이다. 예를 들어 "attack at dawn"이라는 평문이 있다고 해보자. 이 평문을 아래와 같이 표에 배치하는 것이다. (x는 공백이다.)

<br>

||Col 1|Col 2|Col 3|
||:---:|---|---|
|Row 1|a|t|t|
|Row 2|a|c|k|
|Row 3|x|a|t|
|Row 4|x|d|a|
|Row 5|w|n|x|

<br>

그리고 위의 표의 행과 열의 순서를 뒤섞는다.

<br>

||Col 1|Col 3|Col 2|
||:---:|:---:|:---:|
|Row 3|x|t|a|
|Row 5|w|x|n|
|Row 1|a|t|t|
|Row 4|x|a|d|
|Row 2|a|k|c|

<br>

Transposition을 거친 암호문은 "xtawxnattxadakc"이고, 이 때 키는 (3, 5, 1, 4, 2)와 (1, 3, 2)이다.