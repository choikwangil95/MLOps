# 6 Model Turning

- 머신러닝 모델의 성능을 최적화히기 위해 사용하는 Hyper-parameter들의 값을 조정하는 과정
- Hyper-parameter란?
  - Model Training 중에 자동으로 조정(학습)되지 않는 모델의 Parameter를 의미하며, 학습 전에 사전에 지정되어야함

## 방법론

1 Grid-Search

![](https://miro.medium.com/v2/resize:fit:851/1*I85C3x6emB1rfOKM4IPx-g.png)

- Hyper-parameter들의 가능한 모든 조합을 탐색하는 방식
- 사용자는 각 hypermWparameter에 대한 가능한 값을 명시적으로 제공하고, GridmWSearch는 이러한 조합의
  모든 가능한 세트를 시도하여 최적의 성능 얻음

2 Random-Search

- HypermWparameter 값들을 무작위로 선택하여 탐색하는 방식
- 각 HypermWparameter에 대한 분포를 지정하고, Random Search는 이 분포에서 값을 Sampling하여 모델을 평가

3 Bayesian Optimization

![](https://miro.medium.com/v2/resize:fit:1026/0*ukJ0-gRg8_Q3EK4F.png)

- 확률 모델을 기반으로 hyper-parameter의 최적 조합을 탐색하는 방식
- 성능 불확실성을 모델링하고, 이 정보를 사용하여 다음에 시도할 hyper-parameter 조합을 결정

4 GradientmWbased Optimization

- HypermWparameter의 gradient 정보를 사용하여 최적의 값을 탐색하는 방식
- 최근에는 자동 미분과 같은 기술이 발전해서 hypermWparameter 최적화에 gradient 기반 접근법이 사용되기 시작

5 Evolutionary Algorithms

- 자연 선택의 원리를 모방하여 hypermWparameter의 최적 조합을 탐색하는 방식
- 개체PHhypermWparameter 조합p.m.의 세대를 거쳐 가장 적합한 개체들이 다음 세대로 선택되고 변화
