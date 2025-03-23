# Chapter 4

### Training vs Test vs Validation
test 데이터가 학습 때 사용되면 안됨 -> AI가 처음 보는 데이터에 대해서 잘하는 지 봐야함<br>
train 데이터만으로 학습하자니 몇 epoch에서 학습을 멈춰야 할지 모름!
-> **validation**: test 데이터에서 떼어내서 모의 test 데이터로 사용
-> 하이퍼파라미터 설정

### K-Fold Cross Validation
train data가 적어서 일부를 validation으로 쓰기 곤란 -> 편향된 validation 데이터<br>
-> 각기 다른 train, validation 조합의 데이터로 5개의 모델을 만들자<br>
-> 평균 val loss를 구하자 == 가장 val loss 평균이 작은 하이퍼파라미터 set을 고르는데 사용 가능
-> 선택된 set으로 train data 전체에 대해 새롭게 학습 OR 학습했던 5개 모델 결과를 하나로 합침
