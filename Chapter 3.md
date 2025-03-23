# Chapter 3

### 2.7 확률적 경사 하강법(Stochastic Gradient Descent)
:하나의 데이터만을 무작위로 선택하여 loss를 계산

ex) 주머니 예시
주머니에서 무작위로 에러 제곱을 뽑음 -> 이 Loss 기반으로 그래디언트 계산, 파라미터 업데이트 
-> 사용한 에러 제곱 제외, 나머지 네 개 중에서 무작위로 하나를 뽑음 -> 주머니가 빌 때까지 반복
-> 주머니가 비면 다시 모든 데이터를 주머니에 넣고 전체 과정 반복 = 1 Epoch
- 덜 신중하게 방향 설정, GD보다 빠르게 최저점에 도달 가능!

- 속도 개선!
- local minimum으로부터 '탈출할 기회를 제공'

### 2.8 Mini-Batch Gradient Descent
대규모 데이터에 SGD를 적용할 경우 다량의 나머지 데이터 무시 문제 발생 보완
- Batch size가 2 .. -> 주머니에서 두개씩 꺼내서 그라디언트를 구하고 업데이트, 반복
- SGD와 GD의 중간 지점인 알고리즘

GPU 사용 -> 병렬적 연산 가능 -> batch size 키울수록 속도 향상 
-> but 로컬 미니멈 문제 -> 적절한 batch size를 찾아야 함

**Batchsize와 Running rate의 조절**
Batch size가 커질수록 validation error가 발생한다는 연구결과
> Linear Scaling Rule : Batch size 두배 늘릴 때 Learning Rate도 두배 늘려야
> Learning Rate Warmup : 0에서 점진적으로 증가시키는 것

Learning Rate Scheduling: Cosin Decay, Step Decay

> Running Rate: 모델이 학습할 때 파라미터를 얼마나 크게 조정할지 결정하는 값
> 파라미터: 모델이 학습을 통해 스스로 조정하는 값, (웨이트, 바이어스)
> 하이퍼파라미터: 학습 전에 사람이 직접 설정하는 값
> (총 Epoch 수, Batch Size, 초기 Learning Rate, Learning Rate Scheduling, 모델의 구조, 사용할 Loss 함수)

-> 현재 시점의 Gradient만 사용하고 있음

### 2.9 Momentum
: 이전 그래디언트들을 더해서 누적하여 현재의 이동 방향을 결정, "관성" 개념과 유사
-> 좌우 움직임은 상쇄, 전반적인 하강 방향 누적

### 2.10 RMSProp(Roor Mean Squared Propagation)
: 각 파라미터에 대한 편미분값을 제곱하여 누적
-> 가파른 축으로는 조심 스럽게, 완만한 축으로는 과감하게 이동

### 2.11 Adam(Adaptive Momentum Estimation)
: Momentum과 RMSProp의 장점을 결합한 최적의 알고리즘


