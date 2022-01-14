# Cost Function

앞으로 우리는 예측 함수를 **가설 함수**라고 부를 예정  
$$
f(x) = h_{\theta}(x) \to \hat{y}
$$
h는 hypothesis(가설) 이라는 뜻이고  
theta는 우리가 찾아야할 weight 값  

실제 값과 가설 함수의 차이를 **Cost function**이라고 부를 예정
$$
J(w_0, w_1) = \frac{1}{2m} \sum^{m}_{i=1}(h_{\theta}(x^{(i)}) -y^{(i)})^2
$$
(전체 데이터의 갯수가 m)  
($\frac1{2m}$은 미분했을 때 상수를 상쇄시키기 위한 값)  

**Cost function**에서 구하는 것 **Cost function**의 최소화를 위한 **weight** 값

$$
\argmin_{\theta}\frac1{2m}\sum^m_{i=1}(h_{\theta}(x^{(i)})-y^{(i)})^2
$$

($argmin_{\theta}$는 cost function을 최소화 하는 weight 값을 찾으라는 의미다.)  

$$
J(w_0, w_1) = \frac1{2m}\sum^m_{i=1}(w_1x^{i} + w_0 - y^{(i)})^2
$$  

$$
\frac{\partial{J}}{\partial{w_0}} = \frac1{m}\sum^m_{i=1}(w_1x^{(i)} + w_0 - y^{(i)}) \\
$$  

$$  
\frac{\partial{J}}{\partial{w_1}}=\frac1{m}\sum^m_{i=1}(w_1x^{(i)}+w_0-y^{(i)})x^{(i)}
$$

#### 편미분 과정
---

$$let\;A=(w_1x^{(i)}+w_0-y^{(i)})$$
$$J(w_0,w_1) = \frac1{2m}\sum^{m}_{i=1}A^2$$
$$\frac{\partial{J}}{\partial{w_1}} = \frac{\partial{J}}{\partial{A}}\frac{\partial{A}}{\partial{w_1}}$$
$$\frac{\partial{J}}{\partial{A}} = 2A$$
$$\frac{\partial{A}}{\partial{w_1}} = x^{(i)}$$  
## **weight**의 최적값 컴퓨터가 찾는 방법
---
- 연립방정식 풀기 (normal equation)
- gradient descent (거의 안쓴다)