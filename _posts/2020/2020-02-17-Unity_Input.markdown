---
layout: post
title:  "유니티 입력받기"
date:   2020-02-17 15:07:31 +0900
categories: unity
author: "CodeJin19"
---

유니티에서 사용자에게 입력받기

- Input 클래스

  - Unity 내에서 입력을 관리하는 클래스

<br>

- 클래스 변수

  - static var anyKeyDown : bool

    - 최초로 입력을 받은 프레임에 true

  - static var anyKey : bool

    - 입력을 받는 중이면 true

<br>

- 클래스 함수

  - static function GetKey (name : string) : bool

  - static function GetKeyDown (name : string) : bool

  - static function GetKeyUp (name : string) : bool

  - static function GetButton (buttonName : string) : bool

  - static function GetButtonDown (buttonName : string) : bool

  - static function GetButtonUp (buttonName : string) : bool

  - static function GetMouseButton (button : int) : bool

  - static function GetMouseButtonDown (button : int) : bool

  - static function GetMouseButtonUp (button : int) : bool

<br>

유니티에서는 버튼을 눌렀다 떼는 것을 3 가지로 나눈다.

1. 누르는 프레임 (Down)

2. 누르고 있는 프레임 (Stay)

3. 떼는 프레임 (Up)

위의 클래스 함수들 역시 각각 3 가지 상황에 대한 함수들이다.

GetKey 클래스 함수의 경우, name을 매개변수로 받는데, Input Manager를 참조하거나, KeyCode를 참조하면 된다.

GetButton 클래스 함수의 경우, buttonName을 매개변수로 받는데, Input Manager를 참조하면 된다.

GetMouseBoutton 클래스 함수의 경우, int형 정수를 매개변수로 받는데, 마우스 좌클릭은 0, 우클릭은 1이다.


[유니티 홈페이지의 키코드 문서](https://docs.unity3d.com/kr/530/ScriptReference/KeyCode.html)
