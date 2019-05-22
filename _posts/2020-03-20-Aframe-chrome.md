---
layout: post
title:  "Aframe broken in Chrome"
tags:
  - Aframe.js
  - WebVR
  - 360VR
hero: /../assets/resources/img/aframe/chrome/error.png
overlay: red
published: true

---
## Aframe.js가 동작을 하지 않는다.
{: .lead}
어제까지만 해도 잘 동작하던 코드들이 크롬에서 동작하지 않는다. 콘솔 로그를 보니 이상한 에러가 똮! 갑자기?  
<!–-break-–>

## 추적
<img src='/../assets/resources/img/aframe/chrome/error.png' alt='error'>에러를 보면 장비와 관련해서 오류가 나는 것 같은데... 달라긴 것은 Chrome을 버전업 해서 m73이라는 것 혹시나 하고 깃헙으로 달려갔다. 
<a href='https://github.com/immersive-web/webxr-samples/issues/35'>https://github.com/immersive-web/webxr-samples/issues/35</a>
<img src='/../assets/resources/img/aframe/chrome/m73.png' alt='m73'>
m73으로 크롬이 업데이트 되면서 사양이 변경됐고 구현간 불일치가 있어서 오류가 난다는 내용이었다. 

## WebXR
<img src='/../assets/resources/img/aframe/chrome/webxr.png' alt='webxr'>
WebXR API가 Chrome에서 변경을 한것 같다는 내용이다. 몇년 전까지만 해도 WebXR 이라는 개념은 없었다. w3에서 이 개념을 정립하면서 PC는 WebXR Device 범주에 미포함된것 같다.
<a href='https://immersive-web.github.io/webxr/#xr-device-concept'><img src='/../assets/resources/img/aframe/chrome/w3.png' alt='w3'></a>
그래서 PC에서 실행할 때 장치로 인식 못하고 오류가 나는 것 같다.

## 결론
그럼 크롬의 버전을 낮춰서 개발을 하거나 w3에서 스팩을 변경되기를 기다리거나 aframe.io의 기여자들이 문제를 해결해 빌드를 하기를 기다려야한다. 아니면 예전 버전(WebXR 개념이 도입되기 전 버전)의 Aframe을 사용해서 개발을 해야한다.


