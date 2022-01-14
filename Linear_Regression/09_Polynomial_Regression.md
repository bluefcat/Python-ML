# Polynomial Regression

## 집의 넓이와 집세의 상관관계
Housing price prediction 을 예측할때  
직선보다 $x^2$과 같은 곡선을 사용하면 더 집값을 잘 예측할 수 있지 않겠느냐

$$
h_\theta(x)=\theta_0+\theta_1x_1+\theta_2x_2+\theta_3x_3 \\
\begin{cases}
x_1 = \text{depth} \\
x_2 = \text{frontag} \\
x_3 = \text{depth}\times\text{frontag}
\end{cases}   
$$

## Polynomial Features
- 1차 방정식을 고차다항식으로 변경하는 기법
  $$x_1 + x_2 \to x_1+x_2+x_1x_2+x_1^2+x_2^2$$
- sklearn.preprocessing.PolynomialFeature 사용

```python
from sklearn.preprocessing import PolynomialFeature
X = np.arange(6).reshape(3, 2)
#if set interaction_only = True x_1 * x_2
#Only add interaction rows
poly = PolynomialFeature(2)
poly.fit_transform(X)
"""
result :1, x_1, x_2, x_1+x_2, x_1^2, x_1x_2, x_2^2
array([[1, 0 ,1, 0, 0, 1],
       [1, 2, 3, 4, 6, 9],
       [1, 4, 5, 16, 20, 25]])
"""
```

## 언제쓰나?
- 한개 변수가 Y값과 비선형적인 관계가 있다고 의심
  
- 주기적인 패턴을 보이는 Series 데이터
  
- 모델 자체가 복잡해지면 해결가능한 부분이 많음
  - SVM, Tree-based models