---
title: "Unlikelihood training"
date : "2023-03-15"
tags : 
- NLG
---
- Given a set of undesired tokens $C$, **lower their likelihood in context.**
  $$L_{UL}^t = -\sum_{y_{neg} \in C} log(1-P(y_{neg} | {y^*}_{<t}))$$
- Keep teacher forcing objective and **combine them** for final loss function.
  $$L_{MLE}^t = -\sum_{t=1} logP(y_t^* | {y^*}_{<t})$$
  $$L_{ULE}^t = L_{MLE}^t + aL_{UL}^t$$
- Set $C = {y^*}_{<t}$ and you’ll train the model **to lower the likelihood of previously-seen tokens!**
	- Limits repetition!
	- Increases the diversity of the text you learn to generate.