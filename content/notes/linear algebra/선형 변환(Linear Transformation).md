---
title: "선형 변환(Linear Transformation)"
date : "2023-01-19"
---

## 선형 변환(Linear Transformation)

> : 함수의 다른 말. 공간 상에서 선형으로 변환되는 걸 상상하라.

$y = 3x + 1$ 처럼, bias가 붙어 있는 것은 선형 변환이 아니라 affine 변환이다.

![](notes/images/스크린샷%202023-01-10%20오후%205.44.42.png)
Standard basis vector를 하나하나 다 넣어보면 $T(x)$를 알 수 있다.
위의 수식에서, **Transformation을 가하는 순서에 상관없이 값이 동일하다.

## Linear Transformation in Neural Networks

![](notes/images/스크린샷%202023-01-10%20오후%205.58.07.png)

상수벡터가 끼어있으면 Affine Transformation
column combination으로 선형변환으로 바꿀 수 있다!
→ 1을 추가해주면 선형변환으로 바꿀 수 있다.