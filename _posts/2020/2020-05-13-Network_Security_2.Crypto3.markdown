---
layout: post
title: "네트워크보안 2.암호화3"
date: 2020-05-13 20:45:36 +0900
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

하지만 One-Time Pad는 제대로 사용하기 어렵다. One-Time Pad를 제대로 사용하려면, 매 통신마다 random한 Key값을 생성하여 한 번 쓰고 버려야 한다. 왜냐하면 Key를 재사용하면, 

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