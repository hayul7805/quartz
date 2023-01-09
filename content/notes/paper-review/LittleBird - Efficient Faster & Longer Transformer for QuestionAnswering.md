---
title: "LittleBird - Efficient Faster & Longer Transformer for QuestionAnswering"
date : "2022-12-23"
tags:
- Kakao 
---

> [!warning] 선행 개념
> - sliding window attention from BigBird (Zaheer et al., 2020)
> - linear bias to attention from ALiBi (Press et al., 2021) 
> - pack and unpack attention from LUNA (Ma et al., 2021)

> BERT has shown a lot of sucess in a wide variety of NLP tasks. But it has a limitation dealing with long inputs due to its attention mechanism.
- BERT 모델의 단점: long inputs에서 한계가 있다.
- 이를 보완하기 위해 `BigBird` 등이 제안되었으나, 충분치 않았고 그래서 이 연구 'LittleBird'를 제안한다. 

> (...)LittleBird, a novel model based on BigBird with improved speed and memory footprint while maintaining accuracy.

- **특징 1:** method for position representation
	- 기존의 `positional encoding` 방식은 long input에서 한계가 있었다.
	- 그래서, *we devise a new method based on the Attention with Linear Biases (`ALiBi`) that is  fast, flexible, and also effective in QA tasks.*
- **특징 2:** method of capturing global information
	- We show that replacing them with modified `pack and unpack attention` (Ma et al., 2021) is more effective.
- **특징 3:** efficient way to train a model for long sequences
	- `Padding Insertion`, which makes the model robust to long inputs while training on short inputs.
	- `distillation method`
- **이 모델의 기여점:** This is a significant benefit for low-resource languages where large amounts of long text data are difficult to obtain.

### Pretraining objectives for Question  Answering

However, **Masked LM (MLM) is suboptimal for extractive QA task.** Joshi et al. (2020) proposed `SpanBERT`, which is pretrained by a span-level masking scheme whose lengths follows geometric distribution and **it outperformed BERT with MLM** in the most of tasks, especially extractive QA. They proved that training objective predicting spans rather than tokens generates better representations especially for span selection tasks.

## LittleBird Architecture

### Bidirectional ALiBi
- (...) because **ALiBi was designed for causal language modeling, not autoencoding language modeling**, each query can attend to keys to the left of itself only, not keys further away or to the right in ALiBi.
- Therefore, we devised `BiALiBi` (Bidirectional ALiBi), which is improved version of ALiBi to **suit the autoencoding language model**. BiALiBi has the same attention function as ALiBi, but differs only in the method of calculating the distance matrix.

### Sliding window attention & Pack unpack attention
- (...) we completely eliminated random attention from our model.
- We also reduced the number of global tokens and removed global-local attention, they were replaced with pack and unpack attention.
- To effectively replace random and global attention, we employed pack and unpack attention (Ma et al., 2021).

## Conclusion and Limitations
- We propose `LittleBird`, which is more efficient in terms of memory and computational time than existing Transformer models for long sequences, and its effective way to train. 
	- It combines a novel position encoding method, BiALiBi, and pack & unpack with sliding window attention to achieve high speed and accuracy, particularly in question answering tasks for long documents. 
	- The distillation and training method with Padding Insertion allows  the model to be trained by reusing the existing pre-trained language model for short inputs and work well for long inputs even if trained on short inputs.

- (...) causal masking cannot be applied to the pack and unpack attention due to its characteristics, which means that **LittleBird cannot be used to the decoder-only autoregressive language model.**

> [!note] 참고  
>   
> Causal masking is a technique used to ensure that the decoder can only rely on the tokens earlier in the sequence when making its prediction. However, LittleBird uses a method called 'pack and unpack attention', which prevents causal masking from being used, meaning that LittleBird cannot be used to make predictions one token at a time (known as an autoregressive language model).
> An example of a decoder-only autoregressive model is a **machine translation system**, where the input text is encoded into an intermediate representation and then decoded one token at a time to generate the output.