---
title:  "system indentification 1~2"
excerpt: "첫번째"
use_math: true

categories:
  - control theory
---

---
## Introduction

제어기를 만들게 될때 우리는 시스템을 완벽하게 알기란 쉽지 않은 일이다. 시스템이 linear한지 혹은 nonlinear한지, system order, system parameters또한 모를 수 있다.

그래서 controller parameter를 tunning하기 위해서는 시행착오법 즉 trial and error 를 만족할때 까지 쓰거나 수학적인 모델을 사용한다.
<br>

---
## System Models

- Static models
정상상태에서의 거동을 모아서 확인한다.

    - 입력과 출력의 범위를 구하는데 중요함
    - sensor resolution 을 선택하는데 중요함
    - Open-loop experiments 와 Closed-loop experiments를 통해 구할 수 있음

<br>

- Dynamic models
입력과 출력의 관계에서 과도응답과 정상상태까지 전부 고려한다.
    - LTI 을 주로 사용할 것이며 비선형시스템이여도 작동점 부근에서 선형화하여 사용할 수 있다.


---
## Step Response Methods
시스템의 전달함수의 실제 계수를 아는 경우가 많지 않다.
Step Response Methods는 step response를 가지고 전달함수의 계수를 찾는 방법을 말한다.

이번 학기에는 zero initial condition을 가지고 측정 noise가 없다고 생각하고 진행한다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102011939-c6802480-3d8a-11eb-848e-ccade32edf81.jpg" width = "600" ></p>

위 사진처럼 다양한 step response를 볼 수 있다.

---
###Two-Parameter Models

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102012069-a9982100-3d8b-11eb-902d-18db9f1cc606.jpg" width = "400" ></p>

다음을 근사하기 위하여 두가지 Model을 사용한다.

- $\operatorname{G}_{2a}$
<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102012167-2925f000-3d8c-11eb-9150-189a5c281a5a.jpg" width = "400" ></p>

<br>

- $\operatorname{G}_{2b}$
<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102012438-a4d46c80-3d8d-11eb-8437-5b55a16e675a.JPG" width = "200" ></p>

각각의 모델은 장단점을 가진다.

아래 사진과 같이 $\operatorname{G}_{2a}$ 은 t가클때 frequency가 낮을때 잘 근사화 하고 
$\operatorname{G}_{2b}$ 은 t가 작을때 frequency가 클때 근사화를 잘 시킨다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102012457-e107cd00-3d8d-11eb-97ab-47ece69100bf.JPG" width = "600" ></p>
