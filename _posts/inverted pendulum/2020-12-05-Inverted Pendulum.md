---
title:  "Inverted Pendulum - 1.동역학 해석"
excerpt: "개인 프로젝트 - Inverted Pendulum"
use_math: true
categories:
  - Inverted Pendulum
---


## Inverted Pendulum의 동역학 해석

어떤 시스템에 대한 제어기를 설계할때 가장 먼저 해야하는 것이 시스템에 대한 동역학 해석이라고 생각한다.
<br>


<p align="center"><img src="https://user-images.githubusercontent.com/54671691/101979057-01a42a00-3c9d-11eb-9ee0-1ea1e60a963e.png" width = "400" ></p>

위의 사진과 같이 추는 달려있지 않는 하나의 pole과 cart가 있는 시스템이다.

|기호|뜻|값|
|-|-|-|
|M|카트의 질량|1kg|
|m|진자의 질량|0.3kg|
|l|진자의 질량 중심까지의 길이|30cm|
|b|카트의 마찰계수|0.5Kg/s|
|r|볼스크류 1회전당 이동거리|1.27cm|
|Km|모터 토크 상수|4.9 Ncm/A|
|Kb|모터 역기전력 상수|0.0507V/rad/s|
|R|모터 전기자 저항|$0.3 \Omega$ |

<br>

카트의 운동에 대한 방정식을 구하면 다음과 같다.

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/101978083-afabd600-3c95-11eb-89cf-660a538045b7.JPG" width = "600" ></p>

이때 $N$은 다음과 같다

<p align="center"><img src="https://user-images.githubusercontent.com/54671691/101979080-30ba9b80-3c9d-11eb-863d-9f6aac13bc9c.JPG" width = "600" ></p>
<br>

(1)식과 (2-3) 식을 연립
<p align="center"><img src="https://user-images.githubusercontent.com/54671691/101979086-3e702100-3c9d-11eb-8bb2-912d0a573aae.JPG" width = "600" ></p>
<br>

진자에 수직인 힘을 구하면 다음과 같다
<p align="center"><img src="https://user-images.githubusercontent.com/54671691/101979089-40d27b00-3c9d-11eb-917f-b707961d7087.JPG" width = "600" ></p>
<br>

진자의 회전운동에 관한 식은 다음과 같다
<p align="center"><img src="https://user-images.githubusercontent.com/54671691/101979090-416b1180-3c9d-11eb-973b-9ef7f4d8b35f.JPG" width = "600" ></p>
<br>

(5) 식을 (4) 식에 대입
<p align="center"><img src="https://user-images.githubusercontent.com/54671691/101979091-416b1180-3c9d-11eb-803e-7cafcdf7224c.JPG" width = "600" ></p>
<br>

비선형 시스템을 진자가 수식이 되는 즉 $ \theta = \pi + \phi$ 구간에서 선형화 시킵니다. (이 구간이 pole이 수직으로 서있을때 입니다.)
<p align="center"><img src="https://user-images.githubusercontent.com/54671691/101979140-a32b7b80-3c9d-11eb-9f1f-8a908023951e.JPG" width = "300" ></p>
<br>

(3)식과 (6)식을 선형화 시키면 다음 두 식을 얻을 수 있습니다.
<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102013732-4c08d200-3d95-11eb-8e5b-04d2bc34d789.JPG" width = "600" ></p>

<br>

식 (3-1)에서 $F$는 모터에서 발생되는 힘이며 이때 모터에서 밸생되는 토크 $T = \operatorname{K}_{m}i$ 이며

$F$에 대해서 나타내면 $F=2 \frac{\pi T}{r} = \frac{2\pi}{r}{K}_{m}i$ 과 같이 표현되며 이때 $r$은 모터가 한 바퀴 회전할 때 볼스크류가 이송되는 거리이다.

모터에 입력되는 전압과 전류의 관계는 $V=iR+\operatorname{K}_{b} \dot{\theta}$ 와 같다
이때 모터의 회전과 카트의 이동거리는 $\theta=\frac{2\pi}{r}x$ 와 같이 정리될 수 있다.

앞의 두 식을 연립하여 정리하면 
$V=iR+\frac{2\pi\operatorname{K}_{b}}{r}\dot{x}$ 와 같이 정리된다.

이를 $F$에 대해 정리하면 $F=\frac{2\pi}{r}\frac{\operatorname{K}_{m}}{R}(V-\frac{2\pi\operatorname{K}_{b}}{r}\dot{x})$ 가 된다.

<br>

식 (3-1)과 연립하면 다음 식을 얻을 수 있다.
<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102015474-339db500-3d9f-11eb-9728-6c21757c45aa.JPG" width = "600" ></p>


최종적으로 얻을 수 있는 수식은 다음과 같다.
<p align="center"><img src="https://user-images.githubusercontent.com/54671691/102015756-cab73c80-3da0-11eb-98e7-9b516cd7d94f.JPG" width = "600" ></p>

위와 같이 Inverted pendulum의 동역학 해석을 마쳤다.