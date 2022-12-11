---
title: "Hate speech detection is not as easy as you may think"
---

>[!info] Reference  
>
>Aymé Arango, Jorge Pérez, and Barbara Poblete. 2019. Hate Speech Detection is Not as Easy as You May Think: A Closer Look at Model Validation. In Proceedings of the 42nd International ACM SIGIR Conference on Research and Development in Information Retrieval (SIGIR'19). Association for Computing Machinery, New York, NY, USA, 45–54. https://doi.org/10.1145/3331184.3331262

---

## Introduction

> Despite the apparent difficulty of the hate speech detection problem evidenced by social-media providers, current state-of- the-art approaches reported in the literature show near-perfect performance. Within-dataset experiments on labeled hate speech datasets using supervised learning achieve F1 scores above 93% [3, 7–9]. Nevertheless, there are only a few studies towards determining how generalizable the resulting models are, beyond the data collection upon which they were built on, nor on the factors that may affect this property [10]. Furthermore, recent literature that surveys current work also views the state-of-the-art under a more conservative and cautious light [3,10].
- 소셜 미디어 제공자가 증명하는 혐오 발언 탐지 문제의 명백한 어려움에도 불구하고, 문헌에 보고된 현재 최첨단 접근 방식은 거의 완벽한 성능을 보여준다. 지도 학습을 사용하여 레이블링된 혐오 발언 데이터 세트에 대한 데이터 세트 내 실험은 93% 이상의 F1 점수를 달성한다. 
- **그럼에도 불구하고 결과 모델이 구축된 데이터 수집을 넘어, 결과 모델의 일반화 정도를 결정하는 데에는 몇 가지 연구만이 있다.** 또한, 현재 작업을 조사하는 최근 문헌에서도 최첨단 기술을 보다 보수적이고 신중한 관점에서 바라본다.

> [!note] Aim of this paper  
>   
> "(...) measure how these models would perform on similar yet different datasets."

- 비슷하지만 다른 데이터셋. 거기에서 모델의 성능을 보는 것. 이게 핵심이다.

## Related work

> **There is some recent work on testing the generalization of the state-of-the-art methods to other datasets and domains [8–10].** Most of this work has been focused on Deep Learning methods. 
> Agrawal and Awekar [8] test the performance of models trained on tweets [11] classifying on Wikpedia data [33] and Formspring data [34]. The authors show that transfer learning from Twitter to the two other domains performs poorly achieving less than 10% F1. 
> In a similar study, Dadvar and Eckert [9] perform transfer learning from Twitter to a dataset of Youtube comments [35] showing a performance of 15% F1. 
> Gröndahl et al. [10] present a comprehensive study reproducing several state-of-the-art models. 
> Specially important for us is the experiment transferring Badjatiya et al.’s model [7] trained on the Waseem and Hovy’s dataset [11] to two other similarly labeled tweet datasets [16,17]. Even in this case the performance drops significantly, obtaining 33% and 47% F1 in those sets. This is a 40+% drop from the 93% F1 reported by Badjatiya et al. [7]. 
> From these results, **Gröndahl et al. [10] draw as a conclusion that model architecture is less important than the type of data and labeling criteria being used.** 
> In this paper our results are coherent with those of Gröndahl et al. [10]. However, we take our research a step further by investigating why this issue occurs.
- 훌륭한 개괄이다. 이렇게 써야 하는데. 