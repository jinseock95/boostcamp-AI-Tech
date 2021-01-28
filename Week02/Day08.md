# Week02 - AI Math

## [Day 08] - Pandas I / 딥러닝 학습방법 이해하기

### 1. Pandas I

panel data 의 줄임말인 **pandas**는 python의 데이터 처리의 가장 기본적이며 표준 라이브러리이다.

pandas는 python에서 일종의 엑셀과 같은 역할을 하며, 데이터를 전처리하거나 통계 처리 시 많이 활용하는 피벗 테이블 등의 다양한 기능을 사용할 수 있다.
pandas 역시 numpy를 기반으로 개발되어 있고 R의 데이터 처리 문법과 유사한 부분이 많기 때문에 생각보다 빠르게 익숙해질 수 있다.

  - 구조화된 데이터의 처리를 지원하는 python 라이브러리
  - 고성능 array 계산 라이브러이인 numpy와 통합하여 강력한 '스프레드시트' 처리 기능을 제공
  - 인덱싱, 슬라이싱, 연산용 함수, 전처리 함수 등을 제공함
  - 데이터 처리 및 통계 분석을 위해 사용함
  - tabular 데이터를 다루는 것에 가장 최적화 되어 있음

❗️tabular data

#### 1) DataFrame, 데이터프레임

데이터를 tabular 형태로 나타난 데이터 형식으로 엑셀의 스프레드시트와 유사한 형태이다.
기본적으로 행과 열로 구성되어 있는 데이터프레임은 열(column)에는 속성(attribute)과 속성에 대한 값들이 담기게 되고 행(row)에는 행에 해당하는 속성 값들의 모음으로 데이터프레임은 행 데이터의 집합이라고 볼 수 있다.

<image src = https://user-images.githubusercontent.com/48677363/105959646-83baa780-60bf-11eb-949b-a0e51d2650ac.png width = 600>

  - Numpy array-like
  - Series의 모음 object
  - 각 Series는 모두 다른 data type을 가질 수 있음
  - 각 row는 데이터프레임 고유의 index를 가지고 있으며, 모든 Series는 해당 index에 매핑되어 있음
  - 행렬과 마찬가지고 행과 열로 indexing이 가능함
    - **loc**: index search, 인덱스로 검색
    - **iloc**: index position search, 인덱스 위치로 검색

#### 2) Series, 시리즈

데이터프레임 중 하나의 columns에 해당하는 벡터를 표현하는 object이다. Series는 벡터와 매핑되는 index와 벡터, 그리고 해당 벡터들의 data type으로 구성되어 있다.

<image src = https://user-images.githubusercontent.com/48677363/105960760-02fcab00-60c1-11eb-817f-d03e5d669d6c.png width = 300>

  - numpy.ndarray를 기반으로 한 subclass
  - iteration과 vectorize가 가능함
  - index로 데이터를 호출할 수 있음
  - dictionary 형태의 데이터를 Series로 변환할 수 있으며, key-value가 index-value로 변환됨

#### 3) data handling

##### (1) columns

  - columns을 선택할 때는 3가지 방법이 있음
    - `df[column]` -> pd.Series 형태로 column 출력 (여려 개의 columns 출력 불가)
    - `df[[column]]` -> pd.DataFrame 형태로 column 출력 (여려 개의 columns 출력 가능)
    - `df.iloc[:, 1:3]` -> iloc으로 슬라이싱하는 방법으로, 첫번째~두번째 column을 출력 가능
  - column 명을 변경하는 방법은 다양함
    - `df.rename(columns = {기존column명 : 변경column명})`
    - `df.columns = ['A', 'B', 'C']` -> 한번에 바꿀 때만 가능함, 슬라이싱해서 column명을 바꿀 수는 없음
  - column 삭제하는 방법
    - `del df[column]`
    - `df.drop(column, axis = 1)`

##### (2) Rows

  - row를 선택하는 방법 또한 다양함
    - `df.loc[index명]`
    - `df.iloc[index position]`
    - `df.loc[index명, column(s)]`
  - row의 index를 변경하는 방법
    - `df.index = 변경할 index` -> index의 개수가 일치해야함
    - `df.reset_index(drop = True)` -> 현재 position으로 index 초기화, drop = True로 기존 index 삭제
  - row를 삭제하는 방법
    - `df.drop(index, axis = 0)`

##### (3) 조건 추출

pandas의 데이터프레임은 행렬에서 행과 열을 조건에 따라 선택하는 것과 같이 조건에 따라 행과 열을 선별할 수 있다.

  - `df.loc[df[column] == 1(조건)]` -> 해당 column의 조건에 해당하는 행을 출력
  - `df.oc[(df[column] == 1) & (df[column] > 10)]`
  - `df.query('column == 1(조건)')` -> 해당 column의 조건에 해당하는 행을 출력
  - `df.query('column == @zero')` -> @ 표시로 변수를 인식할 수는 있음

##### (4) 데이터 연산

보통 데이터프레임에서 데이터 전처리를 위한 연산을 적용할 때에는 column을 기준으로 적용하는 경우가 많다. 보통 column과 column은 독립적이라고 가정하기 때문에 column에 따라 적용해야할 처리가 다르기 때문이다.

  - `df.apply(f)` -> 모든 Series에 해당 f 함수를 적용하는 방법 
  - `df[column].apply(lambda x : f(x))` ->  해당 Series의 모든 벡터에 해당 f 함수를 적용하는 방법
  - `df[column].astype(int)` -> 해당 Series의 data type을 변경 방법
  - `df[column].diff()` -> 해당 Series의 앞과 뒤의 vector 차를 구하는 방법

##### (5) built-in Function

  - **describe**: Numeric type 데이터의 요약 정보를 반환
  - **unique**: Series data의 고유 값을 반환
  - **sum(axis = )**: 축을 기준으로 행과 열의 합산 값을 반환
  - **isnull**: 모든 데이터 값 == Null에 대한 결과를 반환
  - **fillna('')**: Null 값을 ''로 채워주는 결과를 반환
  - sort_values, value_counts....

----------

### 2. 딥러닝 학습방법 이해하기

이전 강의에서 배운 선형 모델은 단순하거나 저차원 데이터를 해석할 때는 유용하지만 분류 문제와 고차원 문제에 적용할 때에는 예측률이 높지 않다.
이를 개선하기 위해 비선형 모델인 신경망을 도입할 수 있고 보다 높은 예측률을 얻을 수 있다.

이번 강의에서는 신경망 구조에 존재하는 layer와 활성화 함수, 그리고 학습 과정인 역전파 알고리즘에 대한 기본적인 개념을 학습하게 된다.

#### 1) 신경망, Neural Network

Neural Network, 신경망은 뇌의 기본 구조 조직인 뉴런(neuron)과 뉴런이 연결되어 일을 처리하는 과정에서 영감을 얻은 통계학적 학습 알고리즘이다.

화학적 또는 전지적 신호를 전송하고 처리하는 세포인 뉴런이 서로 연결되어 일을 처리하는 것처럼, 수학적 모델로서의 뉴런이 상호 연결되어 네트워크를 형성할 때 이를 **신경망, Neural Network**라고 한다.

#### 2) 신경망 구조

신경망은 기본적으로 신호를 받아들이는 **입력층(input layer)**, 뉴런이 상호작용하는 **은닉층(hidden layer)**, 그리고 결과가 출력되는 **출력층(output layer)** 로 구성되어 있다.

신경망이라는 네트워크를 통해 데이터 간의 비선형적인 문제를 해결할 수 있는 이유는 뉴런이 상호작용하여 계산이 발생하는 은닉층에서 선형 계산과 비선형 계산이 모두 이뤄지기 때문이다. 그러므로 은닉층의 층이 깊어질수록 선형 함수와 비선형 함수와의 조합을 바탕으로 어떠한 비선형적인 특징을 찾을 수 있는 것이 신경망의 가장 큰 장점이다.

##### 소프트맥스

소프트맥스(softmax) 함수는 모델의 출력을 확률로 해석할 수 있게 변환해주는 연산을 가집니다. 분류 문제, classification에서 어떠한 class에 분류될 확률을 반환해준다. 

<image src = https://user-images.githubusercontent.com/48677363/106079476-a4830b80-6158-11eb-9556-a0c8a04e656f.png width = 500>

<br>
<br>

```python
output = np.array([[1,2,3], # 마지막 layer의 출력값
                   [0,1,3],
                   [1,0,0]])

def softmax(x):
    denumerator = np.exp(x - np.max(x, axis = -1, keepdims = True))
    numerator = np.sum(denumerator, axis = -1, keepdims = True)
    val = denumerator / numerator
    return val

class_prob = softmax(output) # 마지막 layer의 출력값을 classification을 위한 확률값으로 변환
-> array([[0.09003057, 0.24472847, 0.66524096],
          [0.04201007, 0.1141952 , 0.84379473],
          [0.57611688, 0.21194156, 0.21194156]])

[np.argmax(prob) for prob in class_prob] # 어떤 class가 가장 확률이 높은지 
-> [2, 2, 0]
```

#### 3) 활성화 함수

활성화 함수는 선형 함수로부터 전달 받은 값을 출력할 때, 일정 기준에 따라 출력값을 변화시키는 비선형 함수이다.  즉, 활성화 함수없이 딥러닝 모델을 구현하게 되면 선형 모델의 연속에 불과하게 된다. 

전통적으로는 시그모이드(sigmoid)와 tanh 함수를 많이 사용했지만 ReLU 함수의 등장 이후로는, ReLU 함수를 통상적으로 사용한다. 활성화 함수는 각 함수가 가지는 특징이 다르기 때문에 데이터와 모델에 따라 다양한 활성화 함수를 시도해보는 것이 좋은 성능을 이끌어낼 수 있다.

<image src = https://user-images.githubusercontent.com/48677363/106081630-8ae3c300-615c-11eb-9498-347faefba8ae.png width = 550>

  - **sigmoid: {0 <= a <= 1}**: z값이 너무 작거나 크게 되면, 기울기(slope)가 0에 가까워짐으로 gradient descent가 매우 천천히 진행되어 성능이 좋지 않아, output layer에서 주로 사용되는 함수임

  - **tanh: {-1 <= a <= 1}**: 대부분의 경우에 sigmoid보다 좋은 성능을 보이며 값의 범위가 -1과 +1 사이에 위치하게 되면서, 데이터 평균값이 0에 가깝게 유지되어 다음 층에서의 학습이 보다 수월함

  - **Relu: max(0, z)**: z가 0보다 클 때, 본래의 기울기를 가지는 특징으로 빠르게 gradient descent로 학습해 나갈 수 있기에, 가장 보편적으로 사용되는 함수임

  - **Leaky Relu**: Relu가 0의 값을 가질 때, 성능이 저하되는 것을 방지하기 위해 개선한 함수임



#### 4) 역전파 알고리즘

역전파 알고리즘인 backpropagation은 순전파 알고리즘을 통해 얻은 output과 실제 값과의 차이(loss)를 시작으로 각 층의 변화량을 기반하여 parameter를 반복적으로 업데이트하면서 loss를 줄여나가는 학습 방법이다.