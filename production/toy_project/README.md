![Alt text](<Untitled (1).png>)

## 계획
### 0 세팅
- 1 (필수) 문제 및 비즈니스 도메인 분석 과 주어진 데이터 이해
- 2 (필수) 로컬 개발환경 세팅 (colab or IDE & github)
- 3 (필수) 개발 기술스택 선정
### 1 로컬 개발
- 3 (필수) 로컬 개발환경에서 data processing, EDA, feature Enginnering 후 feature 저장
  - 동적 데이터에서 파생 피쳐를 생성하여 정적 데이터에 추가 
- 4 (필수) 로컬 개발환경에서 model trainging, evaluation을 하여 model registry에 저장, metadata db에 저장
### 2 상용 개발
- 5 (필수) 상용 mlflow에서 협업으로 model 실험 management를 한다.
- 6 (선택) 상용 airflow에서 로컬 colab에서 진행했던 데이터 프로세싱 및 모델 학습 과정을 워크플로우로 자동화한다.
- 7 (선택) 상용 fastAPI, streamlit으로 모델 API를 서빙하고 추론할 수 있도록 한다.

## 기술스택

- 협업: git, colab
- 피쳐 스토어: S3
- 모델 관리:mlflow, postgreSQL, S3
- 데이터 파이프라인: airflow
- API 서빙: fastAPI
- UI: streamlit
