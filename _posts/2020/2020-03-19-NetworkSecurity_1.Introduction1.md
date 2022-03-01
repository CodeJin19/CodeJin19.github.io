---
title: "네트워크보안 1.개요1"
categories:
  - school
tags:
  - school
  - network_security
date: 2020-03-19 21:14:11 +0900
last_modified_at: 2020-03-19 21:14:11 +0900
---

# 네트워크 보안 개요

네트워크 보안에 대한 이해를 돕기 위해, 은행과 고객 그리고 은행을 공격 (해킹) 하려는 해커가 있다고 가정하자. 이들 각각의 security concern은 무엇일지 생각해보자.

- Security Conern (보안 문제, 보안 경고)

<br>

예를 들어, 은행 고객이 다른 사람에게 송금하는 상황에서의 security concern으로는 다음과 같은 점들이 있을 것이다.

1. 10만원을 송금했는데, 20만원이 출금 됐다.

2. Steve한테 송금해야하는데, 다른 사람이 받았다.

3. 다른 은행, 사람들이 이 고객이 송금했다는 사실을 알았다.

<br>

등등이 있을 것이다. 한편, 은행의 security concern으로는 고객에게 24시간 서비스를 제공해야 한다는 등이 추가적으로 있을 수 있다.

<br>

## CIA

네트워크 보안에 중요 요소에는 Confidentiality, Integrity, Availability 가 있으며, 이 세 요소를 묶어서 CIA라고 한다.

- CIA

  - Confidentiality (기밀성)

  - Integrity (무결성)

  - Avialability (가용성)

<br>

### Confidentiality

Confidentiality는 인가되지 않은 사람이 데이터를 읽을 수 없게 하는 성질이다. 이를 위해 데이터를 암호화한다.

<br>

### Integrity

Integrity는 허가되지 않은 데이터의 조작을 알아채는 성질이다. 이를 위해 데이터를 암호화한다.

Integrity의 또 다른 특징은 데이터의 조작을 방지하는 것이 아니라, 허가되지 않은 데이터의 조작을 탐지한다는 것이다.

<br>

### Availability

Abailability는 필요한 때라면 언제든지 데이터에 접근 가능할 수 있는 성질이다.