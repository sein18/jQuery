# jQuery

---

* __jQuery 시작__
  1. 셀렉터 표현식
  2. DOM 탐색
  3. 이벤트
  4. 이팩트
  5. Ajax

---

* __javascript & jQuery 차이__ 
  * javascript를 이용하여 더 빠르고 쉽게 작성하게 도와주는 API개념이다.

```js
//javascript
let li = document.getElementsByTagName("li")[0].style.backgroundColor = "pink";

//jQuery
$("li").eq(0).css("background-color","pink"); 	
```

---

* __jQuery 사용__

  * selector 표현식

  ```js
  //태그로 선택
  $("태그").~~;
      
  //아이디로 선택
  $("#아이디명").~~;
  
  //class로 선택하기
  $(".아이디명").~~;
  
  //parent child로 선택하기
  $(".아이디명").~~;
  ```

  *  selector:속성

  ```js
  //속성으로 선택
  $("img[title*=02]").~~~;
  
  $("input[name=chk]:checked").~~;
  
  $(this).prop("tagName").~~;
  ```

---

* __dom 활용__

  * eq(): 선택한 엘리먼트들 중에 인덱스로 검색
  * slice(): 선택한 엘리먼트들 중에 인덱스 길이로 탐색
  * first(): 선택한 엘리먼트들 중에 첫 번째 요소 탐색
  * last(): 선택한 엘리먼트들 중에 마지막 요소 탐색

  ```js
  $(function(){
      $("div>p").eq(0).click(function(){
           $("pre b").eq(0).toggle();
       });
  
      $("div>p").eq(1).click(function(){
          $("pre b").slice(1,2).toggle();
      });
  
      $("div>p").eq(2).click(function(){
          $("pre b").first().css("color","red");
      });
  
      $("div>p").eq(3).click(function(){
          $("pre b").last().toggle();
      });
  });
  ```

---

