---
title: "머신러닝 기초2"
categories:
  - machine_learning
tags:
  - machine_learning
  - neural_network
  - artificial_neural_network
  - ann
  - perceptron
  - TIL
date: 2020-09-08 17:23:57 +0900
last_modified_at: 2022-06-04 14:57:57 +0900
---

# 머신러닝 기초

## 퍼셉트론

퍼셉트론은 다수의 신호를 입력받아 하나의 신호를 출력하는 알고리즘이다.

<br>

![perceptron](/images/2020/2020-09-08-MachineLearning_3.Basic2_1.perceptron.jpg)

<br>

위 이미지는 두 개의 입력을 받는 퍼셉트론이다.

퍼셉트론은 $$x_1$$, $$x_2$$을 입력받아 각 입력값에 $$w_1$$, $$w_2$$의 가중치를 곱한다.

이 결과값이 임계값 $$\theta$$ 이상인 경우, 1을 출력하고,

미만인 경우 0을 출력한다.

이를 간단히 표현하면 다음과 같은 식이 된다.

$$
\begin{align*}
y = \cases{
    0\qquad\text{if }\quad w_1x_1 + w_2x_2 \le \theta \cr
    1\qquad\text{if }\quad w_1x_1 + w_2x_2 \gt \theta
}
\end{align*}
$$

<br>

## and 게이트 퍼셉트론

and 게이트 역활을 하는 퍼셉트론을 만든다고 해보자.

and 게이트의 진리표는 아래와 같이 $$x_1$$과 $$x_2$$가 모두 1인 경우에만 출력값이 1이다.

<br>

![truth_table](/images/2020/2020-09-08-MachineLearning_3.Basic2_2.truth_table.jpg)

<br>

가중치 $$w_1$$, $$w_2$$와 임계값 $$\theta$$를 어떻게 조절해야 and 게이트 진리표와 같은 결과값이 나올까?

답은 간단하다.

$$
\begin{align*}
(w_1, w_2, \theta) = (1, 1, 1.5)
\end{align*}
$$

<br>

## 신경망과 딥러닝

다수의 퍼셉트론이 모여 한 층의 신경망을 이루고, 이를 레이어라 부른다.

이 레이어가 하나인 경우, 단일 레이어 퍼셉트론이라고 부르며,

반대로 레이어가 복수일 경우, 심층 신경망이라고 부른다.

심층 신경망을 사용하는 머신러닝 알고리즘을 딥러닝이라 한다.
