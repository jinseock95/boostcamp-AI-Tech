# Week02 - AI Math

## [Day 07] - 경사하강법

### 1. 경사하강법 기초

경사하강법은 딥러닝에서 가장 기본적면서도 중요한 학습 방법입니다. 경사하강법을 이해하기 위해서는 먼저 미분에 대해서 먼저 이해하여야 한다.

#### 1) 미분, differentiation

미분은 변수의 움직임에 따른 함수값의 변화를 측정하기 위한 도구로 최적화에서 제일 많이 사용하는 기법이다. 미분에서는 극한의 개념이 사용되는데, 지점과 지점 간의 변화량을 바탕으로 기울기를 구할 수 있게 되며 변화량이라고도 부른다.

즉, 미분은 주어진 함수 $F()$에서의 **접선의 기울기**를 구하는 것을 의미한다. 한 지점의 기울기를 알게 되면 현재 주어진 지점에서의 증가 혹은 감소 여부를 알 수 있다. 다차원 함수의 경우에서는 시각적으로 증가 혹은 감소를 판단할 수 없기 때문에 기울기를 구함으로써 방향을 알 수 있다.

<image src = https://user-images.githubusercontent.com/48677363/105835107-b9ec1e80-600e-11eb-811c-55677804081f.png width= 580>

  - 미분값을 더함으로써 함수를 최대화하는 것을 경사상승법(gradient ascent)라 하며 목적함수를 최대화할 때 사용함
  - 미분값을 뺌으로써 함수를 최소화하는 것을 경사하강법(gradient descent)라 하며 목적함수를 최소화할 때 사용함
  - 경사상승법/경사하강법에서는 극값에 도달하면 움직임을 멈추게 됨(최적화 되었다고 판단)
  - 시작 지점의 상관없이 해당 함수의 기울기를 통해 경사하강 및 상승법을 반복적으로 적용함으로써 극값에 도달하는 것

#### 2) 편미분, partial differentiation

하지만 변수가 벡터로 표현되어 있을 경우에는 단순 미분을 통해 계산할 수 없으며, 벡터가 입력인 다변수 함수인 경우, 특정 방향의 좌표로 이동하는 미분을 정의하는 **편미분**을 적용할 수 있다.

<image src = https://user-images.githubusercontent.com/48677363/105836598-bf4a6880-6010-11eb-9c6c-c33f7ae031a3.png width = 550>

  - $e_i$ 는 벡터 중 i 번째에만 변화율을 계산할 수 있는 단위벡터를 의미함
  - 각 변수 별로 편미분을 계산한 gradient 벡터를 이용하여 경사하강 및 경사상승법에 사용할 수 있음

❗️gradient 벡터?

-----------

### 2. 경사하강법 심화

#### 1) 경사하강법으로 선형회귀 계수 구하기

선형회귀의 목적식을 먼저 정의하고 이해해야 한다. 목적 함수를 최소화하는 계수를 찾아야 함으로 다음과 같은 gradient 벡터를 구해야 한다.



이론적으로 경사하강법은 미분가능하고 볼록(convex)한 함수에 대해선 적절한 학습률과 학습횟수가 보장된다면 수렴 또한 보장되어 있다.

특히 선형회귀의 경우 목적함수인 $∥y − Xβ∥2$는 회귀계수 $β$에 대해 볼록함수이기 때문에 알고리즘을 충분히 학습하면 수렴이 보장된다.

하지만 비선형회귀 문제의 경우 목적 함수가 볼록하지 않을 수 있으므로 수렴이 무조건 보장된다고 할 수 없다.


#### 2) 확률적 경사하강법

확률적 경사하강법, stochastic gradient descent은 모든 데이터를 사용해서 업데이트하는 대신 데이터 일부를 활용하여 업데이트를 진행하는 방법이다.

non-convex한 목적함수는 SGD를 통해 최적화할 수 있다. 데이터 일부만을 활용해서 파마미터를 업데이트하기 때문에 연산 자원을 좀 더 효율적으로 활용할 수 있다.
이렇게 데이터를 일부만을 활용하는 것을 미니배치를 적용하는 것이다. 

  - 경사하강법은 전체데이터 $𝒟 = (X, y)$ 를 가지고 목적식의 그레디언트 벡터 인 $∇θL(𝒟,θ)$ 를 계산함
  - SGD 는 미니배치 $𝒟(b) = (X(b), y(b)) ⊂ 𝒟$ 를 가지고 그레디언트 벡터를 계산함
  - 미니배치는 확률적으로 선택하므로 목적식 모양이 바뀌게 됨
  - SGD 는 볼록이 아닌 목적 함수에서도 사용 가능하므로 경사하강법보다 머신러닝 학습에 더 효율적임