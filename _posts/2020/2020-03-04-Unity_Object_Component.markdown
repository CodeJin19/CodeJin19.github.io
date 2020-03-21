---
layout: post
title: "유니티 물체 컴포넌트"
date: 2020-03-04 20:42:14 +0900
categories: unity
author: "CodeJin19"
---

RigidBody

물리효과를 받기 위한 컴포넌트1, Rigidbody 컴포넌트를 추가할 경우, 물체는 중력을 받는다

- RigidBody 컴포넌트 요소

  - Mass : 물체의 질량

  - Use Gravity : 중력의 영향을 받는지의 여부로 default는 체크되어 있다

  - Is Kinematic : 외부의 물리 현상에 영향을 받는지 여부로 체크되어 있으면 외부 물리 현상을 무시한다

Collider

물리효과를 받기 위한 컴포넌트2, 물체의 충돌경계를 설정하는 컴포넌트이다. 물체 생성시, 물체와 같은 크기로 설정되어 있으며, 연두색으로 표시된다.

Material

객체의 표면 재질을 결정하는 컴포넌트

- Material 컴포넌트 요소

  - Albedo : 객체의 색상

    - Albedo 좌측의 흰색 네모 칸에 이미지 삽입 시, 객체에 이미지 적용

    - 이러한 이미지를 textrue라고 한다

  - Metalic : 객체 표면의 금속 재질 정도

  - Smoothness : 빛 반사 정도

  - Tiling : Texture 반복 타일 개수

  - Emission : Texture 밝기 조절

Physics Material

탄성과 마찰을 다루는 재질로, create에서 만들 수 있다. 여태까지 리한 내용들은 객체의 기본적인 컴포넌트이지만, Physics Material은 컴포넌트는 아니다.

- Physics Material 요소

  - Bounciness : 튀는 탄성

  - Bounciness Combine : 다음 탄성값 (아마 물리의 e이지 않을까...)

  - Static Friction : 정지 마찰력

  - Dynamic Friction : 운동 마찰력

  - Friction Combine : 다음 마찰력
