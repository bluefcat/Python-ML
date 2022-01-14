# Linear Regression with GD & Implementation

$$
J(w_0, w_1) = \frac1{2m}\sum^m_{i=1}(w_1x^{(i)}+w_0-y^{(i)})^2
$$
**Minimize** $J(w_0, w_1)$

## Linear regression with GD
* 임의의 $\theta_0, \theta_1$ 값으로 초기화  
  
* **Cost function** $J(\theta_0, \theta_1)$이 최소화 될 때까지 학습
  
* 더 이상 **Cost function**이 줄어들지 않거나 학습횟수를 초과할 때 종료
<br></br>
$$
\text{loop until convergence} 
\left\{
    \text{do}\;\theta_j := \theta_j\,-\,\alpha\frac{\partial}{\partial{\theta_j}}J(\theta_0, \theta_1)
\right\}
$$

$$
\begin{cases}
\frac{\partial{J}}{\partial{w_0}} = \frac1{m}\sum^m_{i=1}(w_1x^{(i)}+w_0-y^{(i)}) \\
\frac{\partial{J}}{\partial{w_1}} = \frac1{m}\sum^m_{i=1}(w_1x^{(i)}+w_0-y^{(i)})x^{(i)}
\end{cases}
$$
<br></br>
> $\theta_0, \theta_1$의 값을 동시에 업데이트한다.

* **Learning rate**, **Iteration** 횟수 등 Parameter 지정
  
* Feature가 많으면 Normal equation에 비해 상대적으로 빠름
  
* 최적값에 수렴하지 않을 수도 있다.

### 구현 코드

```python
def gradient_descent(X, y, w, alpha, iterations):
    theta = w
    m = len(y)

    theta_list = [theta.tolist()]
    #hypothesis_fuction(x, theta) is actually X.dot(w)
    cost = cost_function(hypothesis_function(x, theta), y)
    cost_list = [cost]

    for i in range(iterations):
        t0 = theta[0] - (alpha / m) * np.sum(np.dot(X, theta) - y)
        t1 = theta[1] - (alpha / m) * np.sum((np.dot(X, theta) - y) * X[:,1])
        theta = np.array([t0, t1])

        if i % 10 == 0:
            theta_list.append(theta.tolist())
            cost = cost_function(hypothesis_function(X, theta), y)
            cost_list.append(cost)

    return theta, theta_list, cost_list
```
|||
|:---|:---:|
|**hypothesis_function**|$f(x) = h_\theta(x)$
|**cost_function**|$J(w_0, w_1) = \frac1{2m}\sum^m_{i=1}(w_1x^{(i)}+w_0-y^{(i)})^2$
|**t0**|$\frac{\partial{J}}{\partial{w_0}} = \frac1{m}\sum^m_{i=1}(w_1x^{(i)}+w_0-y^{(i)})$
|**t1**|$\frac{\partial{J}}{\partial{w_1}} = \frac1{m}\sum^m_{i=1}(w_1x^{(i)}+w_0-y^{(i)})x^{(i)}$|