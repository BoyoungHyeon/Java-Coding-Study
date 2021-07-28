
####  IndexOutOfBoundsException

##### 에러나던 코드
 ```java
////미리보기 조회
		List<HashMap<String, Object>> PreviewBoard = boardDataAdminService.getPreviewBoard(param);
		String previewboardmenuurl = PreviewBoard.get(0).get("MENUURL").toString();
		param.put("board_seq", getParameter("board_seq"));
```
이 에러는 ArrayList에서 get(index)했을 때, 값이 없는데 자꾸 get으로 가져오려해서 생기는 에러다.
이때는 ArrayList에서 get(0) 이렇게 가져온게 없는지 확인해야한다.
ArrayList 초기화 후 넣은 값이 없는데 0을 찾으면 없기 때문에 당연한 에러였다.



#####  에러 해결 코드
 ```java
////미리보기 조회
        List<HashMap<String, Object>> PreviewBoard = boardDataAdminService.getPreviewBoard(param);
        if(PreviewBoard.size()!=0) {
            String previewboardmenuurl = PreviewBoard.get(0).get("MENUURL").toString();
            param.put("board_seq", getParameter("board_seq"));
            model.addAttribute("previewboardmenuurl", previewboardmenuurl);
        }
```
조건으로 사이즈가 0이 아닐때만 검색되도록 만들었더니 코드가 잘 실행된다.
