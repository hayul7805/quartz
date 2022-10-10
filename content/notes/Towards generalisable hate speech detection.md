---
title: "Towards generalisable hate speech detection"
tags :
- generalization
- key-observation 
---
> [!info] Reference
> Yin, W., & Zubiaga, A. (2021). Towards generalisable hate speech detection: a review on obstacles and solutions. _PeerJ Computer Science_, _7_, e598.

## Data

> [예시 1]
> For example, in Wiegand, Ruppenhofer & Kleinbauer (2019)’s study, FastText models (Joulin et al., 2017a) trained on three datasets (Kaggle, Founta, Razavi) achieved F1 scores above 70 when tested on one another, **while models trained or tested on datasets outside this group achieved around 60 or less**.
- 다른 데이터셋에서는 모델의 성능이 떨어진다는 결과가 있다.

#key-observation 
> Founta and OLID produced models that performed well on each other. The source of such differences are usually traced back to search terms (Swamy, Jamatia & Gambäck, 2019), topics covered (Nejadgholi & Kiritchenko, 2020; Pamungkas, Basile & Patti, 2020), label definitions (Pamungkas & Patti, 2019; Pamungkas, Basile & Patti, 2020; Fortuna, Soler-Company & Wanner, 2021), and data source platforms (Glavaš, Karan & Vulić, 2020; Karan & Šnajder, 2018).
- 서로 테스트 성능이 잘 나오는 데이터셋은 그 근원을 따라가보면 알 수 있는 사실이 있다. 예를 들면, Founta와 OLID 데이터셋은 서로 비슷한 데이터를 공유하고 있다. 

> Another way of looking at generalisation and similarity is by comparing differences between individual classes across datasets (Nejadgholi & Kiritchenko, 2020; Fortuna, Soler & Wanner, 2020; Fortuna, Soler-Company & Wanner, 2021), as opposed to comparing datasets as a whole.
- 이 논문에서도 class 개별로 비교하라고 주장하는구나. [On Cross-Dataset Generalization in Automatic Detection of Online Abuse](notes/On%20Cross-Dataset%20Generalization%20in%20Automatic%20Detection%20of%20Online%20Abuse.md) 에서 주장하는 것과 맞물린다. 

