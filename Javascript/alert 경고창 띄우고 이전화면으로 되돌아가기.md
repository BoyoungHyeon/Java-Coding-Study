
####  이용 중인 이전 페이지로 돌아가기
```js
 <script>
function add(){
	alert("더 이상 이용할 수 없는 게시물 입니다. \n"); // 경고창
	history.back(); // 이전 페이지로 돌아가기 1
    history.go(-1); // 이전 페이지로 돌아가기 2
}
</script>

<body onload = "add()"> // 페이지 열리면 alert창 즉시 실행 
</body>
```


##### JS
```js
<script>
function add(){
	alert("더 이상 이용할 수 없는 게시물 입니다. \n"); // 경고창
	history.back(); // 이전 페이지로 돌아가기 1
    loacation.href = " 주소 "; // 해당 주소로 이동
}
</script>

<body onload = "add()"> // 페이지 열리면 alert창 a즉시 실행 
</body>
```
