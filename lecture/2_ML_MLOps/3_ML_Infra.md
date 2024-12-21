# ML Infra

## Storage

Storage는 MLOps에서 데이터를 저장, 관리, 검색하는 중요한 구성 요소

### 유형

- 클라우드 스토리지 - S3
- 분산 파일 시스템 - Hadoop
- 데이터 웨어하우스
- 데이터 레이크
- Model Registry

## Computing Resource

Computing Resource는 데이터 처리, 모델 트레이닝, 모델 서빙 및 추론에 필요한 컴퓨팅 파워를 제공

### 유형

- 클라우드 기반 컴퓨팅 - EC2, GKE
- GPU/TPU
- 서버리스 컴퓨팅 - AWS Lambda, GC functions
- 컨테이너화된 컴퓨팅 - Docker, K8S cluster

## 환경 관리 툴

소프트웨어 개발에서 특정 프로젝트의 종속성과 설정을 관리하는데 사용되는 도구

### 종류

- Conda
  - 언어 독립적: 주로 Python 프로젝트에 사용되지만, 다른 언어에도 사용할 수 있음
  - 크로스 플랫폼: Linux, Windows, macOS에서 작동
- Virtualenv
  - Python의 가상환경을 생성하는 도구
- Pipenv
- Container 기술 (다음 강의에서 다룸)

## Container

Container 는 애플리케이션과 그 필요한 모든 것(코드, 런타임, 시스템 도구, 시스템 라이브러리 등)을 포함하는 표준화된 단위 .
애플리케이션은 어떤 컴퓨팅 환경에서도 일관되게 실행될 수 있음

![](https://hudi.blog/static/d3eace5d768716e419e7656520ae2529/f79d8/vm-vs-docker.png)

### 주요 구성 요소

- Image - Dockerfile
- Registry - Docker hub, GC Registry
- Container Runtime

### Docker

Docker는 컨테이너화 기술을 사용하여 애플리케이션을 패키징하고 배포하는 데 사용되는 오픈 소스 플랫폼. 이를 통해 애플리케이션을 쉽게 배포하고
실행할 수 있음

### Docker 주요 구성 요소

- Docker Image
- Docker Container
- Docker Daemon
- Docker Registry
- Docker Client
- Docker Volume
- Docker Compose

### Docker 예시

```dockerfile
# 기본 이미지로 Python 3.8 사용
FROM python:3.8-slim

# 작업 디렉토리 설정
WORKDIR /app

# Python 스크립트 복사
COPY hello.py /app

# 스크립트 실행
CMD ["python", "./hello.py"]
```

```
docker build -t hello-world-python .
```

```
docker run hello-workd-python
```

## Orchestrator

다수의 Container를 조정하고 관리하는 시스템. 컨테이너의 배포, 스케일링 및 네트워킹을 자동화

### 주요 기능

- 자동 배포 및 관리
- 스케일링 및 로드 밸런싱
- 자동 복구 및 장애 대응
- 서비스 발견 및 네트워킹
- 업데이트 및 롤백 관리

### 아키텍쳐

![](https://images.velog.io/images/koo8624/post/ea6f796d-3dbb-4966-a477-a851353bd49a/components-of-kubernetes.svg)

- 마스터 컴포넌트
  - API 서버 (kube-apiserver): 쿠버네티스 API를 제공하며, 사용자와
    내부 컴포넌트 간의 중재자 역할
  - 스케줄러 (kube-scheduler): 새로 생성된 파드를 어떤 노드에
    할당할지 결정
  - 컨트롤러 매니저 (kube-controller-manager): 여러 컨트롤러를 실행.
    예를 들어, 노드 컨트롤러, 레플리케이션 컨트롤러
  - etcd: 모든 클러스터 데이터를 저장하는 경량의 분산 키-값 저장소
- 노트 컴포넌트
  - kubelet: 각 노드에서 실행되며, 파드 스펙(Spec)에 설명된 대로
    컨테이너가 실행되고 있는지 확인
  - kube-proxy: 각 노드의 네트워크 규칙을 관리하여 네트워크 통신을
    가능
  - 컨테이너 런타임: 컨테이너 실행을 담당하는 소프트웨어 (예: Docker,
    containerd, CRI-O 등).

### 구성요소

![](https://velog.velcdn.com/images/pinion7/post/27b80769-950b-4aa5-b737-97b05eed13ad/image.png)

- Pod
  - 쿠버네티스에서 배포할 수 있는 가장 작은 작업 단위
  - 하나 이상의 컨테이너를 포함할 수 있으며, 이들은 스토리지와 네트워크를 공유
- Ingress
  - HTTP(S) 요청을 클러스터 내부의 적절한 서비스로 라우팅하고, 다양한 경로 및 도메인에 대한 세밀한 제어
- Service
  - 서비스는 파드의 집합에 대한 안정적인 네트워크 주소를 제공
  - 서비스를 통해 파드 집합에 대한 접근을 관리하고, 로드 밸런싱 및 서비스 발견을 가능
- Deployment
  - 데플로이먼트는 쿠버네티스에서 파드와 레플리카셋의 상태를 선언적으로 관리하는 API 오브젝트
  - 애플리케이션의 배포, 업데이트, 스케일링 등을 자동화하고 관리
- ReplicaSet
  - 레플리카셋은 파드의 복제본을 유지 관리하는 쿠버네티스 오브젝트
  - 파드의 원하는 복제본 수를 지정하고, 지정된 수의 파드 복제본이 항상 실행되고 있도록 보장
- NameSpace

### YAML

YAML : YAML Ain’t Markup Language

- 데이터 직렬화 언어

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  labels:
    app: my-app
spec:
  containers:
    name: my-container
    image: nginx
    ports:
      containerPort: 80
```

## Workflow Management

MLOps에서의 workflow management는 데이터 수집, 처리, 모델 트레이닝 및 배포에 이르는 전체 머신러닝 파이프라인을 체계적으로 계획하고
실행하는 과정

![](https://machinelearninggeek.com/wp-content/uploads/2022/05/image-1024x394.png)

### 구성요소

- 데이터 준비 : 데이터 수집, 정제, 전처리, feature engineering 등의 단계를 포함
- 모델 개발 : 알고리즘 선택, 모델 트레이닝, 하이퍼 파라메터 튜닝 등을 관리
- 평가 및 검증 : 모델 성능을 평가하고 검증 프로세스를 수행
- 배포 및 모니터링 : 트레이닝된 모델을 프로덕션 환경에 배포하고, 지속적으로 모니터링

### 관리도구

- MLFlow: 간단한 실험 추적과 모델 관리를 원하는 환경에 유용
- Apache Airflow
- Kuberflow: Kubernetes 환경에서 대규모 ML 파이프라인을 관리하고 확장해야 하는 환경에 적합

## CI/CD

## 버전 관리

MLOps에서는 코드, 데이터, 모델, 환경 설정 등에 대한 변경 사항을 추적하고 관리하는 프로세스로 확장

![](https://velog.velcdn.com/images/jkseo50/post/5caa8fc0-9bcd-4df1-8b9e-7106e1ec3b4d/image.png)

- 코드: Git, ..
- 데이터: DVC, Git LFS, ..

## HTTP & REST API
