# Gradient Descent

## 컴퓨터에 $x^2$의 최적값 찾기  
$$
    f(x) = x^2 \\
    x_{new} = x_{old} - \alpha \times (\frac{dy}{dx})
$$
$$
\begin{bmatrix}
1 \\
1 - 0.1\times2\times1=0.8 \\
0.8-0.2\times2\times0.8=0.64 \\
\vdots \\
x_{old}\,-\alpha\,\times\frac{dy}{dx}(x_{old}) = x_{new}
\end{bmatrix}
$$  

위 수식을 코드로 표현하면 아래와 같다.  


```python
x = np.arange(-10, 10, 1)
f_x = x ** 2

x_new = 1
derivate = []
y = []
learning_rate = 0.1
for i in range(100):
    old_value = x_new
    derivative.append(old_value - learning_rate * 2 * old_value)
    x_new = old_value - learning_rate * 2 * oldvalue
    y.append(x_new ** 2)

plt.plot(x, f_x)
plt.scatter(derivative, y)
plt.show()
```  

> **Learning rate** 에 대한 선정  
> 얼마나 많이 loop 를 돌 것인가?  

* Learning rate가 너무 작을 경우 
  - 끝까지 못감
* Learning rate가 너무 클 경우 
  - 데이터가 튀는 문제가 생겨서 수렴하지 못하는 경우가 생김

### 굴곡이 많은 함수의 경우는?
$$
f(x) = x\sin(x^2) + 1 \\ \, \\
\frac{df(x)}{dx} = \sin(x^2) + 2x^2\cos(x^2) \\ \, \\
x := x\,-\alpha \times\sin(x^2) + 2x^2\cos(x^2)
$$

> 시작점에 따라서 최고최적값을 못 찾을 수 있다.