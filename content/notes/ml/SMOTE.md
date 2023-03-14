---
title: "SMOTE"
date : "2023-03-12"
---

`SMOTE`: Synthetic Minority Over-sampling Technique은 불균형한 데이터셋에서 분류기의 성능을 향상시키기 위한 방법입니다. 불균형한 데이터셋이란 한 클래스가 다른 클래스보다 훨씬 많은 비율로 존재하는 경우를 말합니다. **SMOTE는 소수 클래스의 예제를 인공적으로 생성하여 소수 클래스를 오버샘플링하는 방식으로 작동합니다.** 인공적인 예제는 소수 클래스의 가까운 이웃들을 기반으로 생성됩니다. SMOTE는 C4.5, Ripper, Naive Bayes와 같은 분류기에 적용할 수 있으며, ROC 곡선 아래 면적(AUC)을 사용하여 평가됩니다.

SMOTE의 동작 원리는 다음과 같습니다. **소수 클래스의 예제를 선택하고 그 예제와 가장 가까운 k개의 이웃을 찾습니다. 그 다음에 이웃들과의 차이 벡터에 임의의 수를 곱하여 새로운 예제를 생성합니다.** 이 과정을 반복하여 원하는 만큼 소수 클래스의 예제를 늘립니다. 이렇게 하면 소수 클래스가 과대표현되지 않고 다양한 패턴을 학습할 수 있습니다.

**장점**:

-   무작위 오버샘플링에서 발생할 수 있는 모델 오버피팅을 완화합니다. 인공적인 예제를 생성하기 때문에 인스턴스의 복제가 아닙니다
-   정보의 손실이 없습니다
-   구현하고 해석하기 쉽습니다

**단점**:

-   인공적인 예제를 생성할 때 SMOTE는 이웃 클래스나 잡음에 대해 고려하지 않습니다. [따라서 소수 클래스와 다수 클래스 사이의 경계에 가까운 예제들을 생성할 수 있습니다](https://www.datacamp.com/tutorial/diving-deep-imbalanced-data)[2](https://www.datacamp.com/tutorial/diving-deep-imbalanced-data).
-   [고차원 데이터셋에서는 효과가 떨어질 수 있습니다](https://www.dominodatalab.com/blog/smote-oversampling-technique)[3](https://www.dominodatalab.com/blog/smote-oversampling-technique).