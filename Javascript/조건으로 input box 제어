
####  js 조건으로 input box 제어
```js
$(document).ready(function () {
        <c:if test="${app.APP_CONDITION eq '1'}">
            $("#sub_app_condition").show();
        </c:if>
        <c:if test="${app.APP_CONDITION ne '1'}">
            $("#sub_app_condition").hide();                 // 아니면 거절 사유 숨김
        </c:if>
```
$(document).ready니까 처음에 페이지 시작할 때
app_condition 조건 이 1과 같으면 sub_app_condition을 보여주고,
app_condition 조건 이 1과 같지 않으면 sub_app_condition을 숨긴다


```js
   jQuery(function(){
        jQuery("select[name=app_condition]").change(function(){
            var app_condition = jQuery(this).val();
            if(app_condition == "1")                            // 승인 거절일 때만 거절사유 나오게
            {
                $("#sub_app_condition").show();
            }
            else {
                $("#sub_app_condition").hide();                 // 아니면 거절 사유 숨김
            }
        });
    });
```


##### jsp / html 코드
```html
<tr>
  <th class="left">승인상태</th>
    <td>
         <select name="app_condition" class="select1 w150px">
            <option value="0">선택</option>
            <option value="1" <c:if test="${app.APP_CONDITION eq '1'}">selected</c:if>>승인거절</option>
            <option value="2" <c:if test="${app.APP_CONDITION eq '2'}">selected</c:if>>승인대기</option>
            <option value="3" <c:if test="${app.APP_CONDITION eq '3'}">selected</c:if>>승인완료</option>
         </select>

         <c:if test="${app.APP_CONDITION_REASON != null}">
             <span name="sub_app_condition" id="sub_app_condition">※ 거절 사유 : <input type="text" name="app_condition_reason" class="input_text1 w200px" value="${app.APP_CONDITION_REASON}"/></span>
         </c:if>
    </td>
</tr>
```
