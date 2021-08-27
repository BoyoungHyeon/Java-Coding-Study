
####  js 조건으로 input box 제어
```js
jQuery(function(){
        jQuery("cheked[name=etc_consultation01]").change(function(){
            var app_condition = jQuery(this).val();
            if(etc_consultation01 == "5")                            // 승인 거절일 때만 거절사유 나오게
            {
                $("#etc_consultation_detail").show();
            }
            else {
                $("#etc_consultation_detail").hide();                 // 아니면 거절 사유 숨김
            }
            jQuery("#etc_consultation_detail").val(etc_consultation_detail);
        });
    });
```


##### jsp / html 코드
```html
 <div class="input-checked-area">
       <input type="checkbox" id="id_etc_consultation0105"name="etc_consultation01" value="5"/>
           <label for="id_etc_consultation0105">
             희망학과
             <input type="text" name="etc_consultation_detail" id="id_etc_consultation_detail" value="" disabled/>
           </label>
  </div>
```
etc_consultation0101부터 etc_consultation0105까지 조건 5개로 만들어져있는데 부분만 가져왔다.
희망학과를 체크하면 input textbox가 활성화되고,
희망학과를 체크하지 않으면 input textbox가 비활성화 되는 제어 코드이다.
