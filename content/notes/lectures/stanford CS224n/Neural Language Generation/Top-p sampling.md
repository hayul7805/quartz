---
title: "Top-p sampling"
date : "2023-03-15"
tags :
- decoding 
---

- 등장 배경: **The probability distributions we sample from are dynamic.** (참고: [Top-k sampling](notes/lectures/stanford%20CS224n/Neural%20Language%20Generation/Top-k%20sampling.md))
	- When the distribution $P_t$ is **flatter**, a limited $k$ removes many viable options.
	- When the distribution $P_t$ is **peakier**, a high $k$ allows for too many options to have a chance of being selecte.
- 이 문제를 해결할 방법: **Top-p sampling**
	- Sample from all tokens in **the top $p$ cumulative probability mass** (i.e., where mass is concentrated).
	- Varies k depending on the uniformity of $P_t$.
	  ![](스크린샷%202023-03-15%20오후%203.39.10.png)