---
layout: post
title:  "Panolens fullscreen"
tags:
  - panolens
  - WebVR
  - 360VR
hero: /../assets/resources/img/panolens/widget/w1.png
overlay: blue
published: true

---
## 크롬에서 전체화면이 안돼요.
역시 테스트 서버에서 기능을 테스트하고 받은 내용이다. 크롬에서 전체화면 버튼을 누르면 F11처럼 전체화면이 되었다가 1~2초 후에 다시 풀린다는 내용이다. 
{: .lead}
자리에서 테스트를 해보니 정말로 1~2초 후에 전체화면이 풀렸다. 
<!–-break-–>
<img src='/../assets/resources/img/panolens/widget/w1.gif' alt='w1'>
바로 검색을 해보니까 다양한 이유로 전체화면이 안될 수 있다는 것을 알았다. 사용자의 크롬 설정에 따라서 전체화면이 동작하지 않을 수 있다는 것인데. 이것은 서버에서 처리할 수 없는 부분이었다.
관련링크: <a href='https://windowsreport.com/google-chromes-full-screen-option-doesnt-fill-screen-fix/'>https://windowsreport.com/google-chromes-full-screen-option-doesnt-fill-screen-fix/</a>

## 그럼 전체화면 어떻게?
"이런 이유 때문에 전체화면은 저희가 처리 못해요." 라고만 하고 끝나면 아마 순식간에 역적으로 몰릴 것이다. 그럼 어떻게 처리 할 것인가? 생각해보면 전체화면을 처리하는 부분이 있고 이 부분을 커스터마이징하면 된다. 먼저 Widget의 생성자를 따라가 봤다.
<div class="colorscripter-code" style="color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important; overflow:auto"><table class="colorscripter-code-table" style="margin:0; padding:0; border:none; background-color:#272727; border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px; border-right:2px solid #4f4f4f"><div style="margin:0; padding:0; word-break:normal; text-align:right; color:#aaa; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div><div style="line-height:130%">18</div><div style="line-height:130%">19</div><div style="line-height:130%">20</div><div style="line-height:130%">21</div><div style="line-height:130%">22</div><div style="line-height:130%">23</div><div style="line-height:130%">24</div><div style="line-height:130%">25</div><div style="line-height:130%">26</div><div style="line-height:130%">27</div><div style="line-height:130%">28</div><div style="line-height:130%">29</div><div style="line-height:130%">30</div></div></td><td style="padding:6px 0"><div style="margin:0; padding:0; color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">/**</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">&nbsp;*&nbsp;Widget&nbsp;for&nbsp;controls</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">&nbsp;*&nbsp;@constructor</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">&nbsp;*&nbsp;@param&nbsp;{HTMLElement}&nbsp;container&nbsp;-&nbsp;A&nbsp;domElement&nbsp;where&nbsp;default&nbsp;control&nbsp;widget&nbsp;will&nbsp;be&nbsp;attached&nbsp;to</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">&nbsp;*/</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">PANOLENS.Widget&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">function</span>&nbsp;(&nbsp;container&nbsp;)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;THREE.EventDispatcher.call(&nbsp;this&nbsp;);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;this.DEFAULT_TRANSITION&nbsp;&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ffd500">'all&nbsp;0.27s&nbsp;ease'</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;this.TOUCH_ENABLED&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;PANOLENS.Utils.checkTouchSupported();</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;this.PREVENT_EVENT_HANDLER&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">function</span>&nbsp;(&nbsp;<span style="color:#4be6fa">event</span>&nbsp;)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">event</span>.preventDefault();</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">event</span>.stopPropagation();</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;};</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;this.container&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;container;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;this.barElement;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;this.fullscreenElement;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;this.videoElement;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;this.settingElement;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;this.mainMenu;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;this.activeMainItem;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;this.activeSubMenu;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;this.mask;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div></div><div style="text-align:right; margin-top:-13px; margin-right:5px; font-size:9px; font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4f; text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom; padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none; color:white"><span style="font-size:9px; word-break:normal; background-color:#4f4f4f; color:white; border-radius:10px; padding:1px">cs</span></a></td></tr></table></div>
딱 fullscreenElement 변수를 따라가니 어렵지 않게 this.createFullscreenButton(); 전체화면을 만드는 함수를 찾을 수 있었다. 이 함수가 어떤 동작을 하는지 분석을 해야겠다.