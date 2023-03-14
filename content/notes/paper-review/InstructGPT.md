---
title: "InstructGPT"
date : "2023-02-27"
---
The [OpenAI API is powered by GPT-3 language models](https://openai.com/blog/gpt-3-apps/) which can be coaxed to perform natural language tasks using carefully engineered text prompts. **But these models can also generate outputs that are untruthful, toxic, or reflect harmful sentiments.** This is in part because GPT-3 is trained to predict the next word on a large dataset of Internet text, rather than to safely perform the language task that the user wants. In other words, these models aren’t _aligned_ with their users.

...

To train InstructGPT models, our core technique is [reinforcement learning from human feedback (RLHF)](https://openai.com/blog/deep-reinforcement-learning-from-human-preferences/), a method we helped pioneer in our earlier alignment research. **This technique uses human preferences as a reward signal to fine-tune our models**, which is important as the safety and alignment problems we are aiming to solve are complex and subjective, and aren’t fully captured by simple automatic metrics.

출처: https://openai.com/blog/instruction-following/#birds-migrate

---

