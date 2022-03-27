---
title:  "Machine learning and Deep learning"
excerpt: "머신러닝과 딥러닝에 대해 araboja"

categories:
  - Data mining
tags:
  - [Machine learning, Deep learning,Data mining,Python]

toc: true
toc_sticky: true
 
date: 2022-03-04
last_modified_at: 2022-03-04
---
   
**Machine learning이란?**   
- 명시적 프로그래밍 없이 컴퓨터 스스로 학습할 수 있는 능력을 갖추게 하는 분야.
- 최초의 도입 분야는 통계학이다. ->Statistics Learning
- Neural Network는 Statistics Learning의 한 분야.
- Neural Network의 구체화가 Deep Learning.
**Deep learning은 Machine learning의 한 분야이다!**   

- Supervised Learning   
:지속된 정보가 축적되었을 때 새로 들어오는 데이터의 문제와 해답 습득하는 방식. (학습이랑 문제(feature)와 정답(target)을 반복을 통해 해결하는것.)
- Un-Supervised Learning   
:데이터에 문제만 존재하고 해답이 없어 그룹화, 군집화 등이 존재한다.
- semi-Supervised Learning  
:레이블이 존재하는 데이터를 학습시키고 이 모형으로 레이블이 없는 Data의 레이블을 추정한다.
- Reinforcement Learning  
:무조건 반사의 학습과정과 비슷하게 현재 policy에 의해 의사결정을 하고 실행한 뒤 결과를 통해 policy를 수정한다.   
   
딥러닝은 히든 레이어가 여러 개인 신경망 모형이다.
신경망 모형은 계산시간의 비약적 증가에도 큰 성과를 내지 못했다. 하지만 빅데이터, Iot 시대를 맞아 영상, 사운드 인식 분야에서 다시 성과를 이루어 냈다.
딥려닝의 부활은.
1. 빅데이터
2. GPU 연산
3. 과거 신경망 모형이 갖고있는 단점을 보완 by 수학과 통계학.
을 통해 일어났다.   
활용 분야는 소기, 시계열 데이터, 텍스트, 이미지, 비디오 등....   
***Tensorflow***
* 구글의 머신러닝 라이브러리다.
* 텐서플로우는 딥러닝에 필요한 연산과정을 행렬(텐서) 그리고 텐서의 흐름(플로우)를 나타내는 그래프로 표현하고 실행하는 패키지임
* 수치는 다차원 행렬로 표현함.
* CPU/GPU를 선택적으로 사용 가능함.
* CPU는 정수연산에 최적화, GPU는 부동소수점 연산에  최적화.   

* Small Data -> 통계학에서 사용되는 크기
* Big Data -> 방대한 데이터를 활용하기 위해 단일 컴퓨터로는 힘들어서 분산 처리 Computing을 사용. 즉, 방대한 데이터를 적은 비용으로 활용 가능하게 됨. 이러한 데이터가 딥러닝 알고리즘을 만나 큰 시너지가 나타남.   

* Big Data의 3V -> 속도, 규보, 다양성   

- Static Data: 개체의 속성에 해당하는 데이터로 시간에 따라 바뀌지 않는 데이터를 말함.
- Event Log Data: 개체의 상태에 해당하는 데이터로 시간에 따라 바뀌는 데이터를 말함 처리가 어려움. ->> 빅'데이터'의 데이터를 의미한다.

* 로지스틱 회귀 - 일반적인 회귀결과의 y 치역은 -무한대에서 +무한대까지이다. 우리가 원하는 y는 0 or 1이기에 적절하지 않다.
그래서 로지스틱 합수를 사용한다.

P = 1/1+exp((−θ^T * X)) = S(wx+b)일 때

Cost(w,b)=−(ylog(P)+(1−y)log(1−P)) 이다.
이제 이를 θ에 대해 편미분 하면.
∂/∂θ Cost(w,b)=−(y*(∂log(P)/∂θ)+(1−y)*(∂log(1−P)/∂θ))
이는 합성함수의 미분법인 연쇄 법칙에 의해
=> −(y*(∂log(P)/∂P)*(∂P/∂θ)+(1−y)*(∂log(1−P)/∂(1−P))*(∂(1−P)/∂P)*(∂P/∂θ))
자연로그 log(x)를 x에 대해 편미분하면 1/x가 됨으로
=>−(y*(1/P)*(∂P/∂θ)+(1−y)*(1/1−P)*(−1)*(∂P/∂θ))
=−y*(1/P)*(∂P/∂θ)+(1−y)*(1/1−P)*(∂P/∂θ)
∂P/∂θ 는 P(1−P)X 임으로
=>−y*(1/P)*P(1−P)X+(1−y)*(1/1−P)*P(1−P)X
=−y(1−P)X+(1−y)PX
=−Xy+PXy+PX−PXy
=(P−y)X
즉,∂E/∂θ=(P−y)X = Σ(S(wx+b)-y) = -Σ(y-S(wx+b)) 가 된다.
θ는 w와 b에 대해 말해주고 있음으로,
∂/∂b Cost(w,b) = -Σ(y-S(wx+b))
∂/∂w Cost(w,b) = -Σ(y-S(wx+b))*x 이다.



* Cost 함수는 weight와 x를 곱하는 연산을 수행하는데 X와 W의 범위의 조화가 필요하다. 범위가 0을 중심으로 해야한다!
-> 이를 위해 정규화를 진행한다. = 평균이 0, 분산이 1이 된다.

# LinearRegression_TF2.ipynb
```python
import tensorflow as tf
import numpy as np
x = np.array([1,2,3])
y = np.array([1,2,3])
#
from tensorflow.keras import layers
model = tf.keras.Sequential()
# input과 output이 1개씩이고 선형 함수이다.
model.add(layers.Dense(1, activation='linear', input_dim=1))
#SDG는 stochastic gradient descent 학습률 = 0.1
sgd=tf.keras.optimizers.SGD(0.01)
#loss='mse' -> mse = SSE/n-2 (SSE랑 비슷한 개념이다.)
model.compile(optimizer=sgd,loss='mse’)
# 1000번 시행, 출력 레벨이 2다.
model.fit(x, y, epochs=1000, verbose = 2)
#1,2,3에 대해서 예상값을 구해봐라.
predicted = model.predict(x)
```

```python
import tensorflow as tf
import numpy as np
x=np.array([[1],
[2],
[3],
[4],
[5],
[6]])

y = np.array([[0],[0],[0],[1],[1],[1]])
from tensorflow.keras import layers
model = tf.keras.Sequential()
# 시그모이드 함수의 형태이다.
model.add(layers.Dense(1, activation='sigmoid', input_dim=1))
model.compile(optimizer=tf.keras.optimizers.SGD(0.1),loss='binary_crossentropy’)
model.fit(x, y, epochs=2000, verbose = 0)
predicted = model.predict(x)
print(predicted)
weights = model.layers[0].get_weights()[0]
biases = model.layers[0].get_weights()[1]
print(weights, biases)
```