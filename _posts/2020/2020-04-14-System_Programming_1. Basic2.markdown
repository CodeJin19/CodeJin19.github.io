---
layout: post
title: "시스템프로그래밍 1. Basic2"
date: 2020-04-14 21:23:29 +0900
categories: school
author: "CodeJin19"
---

# Moving Data

Source에서 Data로 이동하는 명령어는 movq로, 다음과 같이 사용하면 된다.

- movq Source, Dest;

- 피연산자 타입

  - 상수

    - 예) $0x400, $-533

    - 앞에 $를 붙여준다
    
  - 레지스터

    - 예) %rax, %r13

    - 16레지스터들 중 하나를 사용한다

    - %rsp는 사용하지 않는다

    - 대부분의 레지스터는 특정 명령어를 위해 사용한다

  - 메모리

    - 예) (%rax)

    - 레지스터가 가리키는 메모리의 주소에 저장된 데이터로 8바이트에 저장된다

<br>

# movq Operand Combinations

|Source|Dest|Src, Dest|C Analog|
|:---:|:---:|---|---|
|Imm|Reg|movq $0x4, %rax|temp = 0x4;|
|Imm|Mem|movq $-147, (%rax)|*p = -147;|
|Reg|Reg|movq %rax, %rdx|temp2 = temp1;|
|Reg|Mem|movq %rax, (%rdx)|*p = temp;|
|Mem|Reg|movq (%rax), %rdx|temp = *p;|

<br>

메모리에서 메모리로의 데이터 이동은 한 명령어로 할 수 없다.

<br>

# Simple Memory Addressing Modes

- Normal &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(R) Mem[Reg[R]]

  - 레지스터 R이 가리키는 특정 메모리 값에 접근하는 경우

  - 예) movq (%rcs), %rax

<br>

- Displacement &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;D(R) Mem[Reg[R] + D]

  - 레지스터 R이 특정 메모리 구역의 시작위치를 가리키는 경우

  - R에서부터 D만큼 떨어진 메모리 값에 접근할 수 있다

  - 예) movq 8 (%rbp), %rdx

<br>

# Complete Memory Addressing Modes

- Most General Form

  - D(Rb, Ri, S) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Mem[Reg[Rb] + S * Reg[Ri] + D]

    - D : Constant "displacement"로 1, 2, 4바이트 중 하나

    - Rb : 베이스 레지스터

    - Ri : 인덱스 레지스터

      - %rsp는 사용 불가

    - S : 규모 : 1, 2, 4, 8 바이트 중 하나

<br>

- Special Cases

  - (Rb, Ri) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Mem[Reg[Rb] + Reg[Ri]]

  - D (Rb, Ri) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Mem[Reg[Rb] + Reg[Ri] + D]

  - (Rb, Ri, S) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Mem[Reg[Rb] + S * Reg[Ri]]
