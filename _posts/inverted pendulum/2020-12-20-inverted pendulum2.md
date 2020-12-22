---
title:  "Inverted Pendulum - 2.Stabilizing"
excerpt: "개인 프로젝트 - Inverted Pendulum"
use_math: true
categories:
  - Inverted Pendulum
---

## Stabilizing

pole이 균형을 잃지않고 수직을 유지하는것을 stabilizing이라고 하고 이를 위해서는 pole의 움직임에 따라 모터에 적절한 전압을 가해 카트를 움직여줘야한다.

전에 구한 두 식을 다시 표현하면 다음과 같다.

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102706918-7698e480-42d9-11eb-9df5-9571de22c442.JPG" width = "300" ></p>

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102706933-a0520b80-42d9-11eb-9d73-b78c7c033c03.JPG" width = "500" ></p>

식을 간단하 하기 위해 $\alpha$를 사용한다.
$\alpha = (M+m)(I+ml^2)-m^2l^2$

---

### 상태공간 표현

위 방정식들은 선형이기 때문에 아래와 같이 나타낼 수 있다.

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102707046-b9a78780-42da-11eb-9337-e09787ea1207.JPG" width = "600" ></p>

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102707067-04c19a80-42db-11eb-8c00-aeeb206cffb9.JPG" width = "180" ></p>

$\dot{X}=AX+BU$
$Y=CX+DU$
와 같이 일반적인 선형 시스템의 동적 방정식을 구했다.

<br>

#### 가제어성

동적 방정식으로 제어기를 설계하기 전에 가제어성을 먼저 확인한다.
시스템의 특정상 모든 상테를 제어하는 것이 불가능 할 수 있기 때문에 제어를 하기 전에 먼저 제어 간능한 시스템인지 확인할 필요가 있다.
유한한 시간동안 입력을 가하여 한 임의의 상태를 다른 임의의 상태로 바꿀 수 있다면 제어가능하다고 하며 시스템이 가제어성(controllability)을 갖는다고 말한다.

가제어성 행렬이 4X4 이므로 가제어성 행렬의 rank가 4이면 가제어성을 갖는다.
가제어성 행렬은 아래와 같으며 MATLAB을 사용하여 구한다.
$M=[B \quad AB \quad A^2B \quad...\quad A^{n-1}B]$

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102707178-0dff3700-42dc-11eb-9b62-a67ad1651c72.JPG" width = "500" ></p>

다음과 같이 rank가 4인 것을 확인할 수 있고 이는 가제어성을 갖는 것을 보여준다.

<br>

#### 상태방정식과 성능지표

일반적인 선형시스템 의 상태방정식은 다음과 같다.

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102707221-777f4580-42dc-11eb-9aee-da08d8531432.JPG" width = "200" ></p>

이때 $U=-KX=-(k_{p1}x +k_{d1}\dot{x} +k_{p2}\phi +k_{d2}x\dot{\phi})$ 이며 여기서 $k_{p1}, k_{d1}$ 은 각각 카트의 위치와 속도에 대한 제어상수이며 $k_{p2}, k_{d2}$ 는 각각 진자의 각도와 각속도에 대한 제어상수이다.

<br>

성능지표 $J=\int\limits_{0}^{\infty}(X^TX)dt$ 이며 벡터 X의 제곱의 합으로 표현한 것이며 성능지표가 최소화 되어야 한다.
$\frac{d}{dt}(X^TPX)=-X^TX$
일반적인 시스템에서 위 수식을 만족하면 stable하다고 볼 수 있고 성립하는 행렬 P를 찾아야 한다.

<br>

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102707964-cc25bf00-42e2-11eb-8b7a-eb12b74d203c.JPG" width = "300" ></p>

이 식을 정리하면
$H^TP+PH=-I$ 가 되며 이를 만족하는 P와 H를 찾아야 한다.

앞에서 구했던 성능지표에 대입하여 풀면

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102708000-1018c400-42e3-11eb-924a-dec5c35d52e1.JPG" width = "450" ></p>

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102708017-2b83cf00-42e3-11eb-853c-53bccf9bf911.JPG" width = "200" ></p>

아래 두 식을 만족하는 P와 H를 찾으면 제어 게인 K를 찾을 수 있다.


<p align=""><img src="https://user-images.githubusercontent.com/54671691/102708026-49513400-42e3-11eb-989f-aac11c6f1135.JPG" width = "150" ></p>

<br>

좀 더 나아가 일반적으로 성능 지표는 각 상태에 가중치를 줄 수 있고, 제어입력의 크기에 대해서도 가중치를 설정할 수 있도록 다음과 같이 사용한다.

$J= \int\limits_{0}^{\infty}(X^TQX+U^TRU)dt$



---

### MATLAB으로 LQR게인 구하기

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102707046-b9a78780-42da-11eb-9337-e09787ea1207.JPG" width = "600" ></p>

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102707067-04c19a80-42db-11eb-8c00-aeeb206cffb9.JPG" width = "180" ></p>

위에서 구한 상태방정식을 아래와 같은 표현으로 바꿔주기위해 A,B,C,D를 매트랩에서 표현한다.

$\dot{X}=AX+BU$
$Y=CX+DU$

<br>


<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102708323-81f20d00-42e5-11eb-8de6-164a0b2443ae.JPG" width = "400" ></p>

<br>
<br>

위와 같이 매트렙에서 설정하고 lqr툴박스를 통해 게인값 k를 얻을 수 있다.

<br>


<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102708478-cd58eb00-42e6-11eb-92e7-43a44bd693f7.JPG" width = "300" ></p>

Q(1,1) 과 (3,3)은 각각 이동거리와 기울기에 대한 가중치이며 최적의 값을 찾기 위해 try and error방식으로 Q의 가중치 값을 정한다. 이때 R값은 클수록 시스템이 안정적이나 반응속도가 느려지는 점을 고려하여 R은 낮은 값으로 고정하고 Q의 값을 조절하였다.



---
### MATLAB/Simulink



<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102710391-40695e00-42f5-11eb-8149-fbaa5f7e6af7.JPG" width = "500" ></p>

<br>

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102710418-760e4700-42f5-11eb-91b9-0268baa6a543.JPG" width = "500" ></p>

위와 같은 제어기를 만들었고 simulink를 실행시켜 cart의 x축 이동, 진자의 기울기와 voltage를 확인한다.
