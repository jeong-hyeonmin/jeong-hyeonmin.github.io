---
title:  "system indentification 5~6"
excerpt: "세번째"
use_math: true

categories:
  - control theory
---


---
### Least Square Parameter Estimation - Batch Process
이전에 구한 discrete time model에 대해서 error가 가장 낮은 모델을 선정한다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102491557-b7171900-40b3-11eb-9f43-550095b87eb0.JPG" width = "400" ></p>

즉 다음과 같은 식에서 error인 $e(kh)$ 가 가장 낮은 $a_1$~$a_n$ , $b_1$~$b_n$ 을 구한다.

식을 정리하면 다음과 같다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102492272-c8acf080-40b4-11eb-9ff0-bf25a1557787.JPG" width = "180" ></p>

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102492116-871c4580-40b4-11eb-820d-72adc4dc998e.JPG" width = "650" ></p>

이때 error의 제곱의 총합을 구하면 다음과 같다.
$V=\sum_{k=n+1}^N e^2(kh)$

<br>

linear model은 다시 다음과 같이 정리된다.


<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102493161-1d04a000-40b6-11eb-8c41-3858444f0666.JPG" width = "300" ></p>

따라서 다음과 같이 error가 최소가되는 $\theta$ 즉 $a_1$~$a_n$ , $b_1$~$b_n$ 를 구할 수 있다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102494375-e92a7a00-40b7-11eb-9a98-d9bd4f1c004c.jpg" width = "500" ></p>


---
### Least Square Parameter Estimation - Recursive Process

이전에는 모든 데이터를 모은 후에 계산하여 parameter를 얻어냈다면 Recursive Process는 시스템에서 추가되는 정보를 활용한다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102957102-ecd95900-451c-11eb-950f-d04d01ff15e6.JPG" width = "500" ></p>
N은 행의 갯수를 의미한다.

new measurement는 $y_+, \phi_+$ : row vector

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102957646-4a21da00-451e-11eb-9e03-5775f4e9e76e.JPG" width = "300" ></p>

$\theta^N$ 을 사용해서 $\theta^{N+1}$ 를 표현한다.

<br>
<br>


<p align=""><img src="https://user-images.githubusercontent.com/54671691/102957742-953bed00-451e-11eb-831d-b7a874ac322f.JPG" width = "500" ></p>

N+1로 표현하면 위와 같다.
<br>


<p align=""><img src="https://user-images.githubusercontent.com/54671691/102957863-e946d180-451e-11eb-9ed1-ec4d402888a0.JPG" width = "200" ></p>

$P_N$을 위와같이 정의하면 $\theta^N$은 다음과같이 표현된다.

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102957865-e9df6800-451e-11eb-9214-cd8a32fedba5.JPG" width = "300" ></p>

<br>


정리하면 다음과 같이 표현된다.
<p align=""><img src="https://user-images.githubusercontent.com/54671691/102958248-d5e83600-451f-11eb-8a3e-d5d11878792e.JPG" width = "300" ></p>

$\theta^{N+1}$ 은 이전 data와 값이 곱해진 error로 표현될 수 있다.

P의 inverse를 없애기 위해서 다음 식을 활용한다.

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102958505-60c93080-4520-11eb-8307-7112ec513b30.JPG" width = "400" ></p>

<p align=""><img src="https://user-images.githubusercontent.com/54671691/102958502-5f980380-4520-11eb-8979-3536b7305ae6.JPG" width = "400" ></p>

최종적으로 얻어지는 식은 다음과 같다.
<p align=""><img src="https://user-images.githubusercontent.com/54671691/102958618-ae459d80-4520-11eb-9ba6-ee16fff4b187.JPG" width = "300" ></p>


