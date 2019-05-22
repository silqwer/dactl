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
<div class="colorscripter-code" style="color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important; overflow:auto"><table class="colorscripter-code-table" style="margin:0; padding:0; border:none; background-color:#272727; border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px; border-right:2px solid #4f4f4f"><div style="margin:0; padding:0; word-break:normal; text-align:right; color:#aaa; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div></div></td><td style="padding:6px 0"><div style="margin:0; padding:0; color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%">Uncaught&nbsp;TypeError:&nbsp;<span style="color:#4be6fa">navigator</span>.xr.requestDevice&nbsp;is&nbsp;not&nbsp;a&nbsp;<span style="color:#ff3399">function</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;at&nbsp;<span style="color:#4be6fa">Object</span>.<span style="color:#0086b3"></span><span style="color:#ff3399">&lt;</span>anonymous<span style="color:#0086b3"></span><span style="color:#ff3399">&gt;</span>&nbsp;(aframe<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>master.min.js:<span style="color:#c10aff">396</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;at&nbsp;<span style="color:#4be6fa">Object</span>.<span style="color:#c10aff">173.</span>_process&nbsp;(aframe<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>master.min.js:<span style="color:#c10aff">397</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;at&nbsp;s&nbsp;(aframe<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>master.min.js:<span style="color:#c10aff">1</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;at&nbsp;aframe<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>master.min.js:<span style="color:#c10aff">1</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;at&nbsp;<span style="color:#4be6fa">Object</span>.<span style="color:#c10aff">176.</span>.<span style="color:#0086b3"></span><span style="color:#ff3399">/</span>bind&nbsp;(aframe<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>master.min.js:<span style="color:#c10aff">404</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;at&nbsp;s&nbsp;(aframe<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>master.min.js:<span style="color:#c10aff">1</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;at&nbsp;aframe<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>master.min.js:<span style="color:#c10aff">1</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;at&nbsp;<span style="color:#4be6fa">Object</span>.<span style="color:#c10aff">149.</span>..<span style="color:#0086b3"></span><span style="color:#ff3399">/</span>package&nbsp;(aframe<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>master.min.js:<span style="color:#c10aff">341</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;at&nbsp;s&nbsp;(aframe<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>master.min.js:<span style="color:#c10aff">1</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;at&nbsp;e&nbsp;(aframe<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>master.min.js:<span style="color:#c10aff">1</span>)</div></div><div style="text-align:right; margin-top:-13px; margin-right:5px; font-size:9px; font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4f; text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom; padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none; color:white"><span style="font-size:9px; word-break:normal; background-color:#4f4f4f; color:white; border-radius:10px; padding:1px">cs</span></a></td></tr></table></div>
에러를 보면 장비와 관련해서 오류가 나는 것 같은데... 달라긴 것은 Chrome을 버전업 해서 m73이라는 것 혹시나 하고 깃헙으로 달려갔다. 
<a href='https://github.com/immersive-web/webxr-samples/issues/35'>https://github.com/immersive-web/webxr-samples/issues/35</a>
<img src='/../assets/resources/img/aframe/chrome/m73.png' alt='m73'>

<img src='/../assets/resources/img/aframe/chrome/forChrome.png' alt='forChrome'>
m73으로 크롬이 업데이트 되면서 사양이 변경됐고 구현간 불일치가 있어서 오류가 난다는 내용이었다. 

## WebXR
WebXR API가 Chrome에서 변경을 한것 같다는 내용이다. 몇년 전까지만 해도 WebXR 이라는 개념은 없었다. w3에서 이 개념을 정립하면서 PC는 WebXR Device 범주에 미포함된것 같다.
<a href='https://immersive-web.github.io/webxr/#xr-device-concept'><img src='/../assets/resources/img/aframe/chrome/w3.png' alt='w3'></a>
그래서 PC에서 실행할 때 장치로 인식 못하고 오류가 나는 것 같다.

## 결론
그럼 크롬의 버전을 낮춰서 개발을 하거나 w3에서 스팩을 변경되기를 기다리거나 aframe.io의 기여자들이 문제를 해결해 빌드를 하기를 기다려야한다. 아니면 예전 버전(WebXR 개념이 도입되기 전 버전)의 Aframe을 사용해서 개발을 해야한다.


