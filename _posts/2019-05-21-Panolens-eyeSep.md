---
layout: post
title:  "Panolens ipd 설정"
tags:
  - panolens
  - WebVR
  - 360VR
hero: /../assets/resources/img/panolens/ipd post.png
overlay: orange
published: true

---
## IPD...그리고
panolens에서 IPD를 따로 설정해 주는 부분이 없다. 깃허브에도 따로 언급된 부분도 없다.
{: .lead} 
간단하게 눈사이의 거리를 담당하는 변수가 따로 있고, 이 변수의 크기만 조절하면 될 것 같다는 생각을 했다. 일단 VR Mode로 화면을 전환하는 부분에서 부터 코드 역추적을 시작했다.
<!–-break-–>
## StereoEffect
<img src='/../assets/resources/img/panolens/stereo.png' alt='stereo'> 소스에서 Stereoscopic으로 검색을 해서 따라가니 enableEffect 함수와 엮여있었다. 

## enableEffect
<img src='/../assets/resources/img/panolens/enableEffect.png' alt='enableEffect'>
함수는 위와가 같이 작성이 되어 있었고 StereoEffect, CardboardEffect 단어가 눈에 들어왔다. 다시 CardboardEffect으로 검색하니 PANOLENS.Viewer의 생성자에서 StereoEffect, CardboardEffect을 선언하고 있었다.

## StereoEffect
<img src='/../assets/resources/img/panolens/stereoEffect.png' alt='stereoEffect'> 쭉~ 코드를 읽어 가다가 setEyeSeparation? EyeSeparation을 set하는 함수인데 EyeSeparation가 뭐지? <img src='/../assets/resources/img/panolens/eyeSeparation.png' alt='eyeSeparation'> 번역을 해보니 눈 분리!!! _stereo.eyeSep 값이 얼마로 설정되어 있는지 확인하기 위해 보니 _stereo는 three.js 의 new THREE.StereoCamera 였다.

## new THREE.StereoCamera
<img src='/../assets/resources/img/panolens/stereoCamera.png' alt='eyeSeparation'> 여기기서 보니 eyeSep 값이 0.064로 내가 알고 있던 ipd의 평균 수치 (60mm~65mm)의 값과 근사해서 혹시나 싶었다. 





