---
title: "XGB Modeling"
tags :
- model
- ML 
---

## 1. XGB explained

### XGBoost의 특징

- 병렬 처리 가능
- GPU 지원이 가능
- 추가적으로 **정규화 기능, Tree pruning 기능, Early Stopping, 내장된 교차검증과 결측치 처리** 등

### XGBoost의 대표적인 파라미터

**다룰 수 있는 파라미터가 많기 때문에 Customizing이 용이하다.**

- n_estimators (int) : 내부에서 생성할 결정 트리의 개수
- max_depth (int) : 생성할 결정 트리의 높이
- learning_rate (float) : 훈련량, 학습 시 모델을 얼마나 업데이트할지 결정하는 값
- colsample_bytree (float) : 열 샘플링에 사용하는 비율
- subsample (float) : 행 샘플링에 사용하는 비율
- reg_alpha (float) : L1 정규화 계수
- reg_lambda (float) : L2 정규화 계수
- booster (str) : 부스팅 방법 (gblinear / gbtree / dart)
- random_state (int) : 내부적으로 사용되는 난수값
- n_jobs (int) : 병렬처리에 사용할 CPU 수

## 2. Usage

### 분류 문제
```python
from xgboost import XGBClassifier
from sklearn.metrics import roc_auc_score

# 원래 여기 데이터에는 검증 데이터를 넣어야함 Test 데이터 넣으면 안됨!
# 검증 데이터 넣어주어서 교차검증 해보도록하기
evals = [(x_test, y_test)]
xgb_wrapper = XGBClassifier(n_estimators=100, learning_rate=0.1,
                           max_depth=3)
                           
# eval_metric넣어주면서 검증 데이터로 loss 측정할 때 사용할 metric 지정
xgb_wrapper.fit(x_train, y_train, early_stopping_rounds=200,
               eval_set=evals, eval_metric='auc')
# Prediction 1
print('Train Score : {}'.format(xgb_wrapper.score(X_train, y_train)))
print('Test Score : {}'.format(xgb_wrapper.score(X_test,y_test)))

# Prediction 2
preds = xgb_wrapper.predict(x_test)
preds_proba = xgb_wrapper.predict_proba(x_test)[:, 1]
print(preds_proba[:10])

# 모델 평가
xgb_roc_score = roc_auc_score(
    y_test,
    xgb_wrapper.predict_proba(X_test)[:, 1]
)
```

### Missing value는?

XGBoost는 누락 값에 대해서 어떻게 대응할 지 알아서 정하도록 설정되어 있다. 따라서 우리가 해줘야 되는 가공 작업은 단순히 **누락값을 전부 0으로 바꿔주는 것**이다. 

```python
# 누락된 값이 있는 행의 개수 = 누락 데이터 개수
len(df.loc[df['Total_Charges'] == ' '])

# 누락된 행 직접보기
df.loc[df['Total_Charges'] == ' ']

# 직접 바꾸기
df.loc[(df['Total_Charges'] == ' '), 'Total_Charges'] = 0
```

### Categorical values는?

```python
pd.get_dummies(X, columns = ['Payment_Method'])
```

### 성능 알아보기
```python
val_error = mean_squared_error(y_val, y_pred)
print("XGB's Validation MSE:", val_error)
```

### 회귀 문제
```python
from xgboost import XGBRegressor # XGBRegressor 모델 선언 후 Fitting
xgbr = XGBRegressor() 
xgbr.fit(x_train, y_train) # Fitting된 모델로x_valid를 통해 예측을 진행 

# Prediction 1
print('Train Score : {}'.format(xgbr.score(X_train, y_train)))
print('Test Score : {}'.format(xgbr.score(X_test,y_test)))

# Prediction 2
y_pred = xgbr.predict(x_valid)
```

XGBoost는 feature별 중요도를 plot 해주는 라이브러리를 개별적으로 제공한다. feature별 중요도를 보기 위해서 간단하게 시각화하는 코드는 다음과 같다.

```python
# feature별 중요도 시각화하기
from xgboost import plot_importance

fig, ax = plt.subplots(figsize=(9,11))
plot_importance(xgb_wrapper, ax)
```
