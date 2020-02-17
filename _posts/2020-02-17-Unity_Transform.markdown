---
layout: post
title:  "유니티 트랜스폼"
date:   2020-02-17 15:07:31 +0900
categories: unity
author: "CodeJin19"
---

Transform

오브젝트의 위치, 회전, 스케일을 나타내는 컴포넌트로, 모든 오브젝트는 Transform을 갖고 있다. (설령 EmptyObject라 하더라도) 따라서 모든 오브젝트는 transform이라는 변수를 갖고 있기 때문에 따로 변수를 선언할 필요없다.

- 클래스 함수

  - function Translate (translation : Vector3, relativeTo : Space = Space.Self) : void

  - function Translate (x : float, y : float, z : float, relativeTo : Space = Space.Self) : void

  - function Translate (translation : Vector3, relativeTo : Transform) : void

  - function Translate (x : float, y : float, z : float, relativeTo : Transform) : void

Translate 클래스 함수로 오브젝트를 이동시킬 수 있다. 이동방향을 Vector를 매개변수로 받거나, 각 축의 이동 거리에 대해 float형으로 받을 수 있다.


[유니티 홈페이지의 트랜스폼 문서](https://docs.unity3d.com/kr/530/ScriptReference/Transform.html)
