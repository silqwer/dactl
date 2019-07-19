---
layout: post
title:  "Object Collision"
tags:
  - panolens
  - WebVR
  - 360VR
hero: /../assets/resources/img/panolens/collision/c1.png
overlay: red
published: true

---
## Collision 처리  
카메라를 오브젝트 쪽으로 이동시키니 오브젝트 안으로 카메라가 들어가는 현상이 일어난다. 
{: .lead}
회의를 통해서 카메라 오브젝트 안으로 들어가지 않게 충돌처리를 추가하기로 했다. 
<!–-break-–>
처음에 떠오른 생각은 카메라 좌표랑 오브젝트 좌표를 이용해서 일정거리 이상 접근하지 못하게 처리할까 생각했다. 하지만 이렇게 하면 오브젝트가 달라질 때마다 접근거리를 설정해야한다. 충돌처리 하는 방법을 검색하니 winapi 시간에 실습했던 과정이 떠올랐다. 크게 얻은 키워드는 AABB, BOX3, BoxHelper, 물리 관련 three.js 라이브러리 등이 있었다. 간단하게 오브젝트만 카메라가 통과하지 못하도록 처리하는 것이니 물리관련 라이브러리 까지 사용하고 싶지는 않다. 

## BoxHelper 
기본개념은 오브젝트들에 박스에 바운드박스를 씌워서 충돌여부를 판단할 수 있다. 
여기서 좀 고민이 됐던게 three.js 의 THREE.OBJLoader()를 통해서 오브젝트 모델를 불러와서 panorama에 add하는데 THREE.OBJLoader() 밖에서 object에 접근할 방법이 없어서 THREE.OBJLoader() 안에서 panorama에 add하고 센서값 처리를 아예 여기서 처리했다. 우선 테스트하기 위해서 오브젝트에 모델링에 BoxHelper를 추가했다. 
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">var</span>&nbsp;&nbsp;boundingBox&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">new</span>&nbsp;THREE.BoxHelper(object,&nbsp;<span style="color:#c10aff">0xff0000</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">panorama.add(boundingBox);</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

## Box3
그리고 충돌체크에 필요한 box3 객체를 생성한다. 
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">var</span>&nbsp;box3&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">new</span>&nbsp;THREE.Box3().setFromObject(boundingBox);</div></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

## 충돌체크
모델링 오브젝트에서 했던것을 카메라에도 똑같이 해서 처리하면 되겠지 했는데 카메라에는 적용되지 않아서 box3.containsPoint 을 이용해서 충돌체크를 했다.
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">var</span>&nbsp;collision&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;box3.containsPoint(&nbsp;viewer.getCamera().position&nbsp;);</div></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

## 결과 
<img src='/../assets/resources/img/panolens/collision/c2.gif' alt='o2'>
