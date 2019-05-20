---
layout: post
title:  "Aframe ipd  관련 자료 검토"
tags:
  - portfolio
hero: /../assets/resources/img/flag/main/3.메인화면.png
overlay: blue
published: true

---
## 360VR
Aframe.js 에서 IPD 설정이 가능한지 여부를 확인이 필요했다. 우선 IPD가 무엇인지 알아보자.

## IPD
IPD: Inter pupillary distance, <a href='https://search.naver.com/search.naver?sm=top_hty&fbm=1&ie=utf8&query=Interpupillary+distance'>동공 거리</a>

양쪽 눈의 동공 중심을 잇는 선의 거리.
사람에 따라 다소 차이는 있으나 대개 65mm이다.
<a href='https://search.naver.com/search.naver?sm=top_hty&fbm=1&ie=utf8&query=Interpupillary+distance'>[네이버지식백과]</a> 그런데 사람에 따라 동공사이의 거리가 조금씩 다르고 화면을 VR모드로 변경해서 카드보드를 쓰면 초점이 맞지 않을 수 있다.

그래서 VR기기에서 물리적 IPD의 거리를 조절할 수 있게 지원을 하거나 KRPANO처럼 소프트웨어에서 조절을 할 수 있도록 지원한다.

우선 aframe-marster.js 에서 IPD가 언급되는 부분이 있는지 검색을 했다.
setProjectionFromUnion에서 IPD가 선언된다.
![1200x700](/../assets/resources/img/aframe/ipd.png "aframe ipd"){:.oversize}

