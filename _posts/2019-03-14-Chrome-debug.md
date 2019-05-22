---
layout: post
title:  "Chrome 디버깅"
tags:
  - Aframe.js
  - WebVR
  - 360VR
hero: /../assets/resources/img/aframe/chrome/debug.png
overlay: green
published: true

---
## 스마트폰에선 디버깅을 어떻게하지?
로컬에서 작업하고 오류가 나면 크롬 개발자 도구를 사용하면 되는데 폰으로 돌렸을 때 어떻게 확인해야하는걸까? 혹시나 하고 구글에 **스마트폰 크롬 디버깅**이라고 검색을 했다. (하늘아래 새로운건 없다.)
<img src='/../assets/resources/img/aframe/chrome/search.png' alt='search'>

## 스마트폰 디버깅 모드켜기
- 개발자 모드 켜기
- USB 디버깅 켜기
- 컴퓨터와 USB 연결 > 휴대전화 데이터에 접근 허용
- 스마트폰으로 크롬앱 실행
- PC 크롬에서 chrome://inspect 을 입력해서 접속 한 후 ‘Portforwarding’
- 

## 개발바 모드 켜기
<img src='/../assets/resources/img/aframe/chrome/p1.png' alt='dev'>
**스마트폰 설정 > 휴대전화 정보 > 소프트웨어 정보**에서 빌드번호를 연속적으로 터치한다. 그러면 **개발 설정완료 4단계, 3단계, 2단계, 1단계 전입니다.** <img src='/../assets/resources/img/aframe/chrome/p2.png' alt='stereo'> 메시지가 뜨고 계속 누르면 개발자 모드가 켜진다.

## USB 디버깅
<img src='/../assets/resources/img/aframe/chrome/p2.png' alt='usb'>
**스마트폰 설정 > 개발자 옵션**으로 들어가서 화면을 내리다 보면 디버깅 설정 부분이 보인다. 여기서 **USB 디버깅**을 켠다. 그리고 컴퓨터와 스마트폰을 연결하고 **휴대전화 데이터에 접근 허용** 메세지가 뜨면 **허용** 설정을 한다.

## inspect
<img src='/../assets/resources/img/aframe/chrome/p3.png' alt='usb'>
PC와 스마트폰(Chrome App 실행 후)이 연결되면 PC 크롬을 켜고 주소창에 <a href='chrome://inspect'>chrome://inspect</a> 을 입력한다. 해당 페이지가 뜨고 스마트폰 모델명, 크롬앱 버전, 그리고 실행시킨 크롬의 탭 정보(Url)가 뜨면 성공이다.
<img src='/../assets/resources/img/aframe/chrome/p4.png' alt='debug'>
inspect 를 누르면 개발자 도구가 활성화 되고 로그를 확인할 수 있다.  