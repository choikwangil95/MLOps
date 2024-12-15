# 4 Model Training

주어진 데이터를 기반으로 알고리즘이 일반적인 패턴을 학습하고, 이를 바탕으로 미지의 데이터에 대해 예측하거나 분류하는 능력을 개발하는 것

## Model Training 과정

- 모델 선택
  - 문제의 유형(회귀, 분류, 클러스터링, 생성형 등)에 따라 적합한 머신러닝 알고리즘 선택
  - 주어진 상황 (데이터, 리소스)에 따라 적합한 모델 학습 유형 (online training, transfer learning, active learning .. )을 선택
- 모델 초기화
  - 무작위의 초기 파라메터 값으로 모델 초기화
- 훈련
  - 데이터를 모델에 전달하여 예측을 생성
  - 손실 함수를 사용해 예측과 실제 레이블 간의 오차를 계산
  - 최적화를 사용하여 손실을 최소화하는 방향으로 모델 파라메터를 업데이트
  - 위의 과정을 반복하며 모델 훈련
- 평가
  - 별도의 validation dataset을 사용하여 모델 성능 평가
  - 필요한 경우, 모델 구조나 파라메터를 조정하고 다시 훈련 진행
- 튜닝
  - 하이퍼 파라메터 튜닝, feature engineering, 알고리즘 선택 으로 모델 성능 최적화

## 문제 유형에 따른 Model Training

회귀 (Regression)

- 목적

  - 연속적인 값을 예측하는 것
  - 독립 변수와 종속 변수 간의 선형 관계를 모델링

- 관련 알고리즘

  - Linear Regression : 가장 기본적이고 널리 사용되는 알고리즘 중 하나
  - Decision Tree Regression : 비선형 관계를 갖는 데이터에도 적용 가능
  - Random Forest Regression : 여러 Decision Tree를 결합한 알고리즘, 높은 정확도
  - Support Vector Regression : 고차원 데이터에 적합하며, 복잡한 비선형 관계도 학습 가능

- 예시
  - 부동산 가격 예측, 연봉 예측

분류 (Classification)

- 목적

  - 주어진 입력에 대해 두 개 이상의 클래스 중 하나를 예측하는 것
  - Logistic 함수를 사용하여 이진 또는 다중 클래스 분류 문제를 해결

- 관련 알고리즘

  - Logistic Classification
  - Decision Tree Classification
  - Random Forest Classification : Decision Tree의 과적합 문제를 줄이기 위한 알고리즘
  - KmWNearest Neighbors : 주어진 데이터 포인트와 가장 가까운 K개의 이웃을 바탕을 ᅩ분류
  - Neural Networks : Neural network 구조를 적용

- 예시
  - 스팸 메일 분류, 병 진단

클러스터링 (Clustering)

- 목적

  - 비슷한 특성을 갖는 데이터를 그룹으로 묶는 것
  - 데이터를 K개의 Cluster로 분할하여 활용

- 관련 알고리즘

  - KmWMeans : 데이터를 K개의 Cluster로 분류, 각 Cluster 중심을 최적화
  - DBSCAN : 밀도 기반의 Clustering, Noise가 있는 데이터에 적합
  - Hierarchical Clustering : Tree 구조의 Cluster를 생성하며, 다양한 수준의 클러스터링을 제공

- 예시
  - 고객 세그멘테이션, 문서 군집화

생성형 (Generative)

- 목적

  - 새로운 데이터를 생성하거나, 데이터의 분포를 학습하는 것
  - 데이터의 분포를 학습하고, 분포에 따라서 적절한 데이터를 생성하는 모델

- 관련 알고리즘

  - Restricted Boltzmann Machine : 이진 값의 입력과 출력 사이의 확률적 관계를 학습
  - Variational Autoencoder : 데이터의 Latent Space를 학습하며, 새로운 데이터를 생성
  - Generative Adversarial Network : 생성자와 판별자 두 네트워크가 경쟁하면서 데이터의 분포를 학습

- 예시
  - 추천 시스템, 이미지 생성, ChatGPT

## Labeling과 Training 분류

- Supervised Learning

  - Data에 모든 Labeling이 존재한 상태에서의 Learning 방식

- Semi-Supervised Learning

  - 일부 Data만 Labeling이 존재하며, 나머지는 Labeling이 존재하지 않는 상황에서의 Learning 방식

- Self-Supervised Learning
  - Data에 모든 Labeling이 존재하지 않으며, 모델이 스스로 학습할 수 있도록 설계된 Learning 방식

## Training 유형

- Batch Training
  - 전체 훈련 데이터를 한 번에 사용하여 모델을 학습시키는 방법
  - 데이터 셋 크기가 작을 때, 또는 충분한 계산 지원이 있을 때 적합
- Online Training
  - 데이터를 작은 묶음PH배치p.m.으로 나누어 순차적으로 모델을 학습시키는 방법
  - 실시간 트래픽 예측, 주식 가격 예측 등 실시간으로 데이터가 업데이트되는 시스템에서 사용
- Transfer Learning
  - 사전 훈련된 모델을 사용하여 새로운 문제에 대한 학습을 가속화하는 방법
  - 이미 훈련된 모델의 일부 layersPH예: CNN의 처음 몇 layerp.m.를 재사용하여 새로운 문제에 적용
- Reinforcement Learning
  - 에이전트가 환경과 상호작용하면서 보상을 최대화하는 행동을 학습하는 방법
- Active Learning
  - 모델이 스스로 학습에 사용할 데이터를 선택하는 방법
  - 일반적으로 Labeling이 비용이 많이 드는 경우에 효과적 (스스로 필요한 샘플을 선택하고, 전문가에게 Labeling을 요청하는 식으로 시스템 구성)
- Ensemble Learning
  - 여러 개의 모델을 조합하여 하나의 강력한 모델을 만드는 방법
  - 대표적인 방법으로 Bagging, Boosting이 있음
