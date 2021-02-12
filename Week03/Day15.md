# Week03 - DL Basic

## [Day 15] - Generative Models

### 1. Generative Models I

#### 1) Generative Models 의미

**Generative, 생성** 은 '사물이 생겨남. 또는 사물이 생겨 이루어지게 함.'을 의미한다. Generative Models, 생성 모델이 무언가를 만들어내는 모델로 이해할 수 있지만 생성 모델이 가지는 의미에 따라 다양한 과제를 수행할 수 있다.

  - Generation: 학습 후 해당 학습 데이터와 유사한 이미지를 만들어내는 목표 
  - Density estimation: 학습 후 이미지 분류를 하는 목표, anomaly detection에 활용될 수 있음
  - Unsupervies representation learning: 이미지의 보편적인 특징을 학습하는 목표

Density estimation를 보면 분류와 같은 Discriminative의 특징을 가지고 있다. 그렇기 때문에 생성 모델은 단순히 무언가를 만들어내는 모델에 국한되는 것이 아닌 생성과 구분 등과 같은 범위로 확대할 수 있다.

이렇게 입력이 주어졌을 때, 확률과 같은 결과가 출력되는 모델은 explicit generative model이라고 하고 생성 결과를 출력하는 모델을 implicit generative model이라고 한다.

#### 2) Generative Models

생성 모델이 입력되는 데이터의 분포를 파악하기 위해서는 기본적인 확률 분포에 대한 지식이 필요하다.

  - Bernoulli distribution
    - 확률이 P, 1-P인 coin flip
    - 2가지 경우에 대한 확률 표현은 P 1개만 필요
<br>
  - Categorical distribution
    - N개의 경우에 대한 확률 표현은 N-1개 필요

해당 분포에 의거해서 RGB 픽셀을 표현한다면 256가지의 경우가 존재하는 하나의 채널에서 categorical distribution에 의해 255 x 255 x 255개의 parameter가 계산된다. 또한 2가지 경우만 존재하는 흑백 이미지를 표현하기 위해서도 $2^{n} - 1$개의 parameter가 필요하게 된다. 여기서 발생하는 문제는 parameter가 방대하게 되면 모델이 데이터를 학습하는데 어려움을 가진다는 것이다.

학습해야하는 parameter의 개수가 너무 많은 것을 줄이기 위해서, N개의 픽셀을 모두 독립적이라고 가정하는 방법이 있다. 모든 픽셀이 독립적이라고 가정하게 된다면 하나의 픽셀을 표현하고자 하는 parameter 자체는 1개로 표현가능하기 때문에 전체 parameter는 N개가 된다. 

하지만 이렇게 모든 픽셀을 독립적이라고 가정하게 된다면 표현할 수 있는 범위가 굉장히 작아지기 때문에 모든 픽셀을 표현하고자하는 방법과 독립적이라고 가정한 방법 사이의 협의점을 찾아야 한다. 이 때, 3가지 테크닉이 적용된다.

  - Chain rule:




--------


### 2. Generative Models II