# MLOps

패스트캠퍼스 강의 ([10개 프로젝트로 한 번에 끝내는 MLOps 파이프라인 구현](https://fastcampus.co.kr/data_online_mlopspj))

![](https://www.databricks.com/sites/default/files/inline-images/mlops-cycle.png)

## 목차

- [1 머신러닝 모델 상품화 과정](1-머신러닝-모델-상품화-과정)
- [2 머신러닝 모델 상품화 인프라](1-머신러닝-모델-상품화-인프라)

## 1 머신러닝 모델 상품화 과정

### 1 문제정의

데이터를 활용해 어떠한 문제를 해결할지 정의한다.

- ex) 직원 Profile 데이터를 활용해 이 직원이 추후 퇴사할 지 여부를 판단한다.
- ex) 항공기가 얼마나 지연되어 도착할 지를 예측한다.

### 2 EDA (Explore Data Analysis)

#### Data Processing

- Data Type Definition
  - Categorical or Numerical
  - Dependent or Independent
- Data Cleansing
  - N/A Data 처리
  - 이상치 Data 처리
  - 누락 Data 처리

#### Data Explore

- Dependent Data
  - Imbalance data set 여부 확인
- Independent Data
  - Categorical
    - column별 분포 확인
    - target column과의 분포 확인
    - target column과의 상관관계 확인 (카이제곱 검정)
  - Numerical
    - column별 분포 확인
    - column간의 상관관계 확인 (Correlation Analysis, VIF Analysis)
    - target column과의 분포 확인
    - target column과의 유의미 관계 확인 (크루스칼 왈리스 검정)

### 3 Feature Engineering

- Feature Selection

  - 카이제곱 검정을 통과한 categorical 선택
  - kruskall 검정 통과한 numerical 선택
  - correlation에서 상관관계가 높다고 판단한 numericla data 제거

- Feature Transformation

  - Label Encoding
  - feature scaling for numerical data
  - One-hot Encoding for categorical column dat
  - Sampling for imbalanced data (by SMOTEENN, ..)

### 4 Model Training & Analysis

#### 비교분석 예시

- 1 base model without sampling
- 2 model optimization with base feature
- 3 model optimization with smote oversampling
- 4 model optimization with smoteenn combined sampling

## 머신러닝 모델 상품화 인프라

- T.B.D
