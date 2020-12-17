---
title:  "system indentification 5,6"
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
