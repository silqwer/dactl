---
layout: post
title:  "Panolens control sensor"
tags:
  - panolens
  - WebVR
  - 360VR
hero: /../assets/resources/img/panolens/control/c1.png
overlay: purple
published: true

---
## Not working sensor
운영중인 서버에 적용하기 앞서 개발서버에서 테스트를 하는데  스마트폰으로 VR모드에 들어가 Control를 Sensor하면 동작을 하지 않는다고 메일을 받았다.
{: .lead}
관련 메일을 읽고 내 폰으로 실제로 테스트를 해보니 정말로 이상하게 동작을 했다. Sensor(자이로)로 상하좌우를 둘러볼 수 없었다. 
<!–-break-–>

## Debugging in Chrome
The `deviceorientation` event is deprecated on insecure origins and will be removed in M76, around July 2019. Event handlers can still be registered but are no longer invoked since M74, around April 2019. See https://www.chromestatus.com/feature/5468407470227456 for more details.
{: .notice}
가장먼저 컴퓨터랑 스마트폰을 연결해서 디버깅(chrome inspect)을 해보니 위와 같은 오류, 경고문이 떳다. 

deviceorientation 이벤트는 7월 M76버전 부터 불완전한 origins에 지원하지 않고 제거되며 M74버전 이후에 더이상 호출되지 않는다는 말이다. 

## http? https.
예전에 ar.js를 가지고 놀 때 브라우저에서 스마트폰 카메라에 접근하기 위해서 http로는 접근을 할 수 없었다. (보안상의 이유로) https를 통해서 접근해야지 ar.js 라이브러리가 동작했다. 개발서버의 URL을 보니 http에서 동작하고 있었는데 혹시나 이것과 관련된 부분도 있지 않을까? 검색을 했다.
<img src='/../assets/resources/img/panolens/control/c1.png' alt='c1'>pnolens.js에서 일어난 문제는 아니었지만 다른 누군가도 나와 같은 문제에 직면하고 굉장히 크리티컬한 문제라고 인식하고 있었다. 답변자는 https에서 시도해보라고 이야기 했다.

## Insecure origins == http
Insecure origins이 http를 의미하는 것인가? 혹시나 하고 three.js github issues 에서 https를 검색해봤다. 역시나 관련된 이슈가 있었다. 마지막 문단을 읽어보니 https로 교체를해야 한다며 <a rel="nofollow" href="https://goo.gl/rStTGz">https://goo.gl/rStTGz</a> 로 링크를 하나 달아놓았다. 
<img src='/../assets/resources/img/panolens/control/ssl.png' alt='ssl'>

## Deprecating Powerful Features on Insecure Origins
불안전한 Origins에 대한 강력한 기능의 사용중단이란 타이틀의 내용이었다. 
<img src='/../assets/resources/img/panolens/control/c2.png' alt='c2'>
https에서만 접근 가능한 기능은 아래 6가지로 가이드 하고 있었다. 그래서 https, ssl 이 적용이 안된 개발서버에서 테스트할 때 자이로센서가 이상하게 동작한 것이다.
- Geolocation 
- Device motion / orientation
- EME
- getUserMedia
- AppCache
- Notifications
로컬호스트는 안전하다고 간주되어 해당 기능을 테스트 할 수 있었던 것이다. 

## test
테스트 사이트는 http와 https 접속을 동시에 지원하지 않는다. 그래서 생각한 것이 공식 페이지에서는 http와 https 접속을 지원하지 않을까? 역시나 http와 https 접속을 지원했다. 그리고 바로 chrome inspect을 시작했다.
<img src='/../assets/resources/img/panolens/control/http-min.gif' alt='c3'>
http로 테스트 하니 똑같은 문제가 발생했다.
<img src='/../assets/resources/img/panolens/control/https-min.gif' alt='c4'>
https로 테스트 하니 정상적으로 센서가 동작했다. 크롬에서 http로는 panolens sensor를 사용할 수 없다. 


