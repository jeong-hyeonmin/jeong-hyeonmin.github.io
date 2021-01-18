---
title:  "State Space Design 1~2"
excerpt: "다섯번째"
use_math: true

categories:
  - control theory
---

### Introduce

<br>

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/103454958-1881ed80-4d2c-11eb-96e2-ca147e5ca8dc.JPG" width = "400" ></p>

다음과 같이 Fedd back control은 이전의 전달함수를 사용하여 구하는 것과 마찬가지로 사용한다.

출력을 Feedback받아서 error를 만들고 제어기를 설계하는 방식과 다르게 상태방정식은 시스템의 내부변수를 가지고 제어한다.

상태방정식은 처음부터 시간영역에서 설계되어진다.

SISO system부터 MIMO system까지 표현할 수 있으며 전달함수보다 상대적으로 상태방정식이 명확해 보인다.

---

### System Description in State space

<br>

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/103455012-b4135e00-4d2c-11eb-873c-5d1e355a8268.JPG" width = "500" ></p>

다음과 같이 상태공간을 표현하며 고차의 방정식 혹은 시스템의 운동방정식이 있다면 변수를 잘 정해서 연립 1차 방정식으로 표현하는 것을 상태공간에서 표현했다라고 한다.

<br>

State : 시스템의 현재상황을 완벽하게 기술할 수 있는 최소한의 정보의 양

Note : 어떤 시점에서 시스템의 상태값을 알고, 입력을 항상 안다면 이 시스템의 거동을 완벽히 알 수 있다.

Examples of state : position, velocity, current, voltage , etc
"position + velocity" 도 상태변수가 될 수 있다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/103455182-25074580-4d2e-11eb-9e14-ae80601d7005.JPG" width = "200" ></p>

위와 같은 시스템이 있을 때 전달함수와 상태공간에서의 표현은 다음과 같다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/103455275-24bb7a00-4d2f-11eb-8bbf-069c6c290158.jpg" width = "500" ></p>

F : system matrix (nxn)
G : input matrix (nx1)
H : output matrix (1xn)
J : direct transmission term


또 다른 경우를 생각해보자.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/103456290-0017d000-4d38-11eb-87fb-7ce73ead19db.JPG" width = "500" ></p>

다음과 같은 경우를 상태공간에서 표현하면 다음과 같다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/103456419-71a44e00-4d39-11eb-867e-8f692ac3fd87.jpg" width = "400" ></p>


---
### Block Diagrams and State Space
analog 회로의 적분기와 block diagram을 사용하여 미분방정식을 상태공간표현법으로 사용한다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/103456457-df507a00-4d39-11eb-80a6-1bde672c6cce.JPG" width = "500" ></p>

아래 예제를 상태공간으로 표현하면 다음과 같다.


<p align="center"><img src="https://user-images.githubusercontent.com/54671691/103456481-36eee580-4d3a-11eb-8ae3-2bb3ef0b6b32.JPG" width = "500" ></p>

