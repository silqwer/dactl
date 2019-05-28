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