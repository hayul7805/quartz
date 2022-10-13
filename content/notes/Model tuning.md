---
title: "Model tuning"
tags:
- ML 
---

## 그리드 탐색
-   알고리즘 내 효과적인 하이퍼파라미터 조합을 찾을 때까지, 탐색하고자 하는 하이퍼파라미터와 그에 해당하는 시도해볼 값들을 지정하여 하이퍼파라미터 튜닝을 진행하는 것
-  사이킷런의 `GridSearchCV` 클래스를 사용하여, 미리 설정한 하이퍼파라미터 조합에 대해 교차검증을 진행하고, 이를 통해 평가를 할 수 있다
- `RandomForestRegressor`에 `GridSearchCV` 적용하기
	-   3X4개의 Hyperparameter Tuning
	-   2X3개의 Hyperparameter Tuning
	-   5회 Cross Validation 진행

```python
from sklearn.model_selection import GridSearchCV

  

param_grid = [

# try 12 (3×4) combinations of hyperparameters

{'n_estimators': [3, 10, 30], 'max_features': [2, 4, 6, 8]},

# then try 6 (2×3) combinations with bootstrap set as False

{'bootstrap': [False], 'n_estimators': [3, 10], 'max_features': [2, 3, 4]},

]

  

forest_reg = RandomForestRegressor(random_state=42)

# train across 5 folds, that's a total of (12+6)*5=90 rounds of training

grid_search = GridSearchCV(forest_reg, param_grid, cv=5,

scoring='neg_mean_squared_error',

return_train_score=True)

grid_search.fit(housing_prepared, housing_labels)

```

`RandomForestRegressor`에 `GridSearchCV `적용 후 하이퍼파라미터 별 평가 점수 확인

```python
cvres = grid_search.cv_results_

for mean_score, params in zip(cvres["mean_test_score"], cvres["params"]):

print(np.sqrt(-mean_score), params)

>>>
65005.182970763315 {'max_features': 2, 'n_estimators': 3} 55582.91015494046 {'max_features': 2, 'n_estimators': 10} 52745.33887865031 {'max_features': 2, 'n_estimators': 30} 60451.18914812725 {'max_features': 4, 'n_estimators': 3} 53062.818497303946 {'max_features': 4, 'n_estimators': 10} 50663.79774079741 {'max_features': 4, 'n_estimators': 30} 57998.07162873506 {'max_features': 6, 'n_estimators': 3} 52042.04702364244 {'max_features': 6, 'n_estimators': 10} 50028.060190761295 {'max_features': 6, 'n_estimators': 30} 58308.44501796401 {'max_features': 8, 'n_estimators': 3} 52082.74313186547 {'max_features': 8, 'n_estimators': 10} 50165.81805010987 {'max_features': 8, 'n_estimators': 30} 62709.54311517104 {'bootstrap': False, 'max_features': 2, 'n_estimators': 3} 54062.01766032325 {'bootstrap': False, 'max_features': 2, 'n_estimators': 10} 60613.541905953585 {'bootstrap': False, 'max_features': 3, 'n_estimators': 3} 53742.988651846914 {'bootstrap': False, 'max_features': 3, 'n_estimators': 10} 59387.46561811065 {'bootstrap': False, 'max_features': 4, 'n_estimators': 3} 52826.41762121993 {'bootstrap': False, 'max_features': 4, 'n_estimators': 10}
```

## 랜덤 탐색
- `GridSearchCV`를 진행할 하이퍼파라미터 조합의 수가 너무 많을 때, `RandomizedSearchCV`를 활용하면 조합 내에서 임의의 하이퍼파라미터를 대입하여 지정한 횟수만큼 평가하게 됨  
- 주요 장점 2가지
	1.  랜덤 탐색을 1,000회 반복하면, 각 하이퍼파라미터마다 각기 다른 1,000개 경우를 탐색할 수 있음
	2. 반복 횟수를 단순히 조절하는 것 만으로도 하이퍼파라미터에 투입할 컴퓨팅 자원을 제어할 수 있음

```python

from sklearn.model_selection import RandomizedSearchCV

from scipy.stats import randint

  

param_distribs = {

'n_estimators': randint(low=1, high=200),

'max_features': randint(low=1, high=8),

}

  

forest_reg = RandomForestRegressor(random_state=42)

rnd_search = RandomizedSearchCV(forest_reg, param_distributions=param_distribs,

n_iter=10, cv=5, scoring='neg_mean_squared_error', random_state=42)

rnd_search.fit(housing_prepared, housing_labels)
```

```python
cvres = rnd_search.cv_results_

for mean_score, params in zip(cvres["mean_test_score"], cvres["params"]):

print(np.sqrt(-mean_score), params)

>>>
49462.596134607906 {'max_features': 7, 'n_estimators': 180} 51676.97211565583 {'max_features': 5, 'n_estimators': 15} 50827.83871022729 {'max_features': 3, 'n_estimators': 72} 51117.698297994146 {'max_features': 5, 'n_estimators': 21} 49585.185219390754 {'max_features': 7, 'n_estimators': 122} 50836.040148806715 {'max_features': 3, 'n_estimators': 75} 50746.890270152086 {'max_features': 3, 'n_estimators': 88} 49788.190631507045 {'max_features': 5, 'n_estimators': 100} 50574.565725719985 {'max_features': 3, 'n_estimators': 150} 65153.787556165735 {'max_features': 5, 'n_estimators': 2}
```

위와 같이 랜덤 탐색을 이용하는 게 더 나은 결과가 나올 수 있다. 

## 테스트 데이터 세트로 시스템 평가하기

테스트 데이터세트에서 설명변수와 타겟변수를 얻은 후, 기존의 변환 파이프라인을 통해 transform을 진행 **( 테스트의 경우 fit_transform와 같은 학습 과정이 포함된 변환은 진행하지 않음 )**

```python
final_model = grid_search.best_estimator_

  

X_test = strat_test_set.drop("median_house_value", axis=1)

y_test = strat_test_set["median_house_value"].copy()

  

X_test_prepared = full_pipeline.transform(X_test)

final_predictions = final_model.predict(X_test_prepared)

  

final_mse = mean_squared_error(y_test, final_predictions)

final_rmse = np.sqrt(final_mse)
```

```python
final_rmse
>> 47362.98158022501
```

오차 값을 단일 추정값으로 확인하는 것이 아니라, 얼마나 정확한지를 `Scipy.stats.t.interval()` 기반 95% 신뢰 구간 계산을 통해 점검해볼 수 있다.

```python
from scipy import stats

  

confidence = 0.95

squared_errors = (final_predictions - y_test) ** 2

np.sqrt(stats.t.interval(confidence, len(squared_errors) - 1,

loc=squared_errors.mean(),

scale=stats.sem(squared_errors)))
```

```python
>>> array([45397.61151846, 49249.98392646])
```