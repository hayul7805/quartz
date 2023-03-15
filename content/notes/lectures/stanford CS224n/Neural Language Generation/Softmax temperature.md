---
title: "Softmax temperature"
date : "2023-03-15"
---
Scaling **randomness**: Softmax temperature
	  - You can apply **a temperature hyperparameter $\tau$** to the softmax to rebalance $P_t$!
	    $$P_t(y_t = w) = {{exp({\color{blue}S_w / \tau})} \over {\sum_{w'\in V} exp({\color{blue}S_{w'/ \tau}})}}$$
	- Raise the temperature $\tau$  > 1: $P_t$ becomes **more uniform**
		- **More diverse output** (probability is spread around vocab)
	- Lower the temperature $\tau$  < 1: $P_t$ becomes **more spiky** 
		- **Less diverse output** (probability is concentrated on top words 

> [!note] Note  
>   
> Softmax temperature is *not* a decoding algorithm! It’s a technique you can apply at test time, in conjunction with a decoding algorithm (such as beam search or sampling)