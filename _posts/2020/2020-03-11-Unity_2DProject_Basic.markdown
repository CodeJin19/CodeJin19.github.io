---
layout: post
title: "유니티 2D 프로젝트 기초"
date: 2020-03-11 15:34:11 +0900
categories: unity
author: "CodeJin19"
---

- Main Camera

  - Size

    - 사이즈가 작을수록 줌 인 되어 물체가 크게 보인다

  - Projectrion

    - Orthographic

      - 원근법이 없는 정사영 투시

    - Perspective

<br>

- 2D Object

  - Order in Layer

    - 값이 클수록 전면에 보인다

<br>

- Sprite 파일

  - Pixels Per Unit

    - 이미지 크기에 맞춰 설정하면 된다

  - Filter Mode

    - 도트 이미지 같이 작은 용량의 경우 Point (no filter)로 설정하면 된다

  - Compression

    - 이미지의 압축관련 설정으로, 도트의 경우 None으로 설정하면 된다

<br>

프로젝트를 2D로 만들었기 때문에, Collider, Rigidbody 컴포넌트를 모두 2D 컴포넌트를 추가해야 한다.

충돌 시, 물체 간의 여백이 살짝 있는데, 이 때는

Edit -> Project Settings -> PHysics 2D -> Default Contact Offset

로 가서 Offset을 0으로 만들면 여백이 사라진다.