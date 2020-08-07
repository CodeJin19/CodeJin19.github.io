---
title: "시스템프로그래밍 1. Basic1"
categories:
  - school
tags:
  - school
  - system_programming
  - compile
date: 2020-04-09 20:55:40 +0900
last_modified_at: 2020-04-09 20:55:40 +0900
---

# C, Assambly, Machine Code

- Turning C into Object Code

  - C program (p1.c p2.c) / text

    - Compiler (gcc -Og -S) 에 의해 어셈블리 파일 생성

  - Asm program (p1.s p2.s) / text

    - Assembler (gcc or as) 에 의해 오브젝트 파일 생성

  - Object program (p1.o p2.o) / binary

    - Linker (gcc or ld) 에 의해 실행 파일 생성

  - Executable program (p) / binary

<br>

# Assembly Characterisics : Operations

- 레지스터나 메모리에 있는 데이터에 대해 계산 수행

- 메모리와 레지스터간의 데이터 전송

- 프로그램 진행 컨트롤

<br>

# Object Code

- 어셈블러

  - 어셈블리 파일을 오브젝트 파일로 변경한다

  - 각 명령어에 대해 바이너리 인코딩을 한다

- 링커

  - 여러 오브젝트 파일들을 하나로 합쳐 실행파일로 엮는다

  - 오브젝트 파일이 참조한 라이브러리들도 엮어준다

  - 동적 링킹과 정적 링킹이 있다

<br>

# Machine Instruction Example

|언어|코드|설명|
|:---:|---|---|
|C|*dest = t;||
|Assembly|movq %rax, (%rbx)||
|Object Code|0x40059e: 48 89 03|3바이트 명령어<br>0x40059e에 저장|