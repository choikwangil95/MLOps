# ML Development Process

## 1 문제정의

데이터를 활용해 어떠한 문제를 해결할지 정의한다.

- ex. 직원 Profile 데이터를 활용해 이 직원이 추후 퇴사할 지 여부를 판단한다.
- ex. 항공기가 얼마나 지연되어 도착할 지를 예측한다.

## 2 데이터 전처리

### Data Type and Summary

- Data Type Definition
  - Categorical
  - Numerical (숫자인데 Categorical한 데이터는 heuristic하게 타입 변환해줘야 함)
- Data Cleansing
  - NA Data 처리
  - 이상치 Data 처리
  - 누락 Data 처리

### Dependent Data Explore (target data)

- Imbalance data set
  - 데이터 기반 처리: ReSampling
  - 알고리즘 기반 처리: cost-sensitive learning, ...

### Independent Data Explore

- Categorical Data Analysis
  - 불필요 칼럼 제거 (고유 id, 값이 하나만 존재, 의미없는 데이터 등..)
  - column 분포 확인
  - Target column과 categorical column의 관계 분포 확인
  - 카이제곱 독립성 검정 (두 범주형 변수의 연관성 여부 확인)
- Numerical Data Analysis
  - 불필요 칼럼 제거 (값이 하나거나, ...)
  - column 분포 확인
  - numeric column간에 Correlation Analysis (상관계수 분석)
  - numeric column간에 VIF Analysis (다중공선성 분석)
  - Target Column과 numeric Column 관계 분포 확인
  - 크루스칼 왈리스 검정 (Target Column과 유의미한 관계를 갖는 column 여부 확인)

### Feature Transformation

- Feature Selection (Target Column과 유의미한 관계를 갖는 column)
- Label Encoding
- One-hot Encoding for categorical column dat
- Sampling for imbalanced data (by SMOTEENN, ..)

## 3 모델 분석

- Base Model Learning
- Optimization
  - Optimization 1 : ML with Feature Selection (No samping)
  - Optimization 2 : ML with Feature selection and Combined Sampling
  - Optimization 3 : ML with Feature Selection and No Combined Sampilng + Cost Sensitive Learning
- Base Model과 Optimization Model간의 roc_auc_score 비교
