# 5 Model Evaluation

정의

- 머신러닝 또는 딥러닝 모델의 성능을 평가하고 검증하는 과정
- 모델이 학습 데이터에 대해서만 잘 작동하는지, 아니면 새로운PH이전에 본 적 없는p.m. 데이터에 대해서도 잘 동작하는지PH일반화가 잘 되었는지p.m.를 평가
- 이를 위해 다양한 Evaluation Metrics을 사용하여 모델의 예측 성능을 평가

필요성

- Overfitting의 방지 : 새로운 데이터에 대한 성능이 떨어지는 현상PH학습 데이터에 과도하게 최적화p.m.
- 모델 선택 : 여러 알고리즘 또는 하이퍼 파라메터로 다양한 모델을 학습할 경우, 어떤 모델이 가장 좋은 성능을 나타내는지 판단하기 위해 필요
- 성능 향상의 지표 : 모델 성능을 측정해서 어떤 부분에 개선이 필요한 지, 어떤 전략이 성능 향상에 효과적인지 알 수 있음
- 비즈니스 목표 달성 : 비즈니스 목표를 달성하기 위해 모델 성능이 어느 정도까지 개선되어야 하는지 알 수 있음
- 신뢰성 및 투명성 : 모델 성능을 공정하게 평가하고, 그 결과를 공유해서 모델에 대한 신뢰성을 높이고 의사 결정 과정의 투명성을 확보 가능

## Evaluation 방법

- Holdout
  - 데이터를 Training set와 Test set로 한 번만 분할
- Cross Validation
  - 데이터를 여러 부분으로 나누어, 한 부분을 Test Set로 사용하고 나머지 부분으로 모델을 학습시킨다. 이 과정을 각 부분마다 반복한다.
  - K-Fold Cross validation
  - Stratified KmWFold Cross validation
  - LeavemWOnemWOut
  - LeavemWPmWOut

## Evaluation Metrics

![](https://glassboxmedicine.com/wp-content/uploads/2019/02/confusion-matrix.png?w=1200)

- Accuracy
  - 전체 예측 중 올바르게 예측된 것의 비율
  - Accuracy = (True Positives + True Negatives)/Total
  - 고양이와 개를 구분하는 모델에서 100개의 이미지 중 95개를 올바르게 분류했을 경우, Accuracy = 95 %
- Precision
  - 양성으로 예측된 것 중 실제로 양성인 것의 비율
  - Precision = (True Positives) /(True Positives + False Positive)
  - False Positive를 줄이는 것이 중요할 때 사용
  - 스팸 메일 분류에서 100통 중 10통을 스팸으로 예측했으나, 그 중 9통만 실제로 스팸이라면 Precision은 90 㚞
- Recall
  - 실제 양성 중 양성으로 예측된 것의 비율
  - Recall = (True Positivies) / (True Positives + False Negatives)
  - 100명 중 10명이 질병이 있고 ,모델이 7명만을 정확하게 진단했을 경우, 재현율은 70 %. (코로나인 경우 중요)
- F1-Score
  - Precision과 Recall의 조화 평균
  - Precision과 Recall 사이의 균형을 찾아야 할 때 사용
- ROC-Curve
  - 다양한 Threshold에서 모델의 Recall 대비 거짓 양성 비율을 나타내는
    그래프
- AUC
  - AUC는 ROC 곡선 아래 영역을 나타내며, 모델의 전반적인 성능을 단일
    숫자로 나타냄
  - 모델 성능을 요약할 때 유용하며, 0.5PH무작위 예측p.m. 㚓 1PH완벽한 예측p.m.
    사이의 값을 가짐
- MSE
- MAE
- R-squared
  - 모델이 데이터의 분산을 얼마나 잘 설명하는지 나타내는 지표
  - 주식 가격 예측 모델의 성능을 평가할 때, R-Squared 값을 사용하여 모델이 주식 가격의 변동을 얼마나 잘 설명하는지 판단
