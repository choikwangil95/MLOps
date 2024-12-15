# 7 Model Selection

정의

- 주어진 데이터에 대해 가장 잘 맞는 머신러닝 알고리즘을 선택하는 과정
- 데이터의 특성을 잘 표현할 수 있는 모델의 구조를 결정하고, 최적의 hyperparameter를 찾는 것이 포함
- 과정의 목표는 일반화 오류(Generalization error)를 최소화하는 것, 새로운 데이터(unseen data)에 대한 모델의 예측 성능을 높이는 것

## Model Selection 방법

- Train/Validation/Test Split Validation

  - 데이터를 훈련, 검증 그리고 테스트 세트로 나눔
  - 훈련 데이터로 다양한 모델을 학습시키고, 검증 데이터를 사용하여 성능을 평가하여 최적의 모델을 선택
  - 선택된 모델은 테스트 데이터로 한 번 더 평가하여 최종 성능을 검증

- Cross-Validation

  - 데이터 세트를 k개의 서브셋으로 나누고, k-1개의 서브셋으로 모델을 훈련시킨 후 나머지 1개의 서브셋으로 성능을 검증
  - 이 과정을 k번 반복하여 모든 서브셋이 최소 한 번은 검증 데이터로 쓰임
  - 각 반복에서의 성능을 평균내어 모델 성능을 평가하고 선택

- Information Criterion Approaches

- Grid Search, Random Search, Bayesian Optimization
  - Grid Search : 모든 hyperparameter 조합을 시험하여 최적의 조합 찾음
  - Random Search : hyperparameter의 특정 범위 내에서의 무작위로 조합을 선택하여 시험
  - Bayesian Optimization : hyperparameter 성능을 모델링하고, 이 모델을 사용하여 시험해 볼 가장 유망한 hypermWparameter를 선택
- Ensemble Methods
  - 여러 모델을 조합하여 단일 모델보다 더 좋은 성능을 내는 방법
  - Bagging, boosting, stacking 방법을 활용

## 주요 고려 사항

- 데이터 크기, Feature 수, 예측 문제의 복잡성, 실행 시간, 해석 가능성, 그리고 마지막으로 하드웨어 제약 등을 고려해야 한다.
- Model selection은 대부분 experiment 기반 접근과 통계적인 방법론을 혼합하여 수행되며, 최종 목표는 실제 세계 데이터에 대한 예측력을 최대화하는 것
