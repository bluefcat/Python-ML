# Performance measure

- Mean Absolute Error(MAE)
$$
\text{MAE} = \frac1{n}\sum^n_{i=1}|y_i-\hat{y}_i|=\frac1{n}\sum^n_{i=1}|e_i|
$$
**잔차의 절대값의 합**  
0에 가까울 수록 좋은 값

- Root Mean Squared Error(RMSE)
$$
\text{RMSE} = \sqrt{\frac1{n}\sum^n_{i=1}(y_i-\hat{y}_i)^2}
$$
**잔차 제곱의 합의 루트**  
0에 가까울 수록 좋은 값

- R squared
$$
R^2=1-\frac{\sum_i(y_i-\hat{y}_i)^2}{\sum_i(y_i-\mu)^2}
$$
**0과 1 사이 숫자로 크면 클수록 높은 적합도를 지님**

## Training & Test data set
- Training 한 데이터로 다시 Test를 할 경우, Training 데이터에 과도하게 fitting된 모델을 사용하게 될 수 있음 (over fitting)
  
- 새로운 데이터가 출현 했을 때, 기존 모델과의 차이 존재 
  
- 모델은 새로운 데이터가 처리 가능하도록 **generalize** 되어야함
  
- 이를 위해 Training Set과 Test Set을 분리함

## Holdout Method(Sampling)
- 데이터를 Training과 Test로 나눠서 모델을 생성하고 테스트하는 기법  
  
- 가장 일반적인 모델 생성을 위한 데이터 랜덤 샘플링 기법
  
- Training과 Test를 나누는 비율은 데이터의 크기에 따라 다름
  
- 일반적으로는 Training Data 2/3, Test Data 1/3를 활용함