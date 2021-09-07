
### Javascript Cookie 사용하여 팝업창 오늘하루 보지않기

#### html
```html
 <c:if test="${not empty popupInfo }">
	<div class="popup_area">
		<c:forEach var="popupinfo" items="${popupInfo}" varStatus="status">
		<div id="popup_${status.count}" class="layer_popup on">
				${popupinfo.XSS_HCONTENT}
			<div class="popup_btn">
				<a onclick="todaycloseWin('todayCookie_${status.count}');" href="javascript:void(0);" class="close today_b">오늘하루 보지 않기</a>
				<a onclick="closeWin('popup_${status.count}');" href="javascript:void(0);" class="close close_b">닫기</a>
			</div>
		</div>
		</c:forEach>
	</div>
</c:if>
```
먼저 popupInfo에서 값이 있을 때만 밑의 <div class = "popup_are"> 코드를 실행한다.
popup창 한 개, 한 개 [오늘하루보지않기]/[닫기] 가 있으므로,
status를 사용해서 하나씩 증가하는 로직으로 만들어 주었다.


##### javascript
```javascript
<script>
	$( document ).ready(function() {

		if(getCookie('todayCookie_1') == 'done') {
			document.getElementById('popup_1').style.display = "none";
		}else {
			document.getElementById('popup_1').style.display = "block";
		}

		if(getCookie('todayCookie_2') == 'done') {
			document.getElementById('popup_2').style.display = "none";

		} else {
			document.getElementById('popup_2').style.display = "block";
		}

		if(getCookie('todayCookie_3') == 'done') {
			document.getElementById('popup_3').style.display = "none";

		} else {
			document.getElementById('popup_3').style.display = "block";
		}
	});


	// 쿠키 생성 함수
	function setCookie(cName, cValue, cDay){
		var expire = new Date();
		expire.setDate(expire.getDate() + cDay);
		cookies = cName + '=' + escape(cValue) + '; path=/ '; // 한글 깨짐을 막기위해
		if(typeof cDay != 'undefined') cookies += ';expires=' + expire.toGMTString() + ';';
		document.cookie = cookies;
	}
    

	// 쿠키 가져오기 함수
	function getCookie(cName) {
		var x, y; var val = document.cookie.split(';');
		for (var i = 0; i < val.length; i++) {
			x = val[i].substr(0, val[i].indexOf('='));
			y = val[i].substr(val[i].indexOf('=') + 1);
			x = x.replace(/^\s+|\s+$/g, ''); // 앞과 뒤의 공백 제거하기
			if (x == cName) {
				return unescape(y);
				// unescape로 디코딩 후 값 리턴
				}
		}
	}
    
    
    // 팝업창 닫기
	function closeWin(popId) {
		document.getElementById(popId).style.display = "none";    
	}


    // 오늘 하루 보지 않기 닫기
	function todaycloseWin(cookiename) {
		setCookie(cookiename, "done" , 1);     // 저장될 쿠키명 , 쿠키 value값 , 기간
		var popId = 'popup_' + cookiename.split('_')[1];
 		document.getElementById(popId).style.display = "none";    // 팝업창 아이디
	}
</script>
```

ready function에서 가장 직관적으로 짜려고 if문을 구현했는데
더 간단하게 줄여서 쓰셔도 될 듯 햐다.

 저는 html코드에 팝업 id 값이 박혀있는게 아니라
'popup_${status.count}', 'todayCookie_${status.count}' 을 사용했기 때문에
spilt으로 '-' 기준으로 뒤에 번호만 잘라주어서 마지막 todaycloseWin 부분을 구현했다.
어려운 코드는 아니지만, 나름 끙끙 작성하였으므로 기록해본다,,,

쿠키는 어렵다 ㄱ-


#### 추가
https://chrome.google.com/webstore/detail/editthiscookie/fngmhnnpilhplaeedifhccceomclgfbg?hl=ko 

추가로, 크롬에서 쿠키 확장 프로그램을 사용하면 번거롭게 개발자 도구 킬 필요 없이 비교적 간편하더라 추천드립니다~


 

 
