
#### HTML
```html
<div class="lnbArea">
    <div class="lnbInside">
        <span class="btn_share">공유하기</span>
        <div class="shareBox">
            <a href="#" id="sns_urlCoby" class="btn_share_sns" title="새창" onclick="clip(); return false;">
                <img src="${pageContext.request.contextPath}/resources/img/sub/icon_share_link.png" alt="링크 공유하기"></a>
        </div>
</div>
```


##### JS
```js
function clip(){

        var url = '';    // <a>태그에서 호출한 함수인 clip 생성
        var textarea = document.createElement("textarea");  
        //url 변수 생성 후, textarea라는 변수에 textarea의 요소를 생성
        
        document.body.appendChild(textarea); //</body> 바로 위에 textarea를 추가(임시 공간이라 위치는 상관 없음)
        url = window.document.location.href;  //url에는 현재 주소값을 넣어줌
        textarea.value = url;  // textarea 값에 url를 넣어줌
        textarea.select();  //textarea를 설정
        document.execCommand("copy");   // 복사
        document.body.removeChild(textarea); //extarea 요소를 없애줌
        
        alert("URL이 복사되었습니다.")  // 알림창
    }  
```
