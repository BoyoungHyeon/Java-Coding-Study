
#### HTML
```html
 <span class="btn_share">공유하기</span>
        <div class="shareBox">
            <a href="#" class="btn_share_sns" id="sns_facebook" title="페이스북 연동 새창열기" onclick="shareSns('facebook');">
                <img src="${pageContext.request.contextPath}/resources/img/sub/icon_share_facebook.png" alt="페이스북 공유하기"></a>
            <a href="#" class="btn_share_sns" id="sns_blog" title="새창열림" onclick="shareSns('blog');">
                <img src="${pageContext.request.contextPath}/resources/img/sub/icon_share_blog.png" alt="블로그 공유하기"></a>
            <a href="#" id="sns_urlCoby" class="btn_share_sns" title="새창" onclick="clip(); return false;">
                <img src="${pageContext.request.contextPath}/resources/img/sub/icon_share_link.png" alt="링크 공유하기"></a>
        </div>
</span>
```


##### JS
```js
function shareSns(sns){
        var snsTitle = '';
        var snsItems = new Array();
        var winOpt = new Array();
        var snsUrl = location.href;

        snsItems['facebook'] = "http://www.facebook.com/share.php?t="+encodeURIComponent(snsTitle) + "&u=" + encodeURIComponent(snsUrl);
        snsItems['blog'] = "http://blog.naver.com/openapi/share?url=" + encodeURIComponent(snsUrl) + "&title=" + encodeURIComponent(snsTitle);

        winOpt['facebook'] = "";
        winOpt['blog'] = "width=500, height=500, resizable=yes";

        var win = window.open(snsItems[sns], sns, winOpt[sns]);
        if (win) {
            win.focus();
        }
    }
```
