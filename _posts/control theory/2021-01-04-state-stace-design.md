---
title:  "State Space Design 3~4"
excerpt: "여섯번째"
use_math: true

categories:
  - control theory
---

### Block Diagrams and Canonical Forms

전달함수 $G(s)$ 를 상태공간에 표현하는 방법에는 크게 두가지 방법이 있다.
- Control canonical form
- Modal canonical form

다음 예제를 가지고 두가지 방법을 알아보도록 하자.

$G(s) = \frac{s+2}{s^2+7s+12}$

---
#### Control canonical form
block diagram을 그리면 다음과 같다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/103510605-e944bb00-4ea8-11eb-8280-2a7a4bc833d5.JPG" width = "400" ></p>

block diagram을 그리기 위해서는 
$G(s) = \frac{s+2}{s^2+7s+12} = \frac{\xi(s)}{U(s)}\frac{Y(s)}{\xi(s)}$
로 생각하고 먼저 $\frac{\xi(s)}{U(s)} = \frac{1}{s^2+7s+12}$ 을 먼저 그린다.


여기서는 x2 신호가 $\xi$ 가 되고 x1신호가 $S\xi(s)$ 가 되어서 분자부분을 구현할 수 있다.

상태공간으로 표현하면 다음과 같다.

<p align=""><img src="https://user-images.githubusercontent.com/54671691/103511415-5efd5680-4eaa-11eb-98db-e968d7cbbe6f.JPG" width = "300" ></p>
<p align=""><img src="https://user-images.githubusercontent.com/54671691/103511545-9b30b700-4eaa-11eb-85a7-fbfe9400ceb5.JPG" width = "500" ></p>

이때 system matrix, Ac의 행을 보면 -7과 -12가 전달함수의 분모에 부호만 바뀌어 있는 것을 확인 할 수 있다.

또한 output matrix, Cc를 보면 전달함수의 분모에 있는것을 알 수 있다.
$G(s)$는 다음과 같이 유도된다.
<p align=""><img src="https://user-images.githubusercontent.com/54671691/103513730-822a0500-4eae-11eb-8334-afe09a73412f.jpg" width = "300" ></p>

<br>
<br>

3차식에서는 다음과 같다.

<p align=""><img src="https://user-images.githubusercontent.com/54671691/103517205-1e570a80-4eb5-11eb-8655-490cbcab04ac.JPG" width = "550" ></p>

일반적인 식으로 표현하면 다음과 같다.

<p align=""><img src="https://user-images.githubusercontent.com/54671691/103517459-7e4db100-4eb5-11eb-8c5f-98b37e061057.JPG" width = "550" ></p>

전달함수의 분자와 분모의 값들이 $A_c, C_c$에 나타난다.

---
### Modal canonical form
<p align=""><img src="https://user-images.githubusercontent.com/54671691/103517737-f7e59f00-4eb5-11eb-8604-7f09f19835e2.JPG" width = "550" ></p>

이때 system matrix의 값 -4,-3은 pole과 관련있다는 것을 알 수 있다.
modal canonical form 은 pole을 가지고 표현한다고 생각가능하다.

---
### Transform

<p align=""><img src="https://user-images.githubusercontent.com/54671691/103518065-75a9aa80-4eb6-11eb-92d5-c1e15f0af94f.JPG" width = "550" ></p>

$\dot{x}=T\dot{z}=T[ AZ+Bu ]=TAT^{-1}+TBu$

---
### Transformation into control canonical form

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/103518459-22842780-4eb7-11eb-859f-e6280523b2b6.JPG" width = "600" ></p>

$A = T^{-1}FT 를  AT^{-1}=T^{-1}F$ 처렴 사용하는 이유는 $T^{-1}$에 대해서만 생각하기위해 다음과 같이 사용한다.





