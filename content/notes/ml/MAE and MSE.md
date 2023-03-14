---
title: "MAE and MSE"
date : "2023-03-12"
---
MAE와 MSE는 회귀 모델의 성능을 평가하기 위한 두 가지 **손실 함수**입니다[1](https://www.kaggle.com/getting-started/52081). MAE는 Mean Absolute Error의 약자로, 예측값과 실제값의 절대값 차이의 평균입니다. MSE는 Mean Squared Error의 약자로, 예측값과 실제값의 제곱 차이의 평균입니다.

MAE와 MSE는 다음과 같은 차이점이 있습니다[1](https://www.kaggle.com/getting-started/52081)[2](https://stats.stackexchange.com/questions/582238/mae-vs-mse-for-linear-regression)[3](https://m.blog.naver.com/PostView.naver?blogId=heygun&logNo=221516529668)[4](https://stephenallwright.com/mse-vs-mae/):

-   **MAE는 오차에 대해 선형적으로 반응하고, MSE는 오차에 대해 비선형적으로 반응합니다.** 즉, MSE는 큰 오차에 더 큰 패널티를 부여하고 작은 오차에 더 작은 패널티를 부여합니다. 반면에 MAE는 모든 오차에 동일한 가중치를 부여합니다.

>[!info] key difference  
>   
>The key difference between squared error and absolute error is that squared error punishes large errors to a greater extent than absolute error, **as the errors are squared instead of just calculating the difference.**

- **MAE는 이상치(outlier)에 대해 더 강인하고(MSE보다 영향을 덜 받고), MSE는 이상치에 대해 더 민감합니다(MAE보다 영향을 많이 받습니다).** 이상치가 많은 데이터셋에서는 MAE가 MSE보다 더 신뢰할 수 있는 지표일 수 있습니다.
-   **MAE를 최소화하는 값은 중앙값(median)이고, MSE를 최소화하는 값은 평균(mean)입니다.** 중앙값은 평균보다 이상치에 영향을 덜 받기 때문에 MAE가 MSE보다 이상치에 강인하다고 할 수 있습니다.
-   MSE는 기울기 하강법(gradient descent)과 같은 최적화 알고리즘에서 쉽게 계산할 수 있는 편미분(derivative)을 가지고 있습니다. 반면에 MAE는 편미분이 0인 지점에서 연속성이 깨지기 때문에 최적화하기 어렵습니다.

어떤 손실 함수를 사용할지 결정하는 것은 문제의 특성과 목적에 따라 달라집니다. **일반적으로 큰 오차를 허용하지 않거나 정확한 예측 값을 원한다면 MSE를 사용하고, 작은 오차를 허용하거나 이상치가 많은 데이터셋을 다룬다면 MAE를 사용하는 것이 좋습니다**[3](https://m.blog.naver.com/PostView.naver?blogId=heygun&logNo=221516529668).