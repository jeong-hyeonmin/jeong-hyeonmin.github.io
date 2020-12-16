---
title:  "system indentification 3~4"
excerpt: "두번째"
use_math: true

categories:
  - control theory
---

---
## Three-parameter Models
Three-parameter Models는 Two-parameter Models와 사용하는 이유는 같다. 주어진 시스템의 전달함수를 모를때 step response를 보고 전달함수를
구하기위해서 사용하며 다음과 같다.

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102360211-119d7000-3ff5-11eb-9246-f55ee9e8c60e.JPG" width = "200" ></p>

K : static gain
T : time constant
L : dead time $T = T_{ar}-L$

Step Response
$y(t) = \mathcal{L}^{-1} \left \{ \frac{k}{s(sT+1)}e^{-sL} \right \} \quad=K(1-e^{-\frac{1}{T}(t-L)}) 1 (t-L)$

- Average residence time = $T = A_{0}/K = L+T$
- Normalized dead time $\tau = \frac{L}{(L+T)}=\frac{L}{T_{ar}}$
여기서 $L$이 작다는 것은 delay가 적고 이는 제어하기 쉽다는 것을 의미한다.

다음은 시스템 $G(s)$를 보여준다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102363255-98a01780-3ff8-11eb-804e-4e9a5e7d5fe0.JPG" width = "600" ></p>


damping이 있는 모델에서의 three-parameter model은 다음과 같다.
<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102363791-1bc16d80-3ff9-11eb-9194-6e8cd0076470.JPG" width = "600" ></p>

- $T_p$ : peak간의 거리
- $d$ : 가장큰 peak와 다음 peak의 비

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102364402-bd48bf00-3ff9-11eb-8a60-30eec2f13570.JPG" width = "200" ></p>


위에서 했던 방식들은 노이즈가 없다고 가정하고 했지만 실제로는 노이즈에 예민하다.
앞으로 소개할 내용은 measurement noise에 덜 취약한 방법들이다.

적분은 measurement noise에 효과적인 방법이다.

---
## Parameter Estimation- Concept
이전의 방법은 step입력을 주고 출력을 통해 system의 model을 선정했다면 앞으로는 여러 입력과 출력을 가지고 system의 model을 구하는 법을 배운다.

**Data fittin**
얻은 데이터를 가장 잘 표현하는 함수를 만들때 parameter를 선정하는 방법을 말한다.
<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102365083-86bf7400-3ffa-11eb-8d04-0641c8209bdf.JPG" width = "300" ></p>

다음과 같은 데이터가 주어졌을때 우리는 함수를 $y=ax+e$ 와 같이 표현할 수 있다. 이때 $e$ 는 error 혹은 noise를 의미한다.

error의 총합을 더해서 제일 오차가 적은 함수로 표현할 수 있겠지만 분산의 의미를 생각하여 error의 제곱을 총합하여 오차가 가장 적은 함수로 표현한다.

$E=\sum_{i=1}^N (y_i - ax_i)^2$ 일때 error가 가장 적은 a를 구하기 위해서 미분해서 0이되는 a값을 구한다.

$\frac{dE}{da}=0$ &nbsp; &nbsp; &nbsp; => $a=\frac{\sum y_i x_i}{\sum x_i ^2}$  

또 다른 예시로 $y=ax+b$ 일때는 $y_i = ax_i +b+e_i$ 를 가지고 a,b를 구한다.
<p align=""><img src="https://user-images.githubusercontent.com/54671691/102366836-73150d00-3ffc-11eb-8de5-e9ffdba6fe5b.JPG" width = "200" ></p>
<p align=""><img src="https://user-images.githubusercontent.com/54671691/102366995-9b047080-3ffc-11eb-97e6-8681e6ab70ea.JPG" width = "300" ></p>

---

지금까지는 간단한 시스템에 대하여 step입력과 출력을 가지고 model을 선정했다면 좀 더 일반화된 입력을 통해서 구하는 방법을 알아본다.

Q : 앞에서 구한 model도 변수는 3가지 정도밖에 없었는데 3점을 가지고 변수들을 구하면 안되나요?

A:측정데이터에 error가 섞이기 때문에 많은 데이터를 모아 error가 최소화 되도록 구하는 것이 좋다.

<br>

### Descrete Time parametric Models

제어를 위해서 Digital computer를 많이 사용하기때문에 Input/output의 데이터는 이산화 되어있다.

시스템의 모델이 $G(s) = \frac{K}{1+sT}e^{-sT}$ 와 같다고 가정하면 출력은 다음과 같다.

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102368129-dce1e680-3ffd-11eb-916a-a278f09c668b.JPG" width = "400" ></p>

출력인 이전 출력에 a를 곱한것과 그때의 입력에 $b_1$, 그 이전의 입력에 $b_2$를 곱한것을 더해서 얻을 수 있다.

<br>

$a,b_1,b_2$ 는 다음과 같다.
<p align=""><img src="https://user-images.githubusercontent.com/54671691/102368797-993bac80-3ffe-11eb-9216-b58c4a39b6b7.JPG" width = "400" ></p>
