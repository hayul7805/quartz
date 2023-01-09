---
title: "Language Models are Few-Shot Learners"
date : "2022-12-23"
---

> [!note] Goal  
>   
> 이 논문에서 저자들은 GPT-3 언어 모델을 사용하여 가설을 테스트하고 있다. GPT-3는 1,750억 개의 매개 변수를 가지고 있으며 문맥 정보를 사용하여 학습할 수 있다. 저자들은 이 모델을 사용하여 작업에 빠르게 적응할 수 있는 능력과 few shot 시나리오에서 학습에 대한 숙련도를 평가하고 있다.

> PLM을 이용한 Fine-tuning이 만능인가?

The approach of pre-trained language models has had significant success and has allowed for more efficient tasks, **but it requires having a task-specific dataset for fine-tuning.** This means that to get strong performance on any specific task, a dataset of a large number of examples related to that task is needed.

> 아니다, fine-tuning을 위한 데이터셋이 필요하다. 이러한 한계를 없애야하는 이유는 여러가지가 있다.

- First, from a practical perspective, the need for a large dataset of labeled examples for every new task limits the applicability of language models.
- 그리고 무엇보다, 사람은 그렇게 학습하지 않아. 사람에게 무언가를 요구할 때는 간단한 문장이면 충분하다. 

> 그러면, 다른 방향이 있는가?

- One potential route towards addressing these issues is **meta-learning**– which in the context of language models means the model develops a broad set of skills and pattern recognition abilities at training time, and then uses those abilities at inference time to rapidly adapt to or recognize the desired task (illustrated in Figure 1.1).
- **Meta-learning** is a technique used to train a model in such a way that it can develop a set of skills and be able to recognize patterns quickly, which helps it in adapting to a specific task when it is being used. Basically, it prepares the model to become more efficient at a task by 'learning' from a variety of training experiences first.
- = **In-context learning**.
	- In-context learning is a method of teaching a language model to complete a task from contextual information provided by natural language instructions and/or a few demonstrations of the task. It is possible that this method of learning will become more successful as larger language models are developed; that is, models with more parameters, or units processing the data. This means that with larger language models, the in-context learning abilities would improve in performance.

## Term definition

- **Fine-Tuning (FT)** has been the most common approach in recent years, and involves updating the weights of a pre-trained model by training on a supervised dataset specific to the desired task. Typically thousands to hundreds of thousands of labeled examples are used. 
	- The main advantage of fine-tuning is strong performance on many benchmarks. 
	- The main disadvantages are the need for a new large dataset for every task, the potential for poor generalization out-of-distribution [MPL19 ], and the potential to exploit spurious features of the training data [GSL+18 , NK19 ], potentially resulting in an unfair comparison with human performance. 
- **Few-Shot (FS)** is the term we will use in this work to refer to the setting where **the model is given a few demonstrations of the task at inference time** as conditioning [RWC+19 ], but **no weight updates** are allowed.
	- Basically, the model receives these examples, uses them to make a prediction, and then **doesn't get to adjust its internal parameters** to learn from its mistakes.
- **One-Shot (1S)** is the same as few-shot except that only one demonstration is allowed, in addition to a natural language description of the task, as shown in Figure 1. The reason to distinguish one-shot from few-shot and zero-shot (below) is that **it most closely matches the way in which some tasks are communicated to humans.**
- **Zero-Shot (0S)** is the same as one-shot except that no demonstrations are allowed, and the model is only given a natural language instruction describing the task.

> [!note] Tip  
>   
> When building a machine learning model, the batch size and learning rate are important factors that must be considered. Generally, for larger models, you can use a larger batch size - which means that more data is fed in at once during training - but a smaller learning rate, which dictates the pace at which the model learns.

## GPT in reading comprehension
On DROP [DWD+19 ], a dataset testing discrete reasoning and numeracy in the context of reading comprehension, **GPT-3 in a few-shot setting outperforms the fine-tuned BERT baseline** from the original paper but is still well below both human performance (...)

## Limitations
- First, despite the strong quantitative and qualitative improvements of GPT-3, particularly compared to its direct predecessor GPT-2, **it still has notable weaknesses in text synthesis and several NLP tasks.** On text synthesis, although the overall quality is high, GPT-3 samples still sometimes repeat themselves semantically at the document level, start to lose coherence over sufficiently long passages, contradict themselves, and occasionally contain non-sequitur sentences or paragraphs.
- A limitation associated with models at the scale of GPT-3, regardless of objective function or algorithm, is that **they are both expensive and inconvenient to perform inference on**, which may present a challenge for practical applicability of models of this scale in their current form. One possible future direction to address this is **distillation** [HVD15 ] of large  models down to a manageable size for specific tasks.
- Finally, GPT-3 shares some limitations common to most deep learning systems – **its decisions are not easily interpretable**, it is not necessarily well-calibrated in its predictions on novel inputs as observed by the much higher variance in performance than humans on standard benchmarks, and it retains the biases of the data it has been trained on.