---
layout: post
title:  "Letsencrypt renew"
tags:
  - letsencrypt
hero: /../assets/resources/img/letsencrypt/l1.png
overlay: "red" 
published: true

---
## Letsencrypt 갱신
개발서버에 올린 테스트 사이트에서 사용한 무료 인증서 Letsencrypt의 갱신 기간이 20일정도 남았다.
{: .lead}
처음에는 오픈소스를 검토한 내용과 결과물을 공유하기 위해서 만든 테스트 사이트가 이렇게 까지 중요해질지 몰랐다. 회사에서 없었던 걸 만들었으니...
<!–-break-–>
각설하고 인증서를 갱신하기 위해서 putty를 열고 
<div class="colorscripter-code" style="color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important; overflow:auto"><table class="colorscripter-code-table" style="margin:0; padding:0; border:none; background-color:#272727; border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px; border-right:2px solid #4f4f4f"><div style="margin:0; padding:0; word-break:normal; text-align:right; color:#aaa; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:130%"><div style="line-height:130%">1</div></div></td><td style="padding:6px 0"><div style="margin:0; padding:0; color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%">root@administrator:&nbsp;letsencrypt&nbsp;renew</div></div></td><td style="vertical-align:bottom; padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none; color:white"><span style="font-size:9px; word-break:normal; background-color:#4f4f4f; color:white; border-radius:10px; padding:1px">cs</span></a></td></tr></table></div>
라고 갱신 명령을 내렸다. 하지만 ... 
<img src='/../assets/resources/img/letsencrypt/l1.png' alt='l1'>

## renew failure
왠 오류인가.. 생각을 해보니 인증서를 갱신하는데 서버가 구동 중이다? 혹시나 하고 서버를 내리고 다시 명령을 내렸다.
<img src='/../assets/resources/img/letsencrypt/l2.png' alt='l2'>
이렇게 90일이라는 시간을 벌었다. 

## 인증서 만료?
2019.06.17 테스트 서버를 접속하니가 인증서가 만료되었단 화면이 출력됐다. 틀림없이 만료되기 전에 갱신을 했는데? 다시 putty로 letsencrypt renew를 하니 갱신 된 날짜로 출력이 됐다.
<img src='/../assets/resources/img/letsencrypt/l3.png' alt='l3'>
페이지에서 사이트정보보기를 통해서 인증서의 정보를 봤지만 결과는 똑같이 갱신이 되지 않았다. 구글에서 검색을 해도 결과는 renew...
<img src='/../assets/resources/img/letsencrypt/l4.png' alt='l4'>
예전에 인증서를 적용하면서 남겨논 메모를 보고 적용하면서 참고한 블로그를 다시 보면서 처음부터 다시 절차를 확인해봤다. 쭉 읽다가 보니 톰캣에 인증서를 적용할 때 PKCS12 포멧의 키 저장소 파일을 생성하는 부분을 보니 아... 갱신 받고 다시 키 저장소 파일을 생성해야 하나 보다 생각이 들었다. 

## PKCS12 변환
갱신받은 .pem 파일을 변환하는 과정을 거친다. 
<div class="colorscripter-code" style="color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important; overflow:auto"><table class="colorscripter-code-table" style="margin:0; padding:0; border:none; background-color:#272727; border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px; border-right:2px solid #4f4f4f"><div style="margin:0; padding:0; word-break:normal; text-align:right; color:#aaa; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div></div></td><td style="padding:6px 0"><div style="margin:0; padding:0; color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%">#&nbsp;cd&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">/</span>etc<span style="color:#0086b3"></span><span style="color:#ff3399">/</span>letsencrypt<span style="color:#0086b3"></span><span style="color:#ff3399">/</span>live<span style="color:#0086b3"></span><span style="color:#ff3399">/</span>도메인</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">#&nbsp;openssl&nbsp;rsa&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span><span style="color:#ff3399">in</span>&nbsp;privkey.pem&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>text&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">&gt;</span>&nbsp;devbit.key</div><div style="padding:0 6px; white-space:pre; line-height:130%">#&nbsp;openssl&nbsp;x509&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>inform&nbsp;PEM&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span><span style="color:#ff3399">in</span>&nbsp;fullchain.pem&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>out&nbsp;devbit.crt</div><div style="padding:0 6px; white-space:pre; line-height:130%">#&nbsp;openssl&nbsp;pkcs12&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>export&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span><span style="color:#ff3399">in</span>&nbsp;devbit.crt&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>inkey&nbsp;devbit.key&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>out&nbsp;devbit.p12&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span><span style="color:#4be6fa">name</span>&nbsp;tomcat</div><div style="padding:0 6px; white-space:pre; line-height:130%">#&nbsp;keytool&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>list&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>v&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>keystore&nbsp;devbit.p12&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">-</span>storetype&nbsp;pkcs12</div></div></td><td style="vertical-align:bottom; padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none; color:white"><span style="font-size:9px; word-break:normal; background-color:#4f4f4f; color:white; border-radius:10px; padding:1px">cs</span></a></td></tr></table></div>

- privkey.pem 파일을 devbit.key 파일로 변환
- fullchain.pem 파일을 devbit.crt 파일로 변환
- devbit.key과 devbit.crt 파일을 가지고 devbit.p12 파일로 변환
- devbit.p12 를 pkcs12 으로 저장

서버를 다시 시작하니 인증서가 갱신되어서 적용되었다. 

## 적용 테스트 주소
<a href='https://www.whynopadlock.com/results/f13cc1d9-f01e-4578-af14-c630f3ce065f'>https://www.whynopadlock.com/results/f13cc1d9-f01e-4578-af14-c630f3ce065f</a>