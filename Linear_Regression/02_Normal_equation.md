# Normal_equation

$$
y^{(1)} = w_0 + w_1x^{(1)} + \epsilon^{(1)}\\
y^{(2)} = w_0 + w_1x^{(2)} + \epsilon^{(2)}\\
y^{(3)} = w_0 + w_1x^{(3)} + \epsilon^{(3)}\\
y^{(4)} = w_0 + w_1x^{(4)} + \epsilon^{(4)}\\
y^{(5)} = w_0 + w_1x^{(5)} + \epsilon^{(5)}
$$

위의 식을 아래와 같이 행렬로 표현하면 아래와 같다.
($\epsilon$은 무시한다.)

$$
\bold{y} = 
\begin{bmatrix}
y^{1}\\y^{2}\\y^{3}\\y^{4}\\y^{5}
\end{bmatrix}
\qquad
\bold{x} = 
\begin{bmatrix}
1 & x^{(1)} \\ 1 & x^{(2)} \\ 1 & x^{(3)} \\ 1 & x^{(4)} \\ 1 & x^{(5)} \\
\end{bmatrix}
\qquad
\bold{w}=
\begin{bmatrix}
w_0 \\ w_1
\end{bmatrix}
$$
$$
\bold{y} = \bold{x} \bold{w}
$$

아래의 식을 만족하는 $\hat{w}_j$ 값을 구하기
$$
J(w_0, w_1) = \frac1{2m}\sum^m_{i=1}(w_1x^{i} + w_0 - y^{(i)})^2
$$  

$$
\frac{\partial{J}}{\partial{w_0}} = \frac1{m}\sum^m_{i=1}(w_1x^{(i)} + w_0 - y^{(i)}) = 0
$$  

$$  
\frac{\partial{J}}{\partial{w_1}}=\frac1{m}\sum^m_{i=1}(w_1x^{(i)}+w_0-y^{(i)})x^{(i)} = 0
$$

위 미분식을 토대로 $y^{(i)}$와 $y^{(i)}x^{(i)}$을 찾아 이를 행렬로 표현하면 아래와 같아진다
$$
(\mathbf{X}^T\mathbf{X}) \hat{\mathbf{w}} = 
\begin{bmatrix}
m & \sum x^{(i)} \\
\sum x^{(i)} & \sum (x^{(i)})^2
\end{bmatrix}
\begin{bmatrix}w_0 \\ w_1\end{bmatrix}=
\begin{bmatrix}
\sum y^{(i)} \\
\sum y^{(i)}x^{(i)}
\end{bmatrix}
$$
위 행렬식을 토대로 $\mathbf{\hat{w}}$를 구하는 식을 아래와 같이 표현할 수 있다.
$$
\mathbf{X}^T\mathbf{X} \mathbf{\hat{w}} = \mathbf{X}^T\mathbf{y}
$$
$$
\mathbf{\hat{w}} = (\mathbf{X}^T \mathbf{X})^{-1}\mathbf{X}^T\mathbf{y{}}
$$
이제 위 행렬식을 풀어주기 위해서 $\mathbf{X}^T\mathbf{X}$의 역행렬을 구해주면 된다.  
역행렬을 구하기 위해서 행렬식을 구하면 아래와 같다.
$$
\mathbf{X}^T\mathbf{X} = \begin{bmatrix}
m & \sum x^{(i)} \\
\sum x^{(i)} & \sum(x^{(i)})^2
\end{bmatrix}
=
\begin{bmatrix}
m & m\bar{x} \\
m\bar{x} & \sum (x^{(i)})^2
\end{bmatrix}
$$
$$
\begin{aligned}
\det(\mathbf{X}^T\mathbf{X}) &= m\sum(x^{(i)})^2 - (m\bar{x})^2 \\
&=m(\sum(x^{(i)})^2 - m\bar{x}^2) \\
&=m \sum(x^{(i)} - \bar{x})^2  
\end{aligned}

$$

구해준 행렬식을 토대로 역행렬을 구하면 아래와 같다.  
$$
\begin{aligned}
(\mathbf{X}^T\mathbf{X})^{-1} 

&= \frac1{m\sum(x^{(i)} - \bar{x})^2}
\begin{bmatrix}
\sum(x^{(i)})^2 & -m\bar{x} \\
-m\bar{x} & m
\end{bmatrix} \\

&=\frac1{\sum(x^{(i)} - \bar{x})^2}
\begin{bmatrix}
\frac{\sum{(x^{(i)})^2}}{m} & -\bar{x} \\
-\bar{x} & m
\end{bmatrix}
\end{aligned}
$$

위 역행렬을 통해 $\hat{w}$ 를 구할 수 있다.
$$
\begin{cases}
    \hat{w}_1 = \frac{\sum x^{(i)}y^{(i)} - m\bar{x}\bar{y}}{\sum (x^{{(i)}} - \bar{x})^2} \\
\hat{w}_0 = \bar{y} - \hat{w}_1 \bar{x}
\end{cases}
$$

- $\mathbf{X}^T\mathbf{X}$ 의 역행렬이 존재할 때 사용 (현재에 와서는 대부분 역행렬이 존재한다.)  
  
- Iteration등 사용자 지정 parameter가 없음

- Feature가 많으면 계산 속도가 느려짐