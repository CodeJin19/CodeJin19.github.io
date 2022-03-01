---
title: "유니티 물체 운동"
categories:
  - unity
tags:
  - unity
  - moving_objects
date: 2020-03-06 19:44:50 +0900
last_modified_at: 2020-03-06 19:44:50 +0900
---

RigidBody

- RigidBody Property

  - public Vector3 velocity;

    - 객체의 속도

<br>

- RigidBody Public Method

  - public Component GetComponent(Type type);

    - Component의 정보들을 받아온다

  - public void AddForce(Vector3 force, ForceMode mode = ForceMode.Force);

    - 객체에 force vector로 힘을 준다

  - public void AddTorque(Vector3 torque, ForceMode mode = ForceMode.Force);

    - 객체에 torque방향을 축으로 회전력이 생긴다

<br>

- ForceMode Property
    
  - Force

    - 객체의 질량과 유관하게 지속적으로 힘을 적용

  - Accelartion

    - 객체의 질량과 무관하게 지속적으로 힘을 적용

  - Impulse

    - 객체의 질량과 유관하게 힘을 한 번 적용

  - VelocityChange

    - 객체의 질량과 무관하게 힘을 한 번 적용

<br>

```C#
using UnityEngine;

public class MyBall : MonoBehaviour
{
    Rigidbody object;

    void start ()
    {
        object = getComponent<Rigidbody> (); //Rigidbody class object 변수에 객체의 rigidbody 정보들이 대입
    }
}

```

<br>

Unity에서는 RigidBody 관련 코드는 Update 영역보다는 FixedUpdate 영역에서 작성하는 것을 권장한다. FixedUpdate영역이 더 안정적이라고 한다.
