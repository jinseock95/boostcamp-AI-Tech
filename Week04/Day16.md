# Week04 - NLP, Natural Langurage Processing

## [Day 16] - Introduction to NLP

### 1. Intro to NLP, Bag-of-Words

NLP, 자연어 처리의 소개를 시작으로 가장 간단한 모델 중 하나인 Bag-of-Words의 개념에 대해서 다루게 된다.

Bag-of-Words는 one-hot-encoding을 사용하여 단어를 표현하고 단어의 순서를 고려하지 않는 굉장히 간단한 방법이다. 매우 간단한 모델이지만 많은 자연어처리 과제에서 효과적으로 동작하는 알고리즘 중 하나이다. 그리고 Bag-of-Words를 이용해 문서 분류 과제에 활용하는 Naive Bayes Classifier에 대해서도 다루게 된다. 

이번 강의에서는 단어가 벡터로 표현되는 방법, 문서가 벡터로 표현되는 방법에 대해 유념하며 듣는 것이 중요하다.

#### 1) NLP 분야

자연어 처리는 기본적으로 컴퓨터가 주어진 단어나 문장 혹은 문단과 글을 이해하는 Natural Language Understanding(NLU)와 자연어를 상황에 따라 적절히 생성하는 Natural Language Generation(NLG)로 구분된다.

또한, 자연어 처리 분야는 컴퓨터비전 분야와 더불어 인공지능 및 딥러닝 기술이 가장 활발하게 연구되고 발전하고 있다. 

자연어 처리 분야에서도 학문적인 체계로 보면 자연어를 다루는 다양한 분야가 존재한다.

**Natural language processing**

  - Low-level parsing
    - Tokenization: 문장을 이해하기 위해, 문장을 이루는 단어를 정보로 인식하여 단어 단위 혹은 의미 단위로 쪼개는 과정
    - stemming: 형태소 분석 중 하나인 어간 추출을 의미하며, 어미를 자름으로써 동일한 어간을 추출하는 과정

  - Word and phrase level
    - Named entity recognition(NER): 개체명 인식으로 고유명사를 인식하기 위한 과정
    - part-of-speech(POS): 문장 내 단어들의 품사 혹은 성분을 인식하는 과정

  - Sentence level
    - Sentiment analysis: 주어진 문장을 긍정 혹은 부정 어조로 분류하는 과정
    - machine translation: 기계번역으로 주어진 문장을 다른 언어의 문장으로 번역하는 과정

  - Multi-sentence and paragraph level
    - Entailment prediction: 두 문장간의 논리적인 내포 혹은 모순 관계를 예측하는 과정
    - question answering: 독해기반 질의응답으로 질문을 정확하게 이해하고 가지고 있는 데이터를 기반으로 답을 제시하는 과정
    - dialog systems: chat-bot과 같은 대화를 수행할 수 있는 과정
    - summarization: 주어진 문서를 요약하는 과정

**Text Mining**

  - 방대한 규모의 텍스트 데이터에서 유용한 정보와 insight를 추출하는 과정
  - topic modeling을 통한 문서 군집화
  - 텍스트 데이터 분석을 통한 사회현상 혹흔 사회문화와의 논리적인 연관성 분석

**Information retrieval**

  - 정보 검색 기술에 대한 연구가 진행되는 분야
  - 정보 검색 분야에 포함되는 추천 시스템 분야가 최근에는 빠르게 관심을 받고 있으며 발전하고 있음
  - 추천 시스템은 다양한 분야에서 활용되고 있으며 비즈니스적인 부분에서 굉장히 각광받고 있음

#### 2) NLP 동향

**Word Embedding**

먼저 **자연어**란 '사람들이 일상적으로 쓰는 언어를 인공적으로 만들어진 언어인 인공어와 구분하여 부르는 개념'이다. 그렇기 때문에 컴퓨터는 자연어 그 자체를 인식하여 이해할 수 없기 때문에 컴퓨터가 이해할 수 있는 표현법으로 자연어를 변환해야 한다.

자연어를 특정한 차원으로 이루어진 벡터로 표현하는 과정을 거치게 되며, 단어 혹은 토큰을 벡터 공간의 한 점으로 표현한다는 의미로 **Word Embedding, 워드 임베딩** 이라고 한다.

**RNN**

자연어는 소통을 함에 있어 시작과 끝이라는 순서가 존재하는 데이터로 같은 단어 혹은 토큰임에도 입력되는 순서에 따라 가지는 의미가 달라질 수 있다. 이 말은 즉, 같은 단어와 토큰이 워드 임베딩 과정을 거치게 되었을 때, sequence에 따라 워드 임베딩 벡터가 달라질 수 있음을 의미한다. 그렇기 때문에 sequence를 고려한 RNN 모델이 자연어 처리의 핵심 모델로 통상적으로 사용되었다.

**Transformer**

2017년 구글에서 'Attention is all you need' 논문이 발표되면서 기존의 RNN 기반의 자연어 처리 모델 구조를 self-attention 구조의 **Transformer**라는 새로운 모델이 등장하게 되었다. 다양한 자연어 처리 분야에서 Transformer 모델의 성능이 확인되면서 현재 대부분의 자연어 처리를 위한 모델은 Transformer 모델을 기반으로 하고 있다.

Transformer 모델의 시작은 기계 번역에 초점을 맞추고 있었지만 현재에는 자연어 처리의 다양한 분야를 넘어, 영상 처리, 시계열 예측, 신약 개발, 신물질 개발 등 매우 다양한 분야에서 활용되고 있으며 성능 향상을 이뤄내고 있다.

#### 3) Bag-of-Wrods

##### (1) Step of Bag-of_words Representation

**step 1. Constructing the vocabulary contatining unique words**

  - 텍스트 데이터에서 고유 단어를 뽑아내 단어 사전을 구축함
  - 같은 단어인 'really'가 여러 번 등장해도 단어 사전에는 'really'는 한번만 명시됨

```
sentences = ['John really really loves this movie',
             'Jane really likes thig song']

vocabulary = {'John', 'really, 'loves', 'this', 'movie', 'Jane', 'likes', 'song'}
```

**step 2. Encoding unique words to one-hot-vectors**

  - 해당 vocabulary를 categorical 데이터로 인식하여 one-hot 인코딩을 할 수 있음
  - 단어가 원핫벡터로 표현되면 다양한 모델의 입력으로 사용할 수 있음
  - 단어의 의미와 상관없이 모든 단어와의 거리와 유사도가 같게 형성되므로 똑같은 관계를 가지도록 벡터화된 것임

```
vocabulary = {'John', 'really, 'loves', 'this', 'movie', 'Jane', 'likes', 'song'}

John = [1, 0, 0, 0, 0, 0, 0, 0]
really = [0, 1, 0, 0, 0, 0, 0, 0]
.
.
.
song = [0, 0, 0, 0, 0, 0, 0, 1]
```

**step 3. A sentence/document can be represented as the sum of one-hot vectors**

  - 문장에 포함된 단어들의 원핫벡터를 모두 합함으로써 문장 벡터를 생성할 수 있으며 이를 Bag-of-Vector라고 부름 

```
“John really really loves this movie“ = John + really + really + loves + this + movie: [1, 2, 1, 1, 1, 0, 0, 0]

“Jane really likes this song” = Jane + really + likes + this + song: [0, 1, 0, 1, 0, 1, 1, 1]
```

#### 4) Naive Bayes Classifier

나이브베이즈 분류기는 각 클래스가 주어졌을 때, 학습한 확률 분포를 통해 해당 데이터가 속할 확률을 계산하여 가장 높은 확률의 클래스로 분류하는 모델을 말한다.

총 4개의 문서가 CV와 NLP의 클래스로 주어졌을 때, 아직 클래스가 정해져있지 않은 문서의 클래스를 나이브베이즈 분류기를 통해 분류해볼 수 있다.

<center>
<image src = https://user-images.githubusercontent.com/48677363/107906348-3631ac00-6f94-11eb-9c5d-9546fab88a0c.png width = 600>
</center>

  - 각 클래스에 속할 확률은 모두 $1/2$ 임
  - 각 클래스의 확률 분포를 기반으로 추정하고자 하는 test 데이터의 분포를 계산해볼 수 있음

<center>
<image src = https://user-images.githubusercontent.com/48677363/107906583-cd96ff00-6f94-11eb-99e5-4c31027ffd4b.png width = 500>
</center>

  - 클래스 CV의 확률 분포를 기반으로 할 때, test 데이터의 'Classification'은 CV 문서의 14개의 단어 중 1번 등장했으므로 $1/14$의 확률을 가지게 됨
  - 클래스 NLP의 확률 분포를 기반으로 할 때, test 데이터의 'task'는 NLP 문서의 10개의 단어 중 2번 등장했으므로 $2/10$의 확률을 가지게 됨
  - $𝑃(C_{CV}|d_{5})$ = $1/2 + 1/14 + 1/14 + 1/14 + 1/14$ ≈ 
  - $𝑃(C_{NLP}|d_{5})$ = $1/2 + 1/10 + 2/10 + 1/10 + 1/10$ ≈
  - 즉, NLP 클래스에 속할 확률이 보다 높기 때문에 test 데이터는 NLP 클래스로 분류됨

------

### 2. Word Embedding

단어를 컴퓨터가 이해할 수 있는 벡터로 표현하는 대표적인 방법으로 **Word2Vec**과 **GloVe**가 있다.

이 두 방법은 최근까지도 자주 사용되고 있는 Word Embedding 방법이다. 하나의 차원에 단어의 모든 의미를 표현하는 one-hot encoding과 달리 Word2Vec과 GloVe는 단어의 distributed representation을 학습하고자 고안된 모델이다. Word Embedding을 위해 이 두가지 방법이 단어를 학습하는 원리와 과정에 대해 이해할 필요가 있다.

두 word embedding 방법의 핵심 아이디어는 비슷한 의미를 가지는 단어가 좌표 공간상 비슷한 위치에 매핑되게 함으로써 단어들의 의미상의 유사도를 반영하고자 하는 것이다. 이러한 word embedding을 통해서는 의미를 반영한 벡터를 학습하게 되면 다양한 자연어처리 과제를 수행할 때 보다 높은 성능을 보장할 가능성이 높다.

#### 1) Word2Vec

**Wrod2Vec 구조**

유사한 의미의 단어들은 좌표상 비슷한 위치로 매핑하기 위해서 Word2Vec은 주어진 문장에서 비슷한 의미의 단어는 인접한 단어 또한 비슷할 가능성이 높다는 가정을 사용한다. 이 가정은 주변 단어를 통해 해당 단어의 의미를 착안 가능하다는 말로 표현할 수 있다. 주어진 학습 데이터를 바탕으로 특정 단어 주변 단어들의 확률 분포를 예측하게 된다.

Word2Vec의 아키텍처(skip-gram)를 도식화하면 아래 그림과 같다. 입력층, 은닉층, 출력층으로 이루어진 shallow neural network 구조이다.

<center>
<image src = https://user-images.githubusercontent.com/48677363/107929511-1662ae00-6fbd-11eb-9096-c0ca029a828c.png width = 350>
</center>

Word2Vec 구조를 보게 되면 가중치 행렬이 2개 존재하는 것을 알 수 있다. 이 2개의 가중치 행렬은 차원이 서로 전치한 것과 동일하지만 동일한 행렬이 아님을 주의해야 한다. 학습 후, 단어 벡터로 사용하고자 하는 가중치 행렬로는 두 행렬을 하나의 행렬로 취급(tied)하는 방식으로 학습을 진행할 수 있고, 학습이 아주 잘되면 $𝑊_{1}$ 와 $𝑊_{2}$ 중 하나를 사용해도 무방하다고 하다.(출처: [ratgo's blog](https://ratsgo.github.io/from%20frequency%20to%20semantics/2017/03/30/word2vec/))

**Wrod2Vec skip-gram**

**'I study math'** 문장이 주어졌을 때, Word2Vec 과정에 대해서 아주 간단하게 살펴보겠다.

위에서 언급했듯이, Word2Vec은 주변 단어를 통해 중심 단어의 벡터를 유추해나가는 과정을 가진다고 했다. 이 때, 주변 단어의 범위을 window size를 지정함으로써 정의한다. 만약 위 문장에서 window를 1로 부여했을 때에는 다음과 같은 쌍이 이뤄지게 된다.

```
단어 I: (I, study)

단어 study: (study, I), (study, math)

단어 math: (math, study)
```

**Wrod2Vec 학습**

  - **study** 단어가 Word2Vec의 입력으로 One-hot vector로 들어가게 되면 첫번째 가중치 행렬인 $𝑊_{1}$와 내적하게 되면서 해당 단어의 가중치만 남게 됨
  - 의미론상 $𝑊_{1}$에서 study를 의미하는 벡터만 남아있을 때, $𝑊_{2}$와 다시 내적함으로써 출력되는 결과가 전체 단어의 차원으로 나오게 됨으로써, 쌍을 이룬 ground truth 단어와 최대한 가깝도록 학습하게 됨
  - window size가 클수록 중심 단어가 모든 쌍을 돌았을 때, iteration 1회가 마무리됨

<center>
<image src = https://user-images.githubusercontent.com/48677363/107931218-5034b400-6fbf-11eb-8642-3a022a97e9a1.png width = 400>
</center>

#### 2) GloVe

**GloVe**는 Word2Vec이 중심 단어를 기준으로 주변 단어를 통해 의미를 파악하는 과정이 오로지 window 내에서만 학습이 이루어지기 때문에 데이터 전체에 대한 정보를 파악하기 힘들다는 단점을 보완하고자 제안되었다.

GloVe는 문서 내 동시에 등장한 단어의 빈도를 전체 데이터의 단어 개수로 나눠준 동시 등장확률, co-occurrence를 고려함으로써 임베딩된 단어 벡터 간 유사도 측정뿐만 아니라 말뭉치 전체의 통계 정보 또한 포함된 임베딩 벡터를 만드는 것에 집중하였다.




--------
