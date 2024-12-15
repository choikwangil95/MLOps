# 2 학습 데이터 준비

## 1 데이터의 유형 및 저장과 관리

### 데이터 유형

- 정형 데이터 ex) RDB
- 비정형 데이터 ex) txt
- 반정형 데이터 ex) XML
- 실시간 데이터
  - 스트리밍 ex) 금융 거래
  - IoT ex) 미세먼지

### 데이터 저장과 관리

- Database - 정형
- NoSQL Database - 비정형
- Date Warehouse - 정형 (by ETL)
- Data Lake - 비정형

## 2 데이터 sampling

큰 데이터 집합에서 작은 부분 집합을 추출하는 프로세스

통계 및 데이터 분석 분야에서 사용되는 일반적인 기술로, 데이터의 일부를 조사하고 전체 데이터 집합에 대한 결론을 도출하는 데
활용 -> 전체 데이터 셋에 대한 통찰력을 얻거나 계산/저장 공간을 줄이는데 도움

### Data Sampling 종류

- Random Sampling
- Stratified Sampling
  - 데이터를 계층적으로 분류한 후, 각 계층에서 샘플을 추출
  - 예를 들어, 남성과 여성의 성별에 따라 샘플을 추출할 때 사용
- Cluster Sampling
  - 데이터를 여러 그룹 또는 cluster로 나누고 선택된 cluster 내의 모든 데이터를 포함하는 방법
  - 데이터가 고루 분포되지 않은 경우에 유용
- Weight Sampling
  - 데이터 포인트에 가중치를 할당하고 이러한 가중치를 기반으로 샘플을 추출
  - 불균형 데이터 분포를 가진경우 잘 활용됨 (이상치 탐지나 희귀 이벤트 분석과 같이 minor class data가 매우 적은 경우)
- Importance Sampling
  - 확률 분포에 기반한 통계 샘플링 기법

## 3 Labeling과 이에 따른 모델 학습 유형

기계 학습 및 딥러닝 모델을 훈련하기 위해 필요한 데이터에 의미를 부여하는 과정

### Labeling 예시

- Text Labeling
- Image Labeling
- 의료 영상 데이터의 Labeling
- 센서 데이터(라이다, 카메라)의 Labeling

### Labeling과 AI 모델 학습 유형

- Supervised Learning
  - Data에 모든 Labeling이 존재한 상태에서의 Learning 방식
  - Classification : 데이터를 여러 클래스 또는 범주로 분류하는 작업을 수행. 예를 들어, 스팸과 정상 이메일을 구분하는 문제 해결
  - Regression : 연속적인 출력 값을 예측하는 작업을 수행. 예를 들어, 주택 가격 예측과 주식 가격 예측 등의 문제 해결
- Semi-Supervised Learning
  - 일부 Data만 Labeling이 존재하며, 나머지는 Labeling이 존재하지 않는 상황에서의 Learning 방식
  - Co Training
- Self-Supervised Learning
  - Data에 모든 Labeling이 존재하지 않으며, 모델이 스스로 학습할 수 있도록 설계된 Learning 방식
  - Contrastive Learning

### 모델 학습 유형

- Transfer Learning
  - 이미 훈련된 모델을 다른 작업에 적용하는 방법
- Fine Tuning Learning
  - Transfer Learning의 한 형태로, 사전 학습된 모델을 새로운 작업에 맞게 미세 조정하는 과정
- Online Learning
  - 데이터를 순차적으로 처리하면서 모델을 업데이트하는 방식
  - 새로운 데이터가 도착할 때마다 모델을 finetune하며, 스트리밍 데이터나 지속적인 학습을 위해 유용
- Batch Learning
  - 데이터 셋을 한 번에 모델에 입력하는 전통적인 방식

## 4 Class Imbalance

실제 환경에서 데이터 및 클래스 분포가 시간이 지남에 따라 변함. 이로 인해 새롭게 발생하는 Class
Imbalance 문제가 발생할 수 있으므로, 모델을 update하고 재학습해야함.

- 클래스 간의 데이터 불균형을 나타내는 개념
- 예) 희귀 질병을 감지하는 분류 모델에서 질병이 있는 경우PH양성 클래스p.m. 데이터가 드물게 발생하는 경우

### Class Imbalance 조절 방법

- 데이터 기반 접근법 : Resampling 으로 데이터 수를 조절하여 클래스 간 균형을 맞춤
- ML Algorithm 접근법 : model parameter를 조절하여 class imbalance를 고려하도록 모델을 Tuning

### 데이터 접근 방법론 (ReSampling)

- Over Sampling
  - SMOTE (Synthetic Minority OvermWsampling)
  - ADASYN (Adaptive Synthetic Sampling)
- Under Sampling
  - Random UnderSampling
  - Tomek Links UnderSampling
  - ENN PHEdited Nearest Neighborsp.m.
- Combined Sampling
  - SMOTEENN

### ML 알고리즘 방법론

- Model Algorithm 선택
- Class Weight 조정
- Threshold 조정
- 적절한 Metric 사용
- HypermWParameter Tuning
- Validation
- Ensemble 활용

### Class Imbalance 성능 평가 및 선택

- 평가 Metric 선택
  - Precision (정밀도)
  - Recall (재현율)
  - F1-Score
  - ROC Curve
  - AUC
