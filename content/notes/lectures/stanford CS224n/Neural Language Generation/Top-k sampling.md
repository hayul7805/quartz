---
title: "Top-k sampling"
date : "2023-03-15"
tags:
- decoding
---

- **Problem**: Vanilla sampling makes every token in the vocabulary an option
	- Even if most of the probability mass in the distribution is over a limited set of options, **the tail of the distribution could be very long**
	- Many tokens are probably irrelevant in the current context
	- Why are we giving them *individually* a tiny chance to be selected?
	- Why are we giving them *as a group* a high chance to be selected?
- **Solution**: Top-k sampling
	- **Only sample from the top *k* tokens in the probability distribution**.
	- Increase *k* for more **diverse/risky** outputs
	- Decrease *k* for more **generic/safe** outputs
	  ![](스크린샷%202023-03-15%20오후%203.32.22.png)
	- Top-k sampling can cut off *too quickly*!
		- 각 토큰이 비슷한 확률 분포를 가지면 빠르게 cut-off 한다. 
	- Top-k sampling can also cut off *too slowly*!
		- 그러나, 소수의 토큰이 높은 확률을 갖고 나머지가 아주 낮은 확률을 갖는다면, 상당히 느리게 cut-off 할 것이다. 