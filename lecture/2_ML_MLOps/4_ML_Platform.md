# ML Platform

## 1 MLFlow

머신러닝 프로젝트를 관리하기 위한 오픈소스 플랫폼

![](https://miro.medium.com/v2/resize:fit:930/1*-BX3BpJxSZroJkSiwNRfGg.png)

### 구성요소

- MLFlow Tracking : 머신러닝 모델 학습 결과를 추적하고, 다양한 프레임워크에서 동작할 수 있는 학습 코드의 재현성을 보장하는 기능
- MLFlow Projects : 머신러닝 프로젝트의 코드, 환경 설정, 종속성 등을 관리
- MLFlow Models : 학습된 머신러닝 모델을 관리하고, 다양한 환경에서 모델을 배포할 수 있는 기능 제공
- MLFlow Registry : 모델 버전을 관리하고, 공동 작업을 위한 모델 저장소를 제공

### 설치 및 환경구축

```bash
pip install mlflow
```

```bash
mlflow ui
```

### MLFlow Tracking

- 1 auto logging

```python
import mlflow

# Mlflow Sklearn을 활용해서 모델 및 메트릭 자동 기록!
mlflow.sklearn.autolog()
```

- 2 custom logging

```python
# tracking uri, experiment 세팅
mlflow.set_tracking_uri("http://127.0.0.1:5000")
mlflow.create_experiment("hellomlflow!")
mlflow.set_experiment("hellomlflow!")

# mlflow 활용해서 Custom Logging을 진행
n_estimator = 80
random_state = 1234

with mlflow.start_run():
    model = RandomForestClassifier(n_estimators=n_estimator, random_state=random_state)
    model.fit(X_train, y_train)
    y_pred = model.predict(X_test)
    accuracy = accuracy_score(y_test, y_pred)
    prf = precision_recall_fscore_support(y_test, y_pred, average="binary")
    mlflow.log_param("n_estimator", n_estimator)
    mlflow.log_metric("accuracy_on_test", accuracy)
    mlflow.log_metric("precision_on_test", prf[0])
    mlflow.log_metric("recall_on_test", prf[1])
    mlflow.log_metric("f1score_on_test", prf[2])
    mlflow.sklearn.log_model(model, "model")
```

### MLFlow Registry

```python
import mlflow
mlflow.set_tracking_uri("http://127.0.0.1:5000")
logged_model = 'runs:/20176bf12c3a4c13a82f431eda9ca951/model'

# mlflow' pyfunc를 활용하여 모델 로드
loaded_model = mlflow.pyfunc.load_model(logged_model)
```

### MLFlow Models

```bash
# model serving

mlflow models serve -m ./mlartifacts/899358510632907849/d20dbd4fbf2a421eab08dadf49bc8e36/artifacts/model -p 5001 --no-conda
```

```python
import pandas as pd
import requests

# Define local host and endpoint url
host = "127.0.0.1"
url = f"http://{host}:5001/invocations"

# Create dictionary with pandas DataFrame in the split orientation
json_data = {"dataframe_split": test_df[:10].to_dict(orient="split")}

# Score model
response = requests.post(url, json=json_data)
print(f"\nPyfunc 'predict_interval':\n${response.json()}")
```

## 2 Google Cloud Platform

- T.B.D
