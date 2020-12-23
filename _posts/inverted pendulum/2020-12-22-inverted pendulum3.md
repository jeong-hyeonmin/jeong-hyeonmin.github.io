---
title:  "Inverted Pendulum - 3.Swing up"
excerpt: "개인 프로젝트 - Inverted Pendulum"
use_math: true
categories:
  - Inverted Pendulum
---


## Swing up
swing up은 모터를 적절히 가속하여 진자가 가장 낮은 위치에서 적절히 선형제어가 가능한 위치에 위치시키는 것을 말한다.
swing up에 사용할 제어는 Wiklund et al에 의해 제안된 Energy control에 의한 Swing up control 방식이다. 이 방식은 system의 불확실성과 잡음의 영향에 효과적이고 강력하다고 알려져 있다.

<br>


또한 Yusuke Otani에 의해 제안된 새로운 Lyapunov function을 사용하여 진자의 총 에너지를 감소시키는 방향으로 진자를 가속시키는 방식을 사용하였다. 진자의 총 에너지는 아래로 늘어뜨려져 있을 때 최대가 되며 수직에 위치하면 최소가 된다.

<br>

Lyapunov function은 기계적 총 에너지와 카트의 속도와 위치의 제곱의 함인 두 부분으로 구성되며 기계적 총 에너지는 다음과 같다.
$E_p=\frac{1}{2}I\dot{\theta}^2+mgl(cos\theta -1)$
에너지의 절대 값은 최하점 일 때 가장 크고 최상위점일 때 가장 작다.

<br>

카트의 속도와 위치의 제곱의 합은 다음과 같다.
$F_c=wml(x^2+\dot{x}^2)$ 이떄 $w$는 비례상수이며 0보다 크다.

Lyapunov function은 다음과 같다.
$V=\frac{1}{2}(\left\vert E_p \right\vert+F_c^2)$

최상위점을 제외하고는 항상 양의 값을 가지게 된다. 진자가 수직일 때 에너지가 최소가 되기 때문에 이 함수의 도함수가 항상 음의 값을 가지도록 제어해야 한다.

<br>

도함수는 다음과 같다.
$\dot{V}=-ml(\left\vert E_p \right\vert+F_c^2)[ (sgn(E_p)\dot{\theta}cos\theta - 2wx\dot{x})\ddot{x}-2wx\dot{x}]$
sgn은 부호를 의미한다.

<br>

도함수를 항상 음의 값으로 만드는 제어 입력은 다음과 같다.
<p align=""><img src="https://user-images.githubusercontent.com/54671691/102842576-a0254d80-444a-11eb-8335-e1b015d7088f.JPG" width = "350" ></p>

이때 $u_a$는 임의의 비례상수이다.

분모가 0이 되는 경우만 제외하면 도함수는 항상 음의 값을 가진다.
분모가 0이 되는 경우는 매우 짧은 순간이므로 무시할 수 있지만 연산을 고려하여 미소치  을 이용하여 재정의한다.

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102842666-d531a000-444a-11eb-86c6-252cf93086a4.JPG" width = "600" ></p>

<br>

앞에서 F와 모터에 입력되는 전압 $V_a$ 와의 관계는 다음과 같다.

<p align="left"><img src="https://user-images.githubusercontent.com/54671691/102082236-ef6cec00-3e54-11eb-902b-a1834a2a8cac.JPG" width = "200" ></p>

시스템의 모멘트에 관한 비선형 운동방정식은 다음과 같다.
$cos\theta\ddot{x}+l\ddot{\theta}=gsin\theta$ 이며 카트를 가속시켜 진자를 swing시키므로 $\ddot{x}=u$ 이므로 식은 $\ddot{\theta}=\frac{g}{l}sin\theta - \frac{cos\theta}{l}u$ 와 같이 표현할 수 있다.

<br>

위의 두 개의 식과 $\ddot{x}=u$ 를 위에서 구한 시스템의 비선형 운동방정식인 
$(M+m)\ddot{x}+ml\ddot{\theta}cos\theta - ml\dot{\theta}^2sin{\theta}=F-b\dot{x}$ 
에 대입하면 다음과 같은 식을 구할 수 있다.

<p align="left"><img src="https://user-images.githubusercontent.com/54671691/102844149-20997d80-444e-11eb-9ad5-1f7d51d40f6c.JPG" width = "500" ></p>

여기서 $F_v , F_r$은 앞에서 구한 값들이다.

$G = 1 \quad when \quad Z < 0.4$

$G = 0.21 \quad when  \quad Z \ge 0.4$

Z는 swing을 시작해서 현재까지의 각에 대한 cos값의 최대 값을 의미한다. 다시 말해 이 값이 0.4를 넘어서는 순간부터, 한번 이상 최상위점 근처의 특정각 이상으로 진자가 도달하게 되면 G값은 0.21가 돼서 진자를 가속하는 제어신호가 원래 신호의 21%만 적용되어 안정적으로 선형영역으로 진입하게 된다. (아래 그림 참고)

<br>
<br>


<p align="left"><img src="https://user-images.githubusercontent.com/54671691/102844479-e11f6100-444e-11eb-9ff2-8b44ddf06809.png" width = "500" ></p>

<br>

---
#### Reference

- Yusuke Otani, Takuya Kurokami, Akira Inoue and Yoichi Hirashima (2001) A SWINGUP CONTROL OF AN INVERTED PENDULUM WITH CART POSITION CONTROL

---
#### series
1.[동역학해석](https://jeong-hyeonmin.github.io/inverted%20pendulum/Inverted-Pendulum/)

2.[Stabilizing](https://jeong-hyeonmin.github.io/inverted%20pendulum/inverted-pendulum2/)

3.[Swingup](https://jeong-hyeonmin.github.io/inverted%20pendulum/inverted-pendulum3/)
