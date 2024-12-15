# 1 Machine learning (ML)

- 데이터를 기반으로 패턴을 학습하고 예측을 수행하는 컴퓨터
  과학 분야
- 예) 스팸 필터, 음성 인식, 이미지 분류, ChatGPT

## 1 ML 주요 특징

Research VS Production

- 1 Purpose
  - for Research
  - for Pruduction
- 2 Stakeholder
  - Engineer: seek performance
  - Sales: seek money
  - Product Manager: seek UX
- 3 Computation
  - for Latency (지연시간)
  - for Throughtput (처리량)
- 4 Data
  - Research - refined
  - Production - not refined, changable
- 5 Fairness
  - Research - not important
  - Production - important
- 6 Interpretability
  - AI 모델이 왜 그런 결정을 내렸는지 설명할 수 있는 능력
  - 의료 진단 : 암 진단, 질병 진단
  - 모델 개발시 사용된 feature(데이터)와 결과 간의 상관관계를 분석

## 2 ML 개발 과정

- 1 학습 데이터 준비
  - 머신러닝 모델의 목적에 맞춰서 학습 데이터를 준비
  - Data 수집, Data 유형에 따른 처리, Data Sampling, Labeling, Class Imbalance 고려
- 2 Feature Engineering
  - 데이터를 모델에 학습할 수 있는 형태로 Engineering
  - Data Cleansing, Feature Selection, Feature Reduction, Data Augmentation, Data Scaling & Encoding
- 3 모델 학습 및 최적화 평가
  - 모델을 목적에 맞게 학습하고 평가, 최적화
  - Model Training, Model Evaluation, Model Hyperparameter Tuning, Model Selection, Ensembles & Auto ML

## 3 ML 개발 사례

**숙박 추천 모델 개발**: 사용자의 프로필,
검색 기록 등을 활용하여 맞춤형 숙박 추천
서비스를 제공을 목적한다.

### 1단계 : 학습 데이터 준비 (문제인식 포함)

- 숙박 데이터 수집 방법 설계
- 개인 정보 보호 검토
- 숙박 데이터 수집
- 레이블링 (정답셋)

### 2단계 : Feature Engineering (전처리)

- 데이터 정제 및 결측치 처리
- 데이터 분석
- 변환 및 스케일링
- 데이터 분할 및 검증 세트 구성

### 3단계 : 모델 학습 및 평가

- 여러 가지 머신러닝 알고리즘 검토
- 모델 선택 프로세스
- 모델 훈련 및 성능 평가
