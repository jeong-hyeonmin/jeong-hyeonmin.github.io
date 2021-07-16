---
title:  "퍼지 제어"
excerpt: "Fuzzy control, 퍼지 제어기 코드"
use_math: true

categories:
  - control theory
---
Capstone design에서 사용했던 퍼지제어기를 간단하게 설명해 보도록 하겠습니다.


# 1. 퍼지이론

지금까지 우리가 다루어 온 집합(crisp set)의 개념은 어느 원소가 집합에 속하는지 속하지 않는지에 대해 확실하게 알 수 있었다. 하지만 일상에서의 경우 많은 집합은 구성 요소의 기준이 명확하지 않다.


방안의 온도가 22도 일때 시원하다라고 하면 22.1도는 시원하지 않은가에 대해서는 의문이 생길 수 있다. 방이 시원하다라는 것에서 온도가 명확히 설정되어 있지 않기 때문이다.

그렇다면 22도 일때는 시원함의 정도가 1, 26도 일때는 시원함이 0.5 와 같은 식으로 정도를 표현할 수 있다면 좀 더 자연스럽게 느껴질 수 있다.

위의 경우 처럼 어떤 원소가 그 집합에 속한 정도까지 나타내는 것을 퍼지 집합이라고 말할 수 있다.

퍼지 집합을 표현하기 위해서는 소속함수(Membership Function)표시법을 사용한다. 소속함수란 어떤 원소가 집합에 속한 정도를 나타내어 주는 함수를 뜻하며 $m_A (x)$로 정의될 수 있다.

<br>

# 2. 퍼지제어
퍼지 제어는 인간의 판단, 애매성을 포함한 제어 알고리즘을 if-then형식으로 표현하고, 퍼지 추론을 이용하여 실행시킨 것입니다.

예를들어 방의 온도를 22도로 유지하는 에어컨 시스템이 있다고 할때 에어컨은 온도가 22도가 넘어서는 순간부터 작동할 것이다.

온도 > 22  $\rightarrow$ 에어컨 on

그리고 온도가 22도가 되거나 내려가면 에어컨은 off 될것이다. 이러한 시스템은 에어컨이 수시로 on과 off를 반복하게 될 것입니다.

효율과 융통성을 높이기 위해서 

온도 > 25  $\rightarrow$ 에어컨 출력 80%

온도 > 30  $\rightarrow$ 에어컨 출력 90%

온도 > 35  $\rightarrow$ 에어컨 출력 100%

와 같이 제어 문장을 추가하면 온도에 따라 다르게 반응 할것 입니다.

이렇게 될때 문제점은 넓은 범위에서 작은 변화에도 반응하기 위해서는 수백 개의 제어문장이 필요하게 될것입니다.

이러한 문제를 퍼지의 소속함수로 해결할 수 있습니다.


<br>

### 퍼지제어기 구조

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/123254111-371db000-d529-11eb-9cec-7290cb594c54.png" width = "500" ></p>

퍼지 제어기의 구조는 다음과 같습니다. 퍼지화기(Fuzzifier), FRB(Fuzzy Rule Base)를 포함한 퍼지 추론부, 비퍼지화기(Defuzzifier)


**퍼지화기**
Fuzzifier는 Crisp한 수치적 정보를 퍼지 집합으로 변화시키는 연산입니다. 방안의 온도가 높으면 에어컨을 세게틀어라 에서 온도를 30도 와 같이 수치로 주어집니다. 이 수치를 퍼지 입력으로 바꾸는 것이 Fuzzifier입니다.


<p align="center"><img src="https://user-images.githubusercontent.com/54671691/123607221-a270c600-d838-11eb-92b4-c0090447dc05.png" width = "500" ></p>

ex) Temperature = 78, Warm,Hot의 적합도는 각각 0.7,0.27임을 알 수 있습니다.

<br>
<br>

**비퍼지화기**

Defuzzifier는 Fuzzifier의 반대기능을 합니다. 퍼지 제어기에서 퍼지 추론부의 출력(퍼지 집합으로 표현됨)으로 부터 수치 데이터(Crisp number data)를 얻어내는 장치입니다.

<br>
<br>

- 무게중심법(Center of gravity Method)

무게중심법은 직관적으로 가장 합리적이고 타당해보이며 가장 많이 쓰는 방법중 하나입니다.
수식적으로 표현하면

$y^*=\frac{\int_v y \cdot m_B(y)dy}{\int_v m_B(y)dy}
$

이때 $m_B(y)$는 출력 퍼지 집합의 소속함수

<br>

- 평균중심법 (Center of Average Method)
무게 중심법이 직관적으로 좋은 방법이지만 적분계산은 많은 시간을 요하므로 대안으로 제시된 것이 평균 중심법이다.

$y^*=\frac{\sum_{I=1}^{M}(y^{-1}\cdot w_I)}{\sum_{I=1}^{M}w_I}$
($y^{-1}$은 I번째 규칙에 의한 출력의 평균치, $w_I$는 I번째 규칙의 적합도)

평균 중심법도 많이 사용되는 비퍼지화 방법이다.

<br>

- 최대치법(Maximum Method)
최대치법은 $y^*$를 출력 공간 V에서 $m_B(y)$값이 최대가 되는 점으로 잡는 방법이다. 

$m_{max}(B')=\{y\in V|m_{B'}(y)\sup_{y\in V} m_{B'}(y)\}$


최대치법 안에는 세가지 방법이 있다.


'smallest of maxima defuzzifer'는 $m_{max}(B')$에서 가장 작은 값을 취한다

$y^*=inf\{y\in m_{max}(B')\}$

<br>

'largest of maxima defuzzifier'는 $m_{max}(B')$ 에서 가장 큰 값을 출력값으로 정한다

$y^*=sup\{y\in m_{max}(B')\}$

<br>

'mean of maxima defuzzifier'는 $m_{max}(B')$의 평균값을 취하는 방법이다.

$y^* = \frac{\int_{m_{max}(B')}y dy}{\int_{m_{max}(B')dy}}$

최대치법은 계산량이 적어 유리하지만, 출력값의 연속성을 보장하지 못하는 결점이 있다.

<br>
<br>

**퍼지추론**

퍼지화를 통해 소속값으로 결과를 추론하는 과정, 퍼지 규칙을 통해 퍼지입 력으로 퍼지 결과를 추론하게됨
이때 Rule Base를 사용하게 되는데

- NB : Negative Big
- NM : Negative Medium
- NS : Negative Small
- ZO : Zero
- PS : Positive Small
- PM : Positive Medium
- PB : Positive Big
을 의미

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/123608178-7f92e180-d839-11eb-90fe-b781f98d521f.png" width = "500" ></p>



## 3. 적용

캡스톤에서는 옴니휠 모바일 로봇의 위치제어를 위해 사용하였습니다.
로봇을 특정 위치로 이동시키기 위해서 카메라를 통해 특정 위치와 현재 로봇의 오차값을 $x,y,\theta$ 값으로 가져와서 Fuzzy control의 input값으로 사용하였습니다.