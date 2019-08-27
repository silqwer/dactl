---
layout: post
title:  "intelliJ spring mvc "
tags:
  - intelliJ                  
hero: /../assets/resources/img/intelliJ/mvc/m1.jpg
overlay: orange
published: true

---
## intelliJ 를 사용해서 spring mvc 구축하기
intelliJ를 가지고 게시판 만들기를 시작하려고 한다. 
가장 기본적인 게시판을 구현해서 intelliJ의 기능을 하나씩 익혀나가는 것이 목표이다. 
{: .lead}
우선 intelliJ를 켜고 새롭게 프로젝트를 만든다. 
<!–-break-–>

## 1. Spring mvc project 생성 
<img src='/../assets/resources/img/intelliJ/mvc/m1.jpg' alt='m1'>
[File] → [New] → [Project...] 를 눌러서 새로운 프로젝트를 생성한다.
<img src='/../assets/resources/img/intelliJ/mvc/m2.jpg' alt='m2'>
왼쪽 메뉴에서 Spring 을 선택하고 Spring MVC (4.3.18.RELEASE)를 선택한다.
<img src='/../assets/resources/img/intelliJ/mvc/m3.jpg' alt='m3'>
<img src='/../assets/resources/img/intelliJ/mvc/m4.jpg' alt='m4'>
Project SDK에서 JDK를 잡아주는데 나는 전에 다운받은 openJDK9로 설정했다.
<img src='/../assets/resources/img/intelliJ/mvc/m5.jpg' alt='m5'>
프로젝트 이름을 설정하고 프로젝트를 생성한다. 

## 2. local tomcat 추가
<img src='/../assets/resources/img/intelliJ/mvc/m6.jpg' alt='m6'>
intelliJ 우측 상단에서 [ADD CONFIGURATION...]을 클릭한다.
<img src='/../assets/resources/img/intelliJ/mvc/m7.jpg' alt='m7'>
Run/Debug Configurations 창의 왼쪽 상단의 (+)버튼을 누른다.
<img src='/../assets/resources/img/intelliJ/mvc/m8.jpg' alt='m8'>
Add New Configuration 에서 아래로 쭉 내리면 Tomcat Server가 보인다. 
클릭하면 Add New 'Tomcat Server' Configuration이 뜨는데 여기서 Local를 선택한다.
<img src='/../assets/resources/img/intelliJ/mvc/m9.jpg' alt='m9'>
서버의 이름을 서정하고 [CONFIGURE...]을 눌러 로컬의 톰캣으로 설정을 해준다. 
다른 포트와 설정을 해주고 [FIX] 버튼을 누르고 [OK] 버튼을 눌러 톰캣 서버를 추가한다.
<img src='/../assets/resources/img/intelliJ/mvc/m10.jpg' alt='m10'>
intelliJ 좌측 하단에 Application Servers에 톰캣이 추가된 것을 볼 수 있다. 

## 3. maven 추가
<img src='/../assets/resources/img/intelliJ/mvc/m11.jpg' alt='m11'>
생성한 프로젝트를 선택하고 마우스 오른쪽 버튼을 클릭해서 [Add Framework Support...] 를 선택한다. 
<img src='/../assets/resources/img/intelliJ/mvc/m12.jpg' alt='m12'>
Add Frameworks Support 왼쪽 목록에서 Maven 을 선택하고 [OK] 버튼을 클릭해 추가한다.
<img src='/../assets/resources/img/intelliJ/mvc/m13.jpg' alt='m13'>
intelliJ 우측 상단에 보면 Maven 창이 추가 된 것을 볼 수 있다. 

## 4. library 설정
프로젝트에서 Spring, Spring MVC를 사용하기 위해서 아래와 같은 작업이 필요하다.
<img src='/../assets/resources/img/intelliJ/mvc/m14-1.jpg' alt='m14-1'> 
intelliJ 우측 상단에 파란창 같은 아이콘(Project Structure)을 클릭한다.
<img src='/../assets/resources/img/intelliJ/mvc/m14.jpg' alt='m14'>
Output Layout의 output root의 WEB-INF을 클릭하고 lib 폴더를 만들어 준다. 
<img src='/../assets/resources/img/intelliJ/mvc/m15.jpg' alt='m15'> 
lib폴더를 선택하고 우측의 Spring-4.3.18.RELEASE, Spring mvc-4.3.18.RELEASE 추가해준다.

## 5. tomcat start
<img src='/../assets/resources/img/intelliJ/mvc/m16.jpg' alt='m16'>
그리고 서버를 구동하면 index.jsp 화면을 확인 할 수 있다.

 










 



## 메일인증 
<img src='/../assets/resources/img/intelliJ/i4.jpg' alt='i4'>
대학교 이메일로 인증을 받을 꺼라서 [UNIVERSITY EMAIL ADDRESS]를 선택하고 쭉쭉 정보를 입력한다. [APPLY FOR FREE PRODUCTS]을 누르면 학교 메일로 JetBrains에서 인증메일이 하나 날라온다. 
<img src='/../assets/resources/img/intelliJ/i5.jpg' alt='i5'>
[Confirm Request]을 눌러 인증을 마무리한다. 회원가입등의 추가 인증 과정을 거치면 
<img src='/../assets/resources/img/intelliJ/i6.jpg' alt='i6'>
JetBrains Product Pack for Students 가 1년동안 활성화 된다. 
