---
title: 'JAVA 업그레이드 하기'
categories:
  - JAVA
tags:
  - JAVA
date: 2023-05-18 23:09:55 +0900
last_modified_at: 2023-05-18 23:09:55 +0900
---

# JAVA 업그레이드하기

최근 Spring 공부를 다시 시작하기 위해 인강을 시작했다.

강의를 시작하기에 앞서 JAVA11을 설치하랬는데, 확인해보니 내 컴에 설치된 건 JAVA8..

영상을 킨 지 2분도 채 안 되서 영상을 멈추고 부랴부랴 JAVA11을 설치했다.

<br>

## 설치 방법

### JAVA 버전 확인

먼저 JAVA 버전을 확인한다.

CMD창에서 `java -version`으로 설치된 JAVA 버전을 확인할 수 있다.

<br>

### jdk 설치

[open jdk 아카이브 사이트](https://jdk.java.net/archive/)에 접속하여 원하는 jdk를 다운받는다.

다운받은 압축파일을 원하는 위치에 푼다.

나는 C:\Program Files\JAVA\jdk-11.0.0.1에 풀었다.

<br>

### 환경변수 설정

고급 시스템 설정을 연다.

1. 시작에서 "고급"으로 검색하여 열 수 있다.
2. 제어판 > 시스템 > 고급 시스템 설정으로 열 수 있다.

환경변수에 JAVA_HOME이 없다면 아래와 같이 추가를, 있다면 변경한다.

변수 이름 : JAVA_HOME

변수 값 : jdk 압축 파일을 푼 위치 (C:\Program Files\JAVA\jdk-11.0.0.1)

그리고 Path에 %JAVA_HOME%\bin도 업데이트한다.

<br>

끝!
