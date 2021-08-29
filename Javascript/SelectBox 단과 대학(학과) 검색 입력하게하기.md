
####  이용 중인 이전 페이지로 돌아가기
```js
 $('document').ready(function() {
  	var area0 = ["단과대학 선택","경영대학","문과대학","생명과학대학","정경대학","의과대학","간호대학"];
  	var area1 = ["경역학과"];
  	var area2 = ["국어국문학과","철학과","한국사학과","사학과","사회학과","한문학과","영어영문학과","중어중문학과","불어불문학과","독어독문학과"];
  	var area3 = ["생명과학부","생명공학부","식품공학과","환경생태공학부","식품지원경제학과"];
  	var area4 = ["정치외교학과","경제학과","통계학과","행정학과"];
  	var area5 = ["의예학과"];
  	var area6 = ["간호학과"];

 

 // 단과대학 선택 박스 초기화
 $("select[name^=hakbu]").each(function() {
   $selhakbu = $(this);
   $.each(eval(area0), function() {
    $selhakbu.append(""+this+"");
  	 });
  	 $selhakbu.next().append("학과 선택");
   });

 

 // 단과대학 선택시 학과 설정
  $("select[name^=hakbu]").change(function() {
   var area = "area"+$("option",$(this)).index($("option:selected",$(this))); // 선택지역의 구군 Array
   var $major = $(this).next(); // 선택영역 군구 객체
   $("option",$major).remove(); // 구군 초기화

   if(area == "area0")
    $major.append("학과 선택");
   else {
    $.each(eval(area), function() {
    $major.append(""+this+"");
    });
   }
 });
});
```


##### HTML코드
```html
<select name="hakbu" id="hakbu"></select>
<select name="major" id="major"></select>
```
