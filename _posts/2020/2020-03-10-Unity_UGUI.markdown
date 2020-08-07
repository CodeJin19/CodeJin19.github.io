---
title: "유니티 User Graphical User Interface 기초"
categories:
  - unity
tags:
  - unity
  - ui
  - gui
date: 2020-03-10 21:00:07 +0900
last_modified_at: 2020-03-10 21:00:07 +0900
---

UI

- UI

  - Canvas

    - UI가 그려지는 도화지 역활을 하는 컴포넌트

  - Text

  - Image

    - Source Image 적용이 필요하다

    - 적용할 이미지의 Texture Type은 Sprite로 설정해야 Image에 적용이 가능하다

  - Button

    - Interactable

      - 버튼의 활성화

    - Transition

      - 버튼의 반응 타입

      - Color Tint

        - 조건에 따른 색 변화

  - Anchor

    - UI 요소들은 Transform 컴포넌트가 아닌, Rect Transform (혹은 UI Transform)을 갖고 있는데, 여기서 Anchor를 활용해서 UI 요소들을 고정시킬 수 있다.
