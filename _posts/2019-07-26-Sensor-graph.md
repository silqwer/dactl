---
layout: post
title:  "Sensor graph"
tags:
  - panolens
  - WebVR
  - 360VR
hero: /../assets/resources/img/panolens/sensor/s3.jpg
overlay: orange
published: true

---
## 걷는 속도 그래프  
내가 일정하게 걸을때 속도가 어떻게 변하는지 알고 싶었다. 단순하게 숫자로 출력하면 너무 빠른 속도록 지나가기 때문에 읽을 수 없었다.  
{: .lead}
그래서 이 값들을 실시간으로 그래프로 그려주면 보기 편해서 테스트 하기 좋을 것 같다.
<!–-break-–>
실시간 그래프 라이브러리를 검색해서 smoothie.js 를 찾아서 적용시켜보았다.

## 적용
smoothie.js 는 적용하기가 매우 간편했다.  딱 내가 원하는 수준으로 깔끔하게 지원하고 있었다.
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//그래프</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">var</span>&nbsp;smoothie1&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">new</span>&nbsp;SmoothieChart();</div><div style="padding:0 6px; white-space:pre; line-height:130%">smoothie1.streamTo(<span style="color:#4be6fa">document</span>.<span style="color:#4be6fa">getElementById</span>(<span style="color:#ffd500">"mycanvas1"</span>));</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">var</span>&nbsp;line1&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">new</span>&nbsp;TimeSeries();</div><div style="padding:0 6px; white-space:pre; line-height:130%">smoothie1.addTimeSeries&nbsp;(line1);&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">var</span>&nbsp;smoothie2&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">new</span>&nbsp;SmoothieChart();</div><div style="padding:0 6px; white-space:pre; line-height:130%">smoothie2.streamTo(<span style="color:#4be6fa">document</span>.<span style="color:#4be6fa">getElementById</span>(<span style="color:#ffd500">"mycanvas2"</span>));</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">var</span>&nbsp;line2&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">new</span>&nbsp;TimeSeries();</div><div style="padding:0 6px; white-space:pre; line-height:130%">smoothie2.addTimeSeries&nbsp;(line2);&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">var</span>&nbsp;smoothie3&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">new</span>&nbsp;SmoothieChart();</div><div style="padding:0 6px; white-space:pre; line-height:130%">smoothie3.streamTo(<span style="color:#4be6fa">document</span>.<span style="color:#4be6fa">getElementById</span>(<span style="color:#ffd500">"mycanvas3"</span>));</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">var</span>&nbsp;line3&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">new</span>&nbsp;TimeSeries();</div><div style="padding:0 6px; white-space:pre; line-height:130%">smoothie3.addTimeSeries&nbsp;(line3);&nbsp;</div></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

각각의 그래프 객체를 만들고 body의 캔버스를 연결시켜준다. 선을 생성하고 그래프에 addTimeSeries 해준다. 그리고 센서값을 읽어오는 부분에 아래와 같이 적용하면 최종 결과물 처럼 실시간 그래프를 얻을 수 있다. 
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//그래프&nbsp;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">line1.append(<span style="color:#ff3399">new</span>&nbsp;<span style="color:#4be6fa">Date</span>().getTime(),&nbsp;laSensor.z);&nbsp;<span style="color:#999999">//&nbsp;앞뒤</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">line2.append(<span style="color:#ff3399">new</span>&nbsp;<span style="color:#4be6fa">Date</span>().getTime(),&nbsp;laSensor.y);&nbsp;<span style="color:#999999">//&nbsp;좌우</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">line3.append(<span style="color:#ff3399">new</span>&nbsp;<span style="color:#4be6fa">Date</span>().getTime(),&nbsp;laSensor.x);&nbsp;<span style="color:#999999">//&nbsp;상하</span></div></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

## 앞으로 걷기
<img src='/../assets/resources/img/panolens/sensor/앞으로걷기.gif' alt='앞으로걷기'>

## 뒤로 걷기
<img src='/../assets/resources/img/panolens/sensor/뒤로걷기.gif' alt='뒤로걷기'>

## 오른쪽으로 걷기
<img src='/../assets/resources/img/panolens/sensor/오른쪽으로 걷기.gif' alt='오른쪽으로걷기'>

## 왼쪽으로 걷기
<img src='/../assets/resources/img/panolens/sensor/왼쪽으로걷기.gif' alt='왼쪽으로걷기'>

## 앉았다 일어서기 
<img src='/../assets/resources/img/panolens/sensor/앉았다 일어서기.gif' alt='앉았다 일어서기'>