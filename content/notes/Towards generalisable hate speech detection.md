---
title: "Towards generalisable hate speech detection"
tags :
- generalization
- key-observation 
---

> [!info] Reference  
> 
> Yin, W., & Zubiaga, A. (2021). Towards generalisable hate speech detection: a review on obstacles and solutions. _PeerJ Computer Science_, _7_, e598.

---

## Generalisation

> Most if not all proposed hate speech detection models rely on supervised machine learning methods, where the ultimate purpose is for the model to learn the real relationship between features and predictions through training data, which generalises to previously unobserved inputs (Goodfellow, Bengio & Courville, 2016). The generalisation performance of a model measures how well it fulfils this purpose.
- 제안된 혐오 발언 탐지 모델은 대부분 supervised 기계 학습 방법에 의존하며, 궁극적인 목적은 모델이 이전에 관찰되지 않은 입력으로 일반화하는 훈련 데이터를 통해 기능과 예측 사이의 실제 관계를 학습하는 것이다(Goodfellow, Bengio & Courville, 2016). 모델의 일반화 성과는 이 목적을 얼마나 잘 달성하는지 측정한다.

> The ultimate purpose of studying automatic hate speech detection is to facilitate the alleviation of the harms brought by online hate speech. To fulfil this purpose, hate speech detection models need to be able to deal with the constant growth and evolution of hate speech, regardless of its form, target, and speaker.
- 자동 혐오표현 탐지를 연구하는 궁극적인 목적은 온라인 혐오표현이 가져오는 해악의 완화를 용이하게 하는 것이다. 이러한 목적을 달성하기 위해, 혐오표현 탐지 모델은 형태, 대상 및 화자에 관계없이 혐오 발언의 지속적인 성장과 진화를 처리할 수 있어야 한다.

#key-observation 
>Recent research has raised concerns on the generalisability of existing models (Swamy, Jamatia & Gambäck, 2019). Despite their impressive performance on their respective test sets, **the performance significantly dropped when the models are applied to a different hate speech dataset.** This means that the assumption that test data of existing datasets represent the distribution of future cases is not true, and that **the generalisation performance of existing models have been severely overestimated** (Arango, Prez & Poblete, 2020). This lack of generalisability undermines the practical value of these hate speech detection models.
- 최근 연구는 기존 모델의 일반화 가능성에 대한 우려를 제기했다(Swamy, Jamatia & Gambeck, 2019 : [Studying Generalisability Across Abusive Language Detection Datasets](notes/Studying%20Generalisability%20Across%20Abusive%20Language%20Detection%20Datasets.md)).  **각각의 테스트 세트에서 인상적인 성능에도 불구하고 모델이 다른 혐오 음성 데이터 세트에 적용될 때 성능이 크게 떨어졌다.** 이는 기존 데이터 세트의 테스트 데이터가 미래의 사례 분포를 나타낸다는 가정이 사실이 아니며, **기존 모델의 일반화 성능이 심각하게 과대 평가되었다는 것을 의미한다**(Arango, Pres & Poblete, 2020 : [Hate speech detection is not as easy as you may think](notes/Hate%20speech%20detection%20is%20not%20as%20easy%20as%20you%20may%20think.md)). 이러한 일반성의 부족은 이러한 혐오표현 탐지 모델의 실질적인 가치를 훼손한다.

>[!note] Note  
>
>이 부분이 내가 하고 있는 연구의 핵심이다! 모델의 일반화 성능이 과대평가되어 있다는 것. 한국어 데이터셋과 모델로도 비슷한 결과가 나오는지 보는 것.

## Data

> [예시 1]
> For example, in Wiegand, Ruppenhofer & Kleinbauer (2019)’s study, FastText models (Joulin et al., 2017a) trained on three datasets (Kaggle, Founta, Razavi) achieved F1 scores above 70 when tested on one another, **while models trained or tested on datasets outside this group achieved around 60 or less**.
- 모델이 훈련된 것과 다른 데이터셋에서는 모델의 성능이 떨어진다는 결과가 있다.

#key-observation 
> Founta and OLID produced models that performed well on each other. The source of such differences are usually traced back to search terms (Swamy, Jamatia & Gambäck, 2019), topics covered (Nejadgholi & Kiritchenko, 2020; Pamungkas, Basile & Patti, 2020), label definitions (Pamungkas & Patti, 2019; Pamungkas, Basile & Patti, 2020; Fortuna, Soler-Company & Wanner, 2021), and data source platforms (Glavaš, Karan & Vulić, 2020; Karan & Šnajder, 2018).
- 서로 테스트 성능이 잘 나오는 데이터셋은 그 근원을 따라가보면 알 수 있는 사실이 있다. 예를 들면,` Founta`와 `OLID` 데이터셋은 서로 비슷한 데이터를 공유하고 있다. 

> Fortuna, Soler & Wanner (2020) used averaged word embeddings (Bojanowski et al., 2017; Mikolov et al., 2018) to compute the representations of classes from different datasets, and compared classes across datasets. **One of their observations is that Davidson’s ‘‘hate speech’’ is very different from Waseem’s ‘‘hate speech’’, ‘‘racism’’, ‘‘sexism’’, while being relatively close to HatEval’s ‘‘hate speech’’ and Kaggle’s ‘‘identity hate’’.** This echoes with experiments that showed poor generalisation of models from Waseem to HatEval (Arango, Prez & Poblete, 2020) and between Davidson and Waseem (Waseem, Thorne & Bingel, 2018; Gröndahl et al., 2018).
- 혐오표현 데이터셋에서 자주 나오는 단어들인 'hate speech', 'racism', 'sexism' 등도 워드 임베딩을 통해 살펴보니 데이터셋마다 그 의미가 다르다는 관찰이 나왔다. 이는 당연히 모델 성능의 일반화에도 악영향을 끼쳤고 말이다. 

> In terms of what properties of a dataset lead to more generalisable models, there are frequently mentioned factors (...)

> Biases in the samples are also frequently mentioned. **Wiegand, Ruppenhofer & Kleinbauer (2019) hold that less biased sampling approaches produce more generalisable models.** This was later reproduced by Razo & Kübler (2020) and also helps explain their results with the two datasets that have the least positive cases. Similarly, Pamungkas & Patti (2019) mentioned that a wider coverage of phenomena lead to more generalisable models. 
- `Wiegand, Ruppenhofer & Kleinbauer (2019)` 연구에서 언급한 바와 같이, 조금이라도 더 일반화가 잘 되는 모델을 만드려면 sampling을 덜 치우치게 해주어야 한다. 훈련시 `sampler`를 잘 만들어야겠다.

> Another way of looking at generalisation and similarity is by comparing differences between individual classes across datasets (Nejadgholi & Kiritchenko, 2020; Fortuna, Soler & Wanner, 2020; Fortuna, Soler-Company & Wanner, 2021), as opposed to comparing datasets as a whole.
- 이 논문에서도 class 개별로 비교하라고 주장하는구나. [On Cross-Dataset Generalization in Automatic Detection of Online Abuse](notes/On%20Cross-Dataset%20Generalization%20in%20Automatic%20Detection%20of%20Online%20Abuse.md) 에서 주장하는 것과 맞물린다. 

## OBSTACLES TO GENERALISABLE HATE SPEECH DETECTION

> Hate speech detection, which is largely focused on social media, shares similar challenges to other social media tasks and has its specific ones, **when it comes to the grammar and vocabulary used.** Such user language style introduces challenges to generalisability at the data source, mainly by making it difficult to utilise common NLP pre-training approaches.
- 혐오표현 탐지는 문법이나 어휘 관련해서 어려움이 많다는 특징이 있다. 

> On social media, syntax use is generally more casual, such as the omission of punctuation (Blodgett & O’Connor, 2017). Alternative spelling and expressions are also used in dialects (Blodgett & O’Connor, 2017), to save space, and to provide emotional emphasis (Baziotis, Pelekis & Doulkeridis, 2017). Sanguinetti et al. (2020) provided extensive guidelines for studying such phenomena syntactically.
- 그래서 혐오표현 탐지 연구를 할 때는 KcELECTRA가 그나마 괜찮겠구나. 이러한 케이스가 많은 데이터로 사전학습된 모델이니까. 실제로 성능도 가장 괜찮고.

> Qian et al. (2018) found that rare words and implicit expressions are the two main causes of false negatives; Van Aken et al. (2018) compared several models that used pre-trained word embeddings, and found that rare and unknown words were present in 30% of the false negatives of Wikipedia data and 43% of Twitter data.
- 또한 rare words, implicit expressions는 false negatives를 증가시킨다. 이는 따라서 하나의 도메인에서만 수집한 데이터셋이 가지는 한계일 수 밖에 없겠다. 이를 극복하려면 여러 도메인에서 데이터를 수집해야겠네.

>Indeed, BERT (Devlin et al., 2019) and its variants have demonstrated top performances at hate or abusive speech detection challenges recently (Liu, Li & Zou, 2019; Mishra & Mishra, 2019).
- BERT 계열 모델은 혐오표현 탐지에서도 여전히 top 퍼포먼스를 보인다. 

>It is particularly challenging to acquire labelled data for hate speech detection as knowledge or relevant training is required of the annotators. As a high-level and abstract concept, the judgement of ‘‘hate speech’’ is subjective, needing extra care when processing annotations. Hence, datasets are usually not big in size.
- 혐오표현 데이터셋은 '혐오표현'을 정의하는 것 자체가 주관적이기 때문에, 주석 처리에 추가적인 힘이 들고 따라서 큰 사이즈로 만들어지기 어렵다.

> Moreover, **different studies are based on varying definitions of ‘‘hate speech’’, as seen in different annotation guidelines** (Table 5). Despite all covering the same two main aspects (directly attack or promote hate towards), datasets vary by their wording, what they consider a target (any group, minority groups, specific minority groups), and their clarifications on edge cases.
> Davidson and HatEval both distinguished ‘‘hate speech’’ from ‘‘offensive language’’, while ‘‘uses a sexist or racist slur’’ is in Waseem’s guidelines to mark a case positive of hate, **blurring the boundary of offensive and hateful.**
> Additionally, as both HatEval and Waseem specified the types of hate (towards women and immigrants; racism and sexism), hate speech that fell outside of these specific types were not included in the positive classes, while Founta and Davidson included any type of hate speech.
- 또한, 다른 주석 지침(표 5)에서 볼 수 있듯이, 다양한 연구는 "혐오 발언"의 다양한 정의를 기반으로 한다. 모든 것이 동일한 두 가지 주요 측면을 포함함에도 불구하고 데이터 세트는 표현, 대상으로 간주하는 것(모든 그룹, 소수 그룹, 특정 소수 그룹) 및 엣지 사례에 대한 명확화에 따라 다르다. 
- Davidson과 HatEval은 모두 "hate speech"와 "offensive language"를 구분했으며, "성차별적 또는 인종차별적 비방 사용"은 Waseem의 가이드라인에 hate로 표시하여 offensive와 hate의 경계를 모호하게 한다. 
- 또한, HatEval과 Waseem이 혐오의 유형(여성과 이민자에 대한 것; 인종 차별과 성차별)을 명시함에 따라, 이러한 특정 유형에서 벗어난 혐오 발언은 긍정적인 등급에 포함되지 않았고, 반면 Fonta와 Davidson은 모든 유형의 혐오 발언을 포함시켰다.

