---
layout: post
title:  "Html svg event test"
tags:
  - svg
  - test
hero: /../assets/resources/img/test/background.png
overlay: green
published: true

---
## Html으로 불러온 svg에서 svg관련 event가 동작하는지 테스트
<!–-break-–>

<script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>

<script>
	var arr = [
		'btn1',
		'btn2',
		'btn3'
	];
	var arrIdx = 0; 
	$( window ).on( "load", function() {
		var object  = document.getElementById("svgObj");
		var svgDoc = object.contentDocument;
		var background = svgDoc.getElementById("background");
		background.setAttribute("fill", "yellow");
		background.addEventListener("click", function(){
			console.log('mouse move');
			$('.post').append('<p>마우스 클릭</p>');
		});
		background.addEventListener("mousemove", function(){
			$('.post').append('<p>마우스 움직임</p>');
		});
		background.addEventListener("SVGScroll", function(){
			$('.post').append('<p>마우스 스크롤</p>');
		});
	});
	function colorChange(btnsObj, btnObj){
		btnsObj.css('background-color', 'gray');
		btnObj.css('background-color', 'red');
	}
	
</script>
<style>
	#background{
		width: 100%;
		height: 500px;
		background-color: antiquewhite;
	}
	.btn{
		width: 50%;
		height: 50px;
		background-color: gray;
		position: relative;
		left: 120px;
	}
	#btn1{
		top: 100px;
	}
	#btn2{
		top: 200px;
	}
	#btn3{
		top: 300px;
	}
</style>
<object id="svgObj" width="100%" height="600"  type="image/svg+xml" data="/../assets/file/ARS2018299914467.svg" ></object>