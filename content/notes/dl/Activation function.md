---
title: "Activation function"
date : "2023-01-19"
---
## Activation functions

![](notes/images/스크린샷%202023-01-10%20오후%2011.04.41.png)

> 입력 신호의 총합을 출력 신호로 변환하는 함수

-   `Sigmoid`
    -   • 출력 값을 0에서 1로 변경해줍니다(Squashes number to range [0, 1])
        -   단점: `Saturation` 문제
            -   Sigmoid 함수의 출력 그래프를 보면 입력 신호의 총합이 크거나 작을 때 기울기가 0에 가까워지는 것을 볼 수 있습니다. 이렇듯 Activation Function의 구간에서 **기울기(gradient)가 0에 가까워지는 현상을 Saturated**라고 합니다. 이는 `Vanishing Gradient`문제를 야기합니다.
-   `tanh`
    -   출력 값을 -1에서 1로 압축시켜줍니다.
    -   단점: 여전히 `Saturation` 문제가 있음.
-   `ReLU`
    -   양의 값에서는 Saturated 되지 않습니다.
    -   단점: 음수 영역에서 saturated 되는 문제가 다시 발생합니다.
-   `LeakyReLU`
    -   ReLU와 유사하지만 negative regime(음의 영역)에서 더 이상 0이 아닙니다.
    -   saturated 되지 않습니다