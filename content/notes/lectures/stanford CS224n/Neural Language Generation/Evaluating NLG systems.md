---
title: "Evaluating NLG systems"
date : "2023-03-15"
tags:
- NLG
---
- Types of evaluation methods for text generation
	- Content overlap metrics
	- Model-based Metrics
	- Human Evaluations
- ==Content overlap metrics==
	- Compute a score that indicates the similarity between *generated* and *gold-standard* (human-written) text
	- Fast and efficient and widely used
	- Two broad categories:
		- **N-gram overlap metrics** (e.g., BLEU, ROUGE, METEOR, CIDEr, etc.)
			- *They’re not ideal for machine translation.*
		- **Semantic overlap metrics** (e.g., PYRAMID, SPICE, SPIDEr, etc.
- ==Model-based metrics==
	- Use **learned representations of words and sentences** to compute semantic similarity between generated and reference texts.
	- **No more n-gram bottleneck** because text units are represented as embeddings!
	- Even though embeddings are **pretrained**, distance metrics used to measure the similarity can be **fixed**.
	- Model-based metrics: **Word distance functions**
		- **Vector Similarity**
			- Embedding Average (Liu et al., 2016)
			- Vector Extrema (Liu et al., 2016)
			- MEANT (Lo, 2017)
			- YISI (Lo, 2019)
		- **Word Mover’s Distance**
		- **BERT SCORE**
			- Uses pre-trained contextual embeddings from BERT and matches words in candidate and reference sentences by cosine similarity. (Zhang et.al. 2020)
	- Model-based metrics: **Beyond word matching**
		- **Sentence Movers Similarity**
		- **BLEURT**
			- A regression model based on BERT returns a score that indicates to what extend the candidate text is grammatical and conveys the meaning of the reference text. (Sellam et.al. 2020)
- Human evaluations
	- Most important form of evaluation for text generation systems
	- *Ask* humans to evaluate the quality of generated text
> [!warning] Note  
> 
> Don’t compare human evaluation scores across differently-conducted studies. Even if they claim to evaluate the same dimensions!

- Learning from human feedback
	- ADEM
	- HUSE

> [!note] Evaluation: Takeaways  
>   
>  - **Content overlap metrics** provide a good starting point for evaluating the quality of generated text, but they’re **not good enough on their own.**
>  - **Model-based metrics** are can be more correlated with human judgment, but behavior is **not interpretable.**
>  - **Human judgments** are critical.
> 	 - Only ones that can directly evaluate **factuality** – is the model saying correct things?
> 	 - But humans are **inconsistent**!
>  - In many cases, the best judge of output quality is YOU!

- **학습이 필요 없는 자동 척도**: 생성된 텍스트와 참조 텍스트 간의 유사도를 측정하는 수학적인 공식을 사용하는 방법입니다. 이 방법은 계산하기 쉽고 저렴하지만 언어적 다양성에 대응하기 어렵고 인간의 판단과 일치하지 않을 수 있습니다. 예를 들면 BLEU, ROUGE, METEOR 등이 있습니다.
- **기계 학습된 척도**: 생성된 텍스트의 품질이나 유용성을 예측하기 위해 데이터로부터 학습한 모델을 사용하는 방법입니다. 이 방법은 인간의 판단과 더 잘 일치하고 언어적 다양성에 더 유연하게 대처할 수 있지만 학습에 필요한 데이터와 컴퓨팅 자원이 많이 필요합니다. 예를 들면 BERTScore, BLEURT 등이 있습니다.
- **인간 중심의 평가 척도**: 인간 평가자들이 생성된 텍스트의 품질이나 유용성을 직접 점수화하거나 비교하는 방법입니다. 이 방법은 언어적 다양성에 민감하고 신뢰할 수 있지만 비용이 많이 들고 시간이 오래 걸립니다.