---
title: "Teacher forcing"
date : "2023-03-15"
---
- Maximum Likelihood Training (i.e., **teacher forcing**)
- Trained to generate the next word $\color{blue}y_t^*$ given a set of preceding words $\color{red}\{y_{<t}^*\}$.
- 모델의 출력값이 다음 타임 스텝에 입력값으로 들어가는 방식.
	  $$L = -\sum_{t=1}^4 logP({\color{blue}y_t^*} | {\color{red}\{y_{<t}^*\}})$$![](스크린샷%202023-03-15%20오전%2012.26.09.png)