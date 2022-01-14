# Stochastic Gradient Descent

## Gradient descent
Gradient descent는 한 점을 잡아서 그래프 아래로 내려가는 방법  

일반적으로 여러개의 점의 평균 Gradient를 업데이트하는 것이다.  
이를 **Full-batch Gradient descent**라고 한다.

### **Full-batch gradient descent**
$$
\theta_j := \theta_j - \alpha\frac{\partial}{\partial \theta_j}J(\theta_0, \theta_1) \\ \, \\
\frac{\partial{J}}{\partial{w_n}}=\frac1{m}\sum^m_{i=1}(\mathbf{w}^T\mathbf{x^{(i)}}-y^{(i)})\cdot x_n
$$
- 업데이트 횟수 감소 -> 계산상 효율적
  
- 안정적인 Cost 함수 수렴
  
- 지역 최적화 문제
  
- 메모리 문제 (ex - 30억개의 데이터를 한번에?)
  
- 대규모 dataset -> 모델/파라미터 업데이트가 느림  

### **Stochastic gradient descent**  

- 원래 의미는 dataset에서 random하게 training sample을 뽑은 후 학습할 때 사용함
  
- Data를 넣기 전에 Shuffle
```pseudo
procedure SGD
    shuffle(X)
    for i in number of X do
        $\theta_j := \theta_j - \alpha(\hat{y}^{(i)}-y^{(i)})x^{(i)}_j$
    end for
end procedure
```
$$
\theta_j := \theta_j - \alpha(\hat{y}^{(i)}-y^{(i)})x^{(i)}_j
$$
- 빈번한 업데이트, 모델 성능 및 개선 속도 확인 가능
  
- 일부 문제에 대해 더 빨리 수렴
  
- 지역 최적화 회피
  
- 대용량 데이터 처리시 시간이 오래 걸림
  
- 더 이상 cost가 줄어들지 않는 시점을 발견하기가 어려움

### **Mini-batch SGD**
- 한번의 일정량의 데이터를 랜덤하게 뽑아서 학습
- SGD와 Batch GD를 혼합한 기법
- 가장 일반적으로 쓰이는 기법

#### **Epoch & Batch-size**
epoch
- 전체 데이터가 Training 데이터에 들어갈 때 카운팅
- Full-batch를 n번 실행하면 n epoch

batch-size
- 한번에 학습되는 데이터의 개수

-> 총 5120개의 Training data에 512 batch-size면 몇 번을 학습해야 1epoch이 되는가 = 10번

```pseudo
procedure Mini-Batch SGD
    shuffle(X)
    BS <- BATCH SIZE
    NB <- NUMBER OF BATCHES
    NB <- len(X)//BS
    for i in NB do
        \theta_j := \theta_j - \alpha\sum^{(i+1)\times BS}_{k=i\times BS} (\hat{y}^{(k)} - y^{(k)})x^{(k)}_j
```
$$
\theta_j := \theta_j - \alpha\sum^{(i+1)\times BS}_{k=i\times BS} (\hat{y}^{(k)} - y^{(k)})x^{(k)}_j
$$

## SGD implementation issues

**iteration을 몇번할지 정해야 한다.**

```python
for epoch in range(epoches):
    X_copy = np.copy(X)
    if is_SGD:
        np.random.shuffle(X_copy)
    batch = len(X_copy) // BATCH_SIZE
    for batch_count in range(batch):
        X_batch = np.copy(
            X_copy[batch_count * BATCH_SIZE : (batch_count+1)*BATCH_SIZE]
        )
        #Do weight Update
    print("Number of epoch : %d" % epoch)
```

**Learning rate는 일정해야하는가?**

Learning-rate decay
- 일정한 주기로 Learning rate을 감소시키는 방법
  
- 특정 epoch 마다 Learning rate을 감소
    ```python
    self._eta0 = self._eta0 * self._learning_rate_decay
    ```
- (특정 epoch) Hyper-parameter 설정의 어려움
  
- 지수감소 $\alpha=\alpha_0e^{(-kt)}$, 1/t 감수 $\alpha = \frac{\alpha}{(1+kt)}$

**종료조건 설정**
- SGD과정에서 특정 값 이하로 cost function이 줄어들지 않을 경우 GD를 멈추는 방법
  
- 성능이 좋아지지 않는/필요없는 연산을 방지
  
- 종료조건을 설정 -tol > loss - previous_loss
  
- tol은 hyper parameter로 사람이 설정함