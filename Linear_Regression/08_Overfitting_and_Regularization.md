# Overfitting and Regularization

## Overfitting
학습 데이터 과다 최적화 -> 새로운 데이터의 예측률이 떨어짐  
generalization이 중요하다, 평범함이 중요함  

> 보다 적은 수의 논리로 설명이 가능한 경우, 많은 수의 논리를 세우지 말라  
> -Occam's razor  

## Bias-Variance tradeoff

**High bias**
* 원래 모델에서 많이 떨어짐  
잘못된 데이터만 계속 학습함  
->잘못된 weight만 update

**High variance**
* 모든 데이터에 민감하게 학습함  
  Error를 고려하지 않음  
  ->모든 weight가 update


||Low Variance|High Variance|
|-----|:---:|:---:|
|High Bias|Under Fitting||
|Low Bias||Over Fitting|

## Overcoming Overfitting
- 더 많은 데이터를 활용한다. (Best)
  - Gen : Fake 이미지를 만들어서 학습시키는 것
  
- Feature의 개수를 줄인다.

- 적절한 Parameter를 선정한다.
  
- Regularization(정규화)

## Reqularization

$$
J(w_0, w_1) = \frac1{2m}\sum^m_{i=1}(w_1x^{(i)}+w_0-y^{(i)})^2 + (\text{Penalty})
$$
$J(w_0, w_1)$를 줄이는 것이 목표이기 때문에 $\text{Penelty}$를 줌으로써 cost_function의 값을 안늘어나게 하는 방법.

## L2 - Regularization / Ridge

- 기존 Cost function에 L2(norm) penalty term을 추가
$$
J(w_0, w_1) = \frac1{2m}\sum^m_{i=1}(w_1x^{(i)}+w_0-y^{(i)})^2 + \frac{\lambda}{2}\sum^n_{i=1}\theta^2_j
$$

- norm - 벡터의 길이 혹은 크기를 측정하는 방법  
  $||(\theta)||^2_2$ L2는 Euclidean distance 원점에서 벡터 좌표까지의 거리

$$
J(\theta)=\frac1{2m}\sum^m_{i=1}(h_\theta(x^{(i)})-y^{(i)})^2+\frac{\lambda}{2}\sum^n_{i=1}\theta^2_j \\
$$

$$
\theta_0 := \theta_0 - \alpha \frac1{m}\sum^m_{i=1}(h_\theta(x^{(i)})-y^{(i)})x^{(i)}_0
$$

$$
\begin{aligned}
    \theta_j &:= \theta_j - \alpha
    \begin{bmatrix}
        \left(\frac1{m}\sum^m_{i=1}(h_\theta(x^{(i)})-y^{(i)})x^{(i)}_0\right)+\frac{\lambda}{m}\theta_j
    \end{bmatrix}
    j\in\{1, 2 \dots n\} \\
    &:= \theta_j\left(1-\alpha\frac{\lambda}{m}\right) - \alpha\frac1{m}\sum^m_{i=1}(h_\theta(x^{(i)})-y^{(i)})x^{(i)}_0 \quad(1-\alpha\frac{\lambda}{m} \lt 1)
\end{aligned}
$$

## L1 - Regularization

- 기존 Cost function에 L1(norm) penalty term을 추가
$$
J(w_0, w_1) = \frac1{2m}\sum^m_{i=1}(w_1x^{(i)}+w_0-y^{(i)})^2 + \frac{\lambda}{2}\sum^n_{i=1}|\theta_j|
$$

- norm - 벡터의 길이 혹은 크기를 측정하는 방법  
  $||(\theta)||_1 := \sum^n_{i=1}|x_i|$ L1는 manhattan distance 원점에서 벡터 좌표까지의 거리

|L1|L2|
|:-:|:-:|
|Unstable solution|Stable solution|
|Always on solution|Only one solution|
|Sparse solution|Non-sparse solution|
|Feature Selection||  
<br></br>
L2가 조금더 Stable하고 미분하기 편하다.  
L1은 값이 0으로도 나올 수 있다.  
(weight가 0으로 나오면 그 Feature은 안중요하다 할 수 있다  
$\therefore$ 중요한 Feature을 골라주는 기능도 할 수 있다.)