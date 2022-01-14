<style>
div {
    align : "center";
}
</style>
# Overview 
## 머신러닝의 학습 방법들

* Gradient descent based learning

    실제 값과 학습된 모델 예측치의 오차를 최소화  
    모델의 최적 parameter 찾기가 목적 

    > gradient descent 활용
    
* Probability theory based learning

* Information theory based learning
  
* Distance similarity based leaning

---

<img src="https://platum.kr/wp-content/uploads/2017/06/unnamed-12.png" alt="graph about linear regression" width = 300></img>

예측치 : $\hat{y} = ax + b$ 에서 $ax+b$ 부분이 모델  
데이터로 주어지는 것은 $x$ 와 실제 $y$ 의 값이다.  
그래서 $a$ 와 $b$의 값을 찾아내는 것이 gradient descent 방법이다.  

예측한 값과 실제값의 오차를 줄이는 것

## 예측 함수와 실제 값의 오차를 줄여보자
---

**Squared Error**
$$
\sum_{i = 1}^{n}(\hat{y}^{(i)} - y^{(i)})^{2}
$$ 

$$
\hat{y} = \begin{bmatrix}
w_{1} \times 8759\,+ w_{0} \\
w_{1} \times 10132\,+ w_{0} \\
w_{1} \times 12078\,+ w_{0} \\
w_{1} \times 16430\,+ w_{0}
\end{bmatrix}
\;
y = \begin{bmatrix}
487\\612\\866\\1030
\end{bmatrix}
$$

$$
(\hat{y} - y)^{2} = \begin{bmatrix}
(w_{1} \times 8759\,+ w_{0} - 487)^2\\
(w_{1} \times 10132\,+ w_{0} - 612)^2 \\
(w_{1} \times 12078\,+ w_{0} - 866)^2 \\
(w_{1} \times 16430\,+ w_{0} - 1030)^2 
\end{bmatrix}
$$

squared Error를 최소화 할 수 있는 weight값을 찾는다.

$$
\sum^{n}_{i=1}(w_{1}x^{(i)} + w_{0} - y^{(i)})^{2}
$$

최소 또는 최대의 문제 -> 미분으로 해결하기
찾고자 하는 값은? 
$$w_{1}, w_{0}$$