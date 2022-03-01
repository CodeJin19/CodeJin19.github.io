---
title: "유니티 물체 충돌"
categories:
  - unity
tags:
  - unity
  - collision
date: 2020-03-09 17:39:25 +0900
last_modified_at: 2020-03-09 17:39:25 +0900
---

MeshRenderer

- MeshRenderer Property

  - public Material material

    - public Color color

<br>

Collision 

충돌 관련 클래스

<br>

- OnCollision Function

  - private void OnCollisionEnter (Collision collision)

    - 충돌이 시작될 때 호출되는 함수

  - private void OnCollisionStay (Collision collision)

    - 충돌이 지속될 때 호출되는 함수

  - private void OnCollisionExit (Collision collision)

    - 충돌이 끝났을 때 호출되는 함수

<br>

```C#
using UnityEngine;

public class MyBall : MonoBehaviour
{
    MeshRenderer mesh;
    Material mat;

    void start ()
    {
        mesh = getComponent<MeshRenderer> ();
        mat = mesh.material;
    }
}

```
