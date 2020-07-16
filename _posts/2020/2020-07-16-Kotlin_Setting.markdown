---
layout: post
title: "안드로이드 스튜디오 환경 에러"
date: 2020-07-16 18:28:00  +0900
categories: kotlin
author: "CodeJin19"
---

4달 만에 코틀린 공부를 시작하기 위해 안드로이드 스튜디오를 켰더니 밀린 업데이트가 한 가득이었다. 각종 업데이트를 하고나니 에러가 생겼다. 터미널에 'could not initialize class org.jetbrains.kotlin.gradle.plugin.sources.defaultkotlinsourcesetkt' 라는 에러 문구가 있었다. 구글신에게 물어보니, 안드로이드 스튜디오 4.0이 되면서 안드로이드 스튜디오의 코틀린 버전과 build.gradle의 코틀린 버전이 달라 생기는 문제라고 한다.

<br>

Tool - Kotlin - Configure kotlin plugin updates에서 버전을 확인하고, build.gradle에서 버전을 수정하면 해결된다...고 해서 따라했는데 나는 안 됐다. 외 나만 안되.... 결국 컴을 재부팅하고 새 프로젝트를 만드니, 새로 설치가 진행되면서 깔끔하게 해결됐다.

<br>

포맷이 답이다.