---
layout: post
title:  "Basic Instascan"
tags:
  - instascan
hero: /../assets/resources/img/instascan/setup.jpg
overlay: red
published: true

---
## Instascan.js 구동 
{: .lead}
- 켜기 버튼을 누르면 *스마트폰 후면부 카메라*가 켜진다.
- 끄기 버튼을 누르면 *스마트폰 후면부 카메라*가 꺼진다.
- 읽기 버튼을 무르면 *QRCODE*정보를 읽어온다. 
<!–-break-–>

<iframe id="instascanIframe" width="100%" height="500px;" src="/../assets/resources/html/instascan/instascan.html"></iframe>

<button id="onBtn" onClick="onInstascan();">켜기</button> 
<button id="offBtn" onClick="offInstascan();">끄기</button>
<button id="readBtn" onclick="readInstascan();">읽기</button>

<script type="text/javascript">
function onInstascan (){
	console.log('켜기');
	var istIframe = document.getElementById('instascanIframe');
	istIframe.contentWindow.onCamera();
}

function offInstascan (){
	console.log('끄기');
	var istIframe = document.getElementById('instascanIframe');
	istIframe.contentWindow.offCamera();
}

function readInstascan (){
	console.log('읽기');
	var istIframe = document.getElementById('instascanIframe');
	istIframe.contentWindow.readContent();
}

</script>

<div id="readView">
## 읽어드린 정보
</div>

