---
title: 🧭 Linear system
date : "2023-01-09"
tags :
- In-progress
---

## 선형시스템

$$a_{1}x_{1} + a_{2}x_{2}+a_{3}x_{3} + ... + a_{n}x_{n} = b$$

$$a^Tx = b$$
$$where \, a =
\begin{bmatrix}
a_{1}\\
a_{2}\\
...\\
a_{n}\\
\end{bmatrix}
and \, x =
\begin{bmatrix}
x{1}\\
x{2}\\
...\\
x_{n}\\
\end{bmatrix}$$

## 역행렬

만약 행렬 $A$가 역행렬이 가능하다면(invertible), 가능한 해는 오직 하나이며 그것은 $x = A^{-1}b$ 이다. 
역행렬이 가능한지는 두 가지 방식으로 알 수 있다. 행렬 $A$가

$$A =
\begin{bmatrix}
a&b\\
c&d\\
\end{bmatrix}$$
일때, 

1. $ad - bc =0$ 이거나(= denominator가 0이면),
2. $a:b = c:d$  이면 역행렬이 존재하지 않는다. 

단, 이것은 2차원일 때의 이야기다. 
만약 행렬 $A$가 역행렬이 존재하지 않는다면, 

1. 해가 없거나
2. 가능한 해가 무수히 많다는 이야기다.


> [!note] 만약 정사각 행렬이 아니라면?
> 
> $m = equations, \, n = variables$ 이라고 할 때,
> - m < n: 가능한 해가 무수히 많다.
> - n < m: 해가 존재하지 않는다.