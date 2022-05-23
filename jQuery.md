# jQuery

---

* __jQuery 시작__
  1. 셀렉터 표현식
  2. DOM 탐색
  3. 이벤트
  4. 이팩트
  5. Ajax

---

* __javascript & jQuery 를 쓰는 이유__
  * javascript를 이용하여 더 빠르고 쉽게 작성하게 도와주는 API개념이다.

```js
//javascript
let li = document.getElementsByTagName("li")[0].style.backgroundColor = "pink";

//jQuery
$("li").eq(0).css("background-color","pink"); 	
```

* __(jQuery를 많이 쓰고있지만, 요즘에는 vanilla JS를 많이 사용한다.)__
  * `vanilla JS`란 순수 javascript를 활용한다는 뜻이라고 할 수 있다.

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

* __태그들의 부모, 형제 ,자식 탐색__

  * find("selector") : 선택한 엘리먼트의 자손들 중에 탐색하고자 하는 엘리먼트를 찾는다.
  * children("selector") : 선택한 엘리먼트의 자식요소들 중에 탐색하고자 하는 엘리먼트를 찾는다.
  * parent()/parents() : 선택한 엘리먼트의 부모요소를 찾는다.
  * next("selector") : 선택한 엘리먼트 다음에 따라오는 요소를 찾는다.

  ```js
  $(document).ready(function(){
      $("div").find("b").css({"font-size":"30px","color":"red"});
      //div자손 중 b태그들의 css변경
      
      $("div").children("#chd").text("2.children()");
      //div자식 중 
      
      $("#chd").parent().css("background-color","skyblue");
      //id가chd의 부모요소의 css변경
      
      $("p>b").parents("p").css("background-color","khaki");
      //p>b의 상위요소들 중에 p요소만 css변경
      
      $("p").eq(0).next().css({"font-size":"50px","color":"blue"});
      // $("p").eq(0).nextAll().css({"font-size":"50px","color":"blue"}); 
  });
  ```

  