---
title: "Machine Learning"
tags : 
- ML 
---

## ML 대표 알고리즘

-   Logistic Regression
-   Decision Tree
-   Naïve Bayes
-   Support Vector Machine
-   K Nearest Neighbors
-   Decision Tree 기반 Ensemble 모형
	- Random Forest
	- Extra Trees Boosting
- Decision Tree 기반 Gradient Boosting 모형
	- Extreme Gradient Boosting  
	- Light Gradient Boosting  
	- Categorical Gradient Boosting
- Natural Gradient Boosting

> [!note]
> 일반적으로 **Decision Tree & Logistic Regression** 이 설명력이 좋아서 자주 쓰인다. 그러나 최근에는 **Gradient Boosting** 계열도 자주 쓰이고 있다.

## ML system 종류의 대표 구분 3가지

**1. 사람의 감독하에 프로그램이 훈련하는 것인지 여부** 
- [지도학습 ( Supervised Learning )](notes/지도학습%20(%20Supervised%20Learning%20).md)
	- 분류 (Classification)
	- 회귀 (Regression)
- [비지도학습 ( Un-supervised Learning )](notes/비지도학습%20(%20Un-supervised%20Learning%20).md)
- 준지도학습 ( Semi-supervised Learning )
- 강화학습 ( Reinforcement Learning )

**2. 실시간으로 점진적인 학습을 하는지 여부**
- 온라인 학습 ( Online Learning )  
- 배치 학습 ( Batch Learning )

**3. 기존의 데이터와 새로운 데이터를 간단히 비교분석하는 것인지 혹은 훈련 데이터 셋으로부터 패턴을 발견하여 예측 모델을 만드는지 여부** 
- 사례 기반 학습 ( Instance-based Learning )
- 모델 기반 학습 ( Model-based Learning )

## ML 문제 해결 순서

1. 학습 데이터와 테스트 데이터의 분포가 동일한지 여부를 파악한다
2. 활용할 모델 알고리즘들을 정한다
3. Hyperparameter Tuning Case를 정의한다
4. `Cross Validation`기반 학습을 진행한다 ( 모든 학습 데이터를 학습과 검증에 다 활용 )
5. 유의미한 결과가 나오는 알고리즘 및 Hyperparameter Case를 기반으로 학습 데이터 전체를 학습한다
6. 테스트 결과를 확인한다

## [Model tuning](notes/Model%20tuning.md)