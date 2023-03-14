---
title: "Neural Language Generation"
date : "2023-03-14"
---

> **What is natural language generation?**  
> Any task involving text production for human consumption requires natural language generation

### Formalizing NLG: a simple model and training algorithm

- Basics of natural language generation
	- In autoregressive text generation models, at each time step $t$, our model takes in a sequence of tokens of text as input $\{y\}_{<t}$ and outputs a new token, ${\hat{y}}_t$.
	- ![](notes/lectures/stanford%20CS224n/image/cs224n_1.png)
	- At each time step t, our model computes a vector of scores for each token in our vocabulary, $S \in \mathbb{R}^V$:
	  $$S = f(\{y_{<t}\}, \theta)$$
	- Then, we compute a probability distribution $𝑃$ over $w \in V$ using these scores:
	  $$P(y_t = w | \{y_{<t}\}) = {{exp(S_w)} \over {\sum_{w'\in V} exp(S_{w'})}}$$
- **Basics: What are we trying to do?**
	- At each time step $t$, our model computes a vector of scores for each token in our vocabulary, $S \in \mathbb{R}^V$). Then, we compute a probability distribution $P$  over $w \in V$ using these scores:
	  
	  ![](notes/lectures/stanford%20CS224n/image/스크린샷%202023-03-14%20오후%205.14.39.png)
	- At inference time, our decoding algorithm defines a function to select a token from this distribution:
	  $${\hat{y_t}} = g(P(y_t|\{y_{<t}\})$$
	  - In the equation above, $\color{red}g(\cdot)$ is your decoding algorithm.
	  - We train the model to minimize **the negative loglikelihood** of predicting the next token in the sequence:
	    $$L_t = -logP(y_t^* | \{y_{<t}^*\})$$
	- The label at each step is the actual word $\color{blue}y_t^*$ in the training sequence.
	- This token is often called the “gold” or “ground truth” token.
	- This algorithm is often called **“teacher forcing”**.

- **Maximum Likelihood Training** (i.e., **teacher forcing**)