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

---

* __.hover__

  ```js
   // .hover() : 매개변수 2개를 받는다.
      $(".menu").hover(
          function(){
              $(this).children("div").show(); //보여주기
          },//이벤트 발생
          function(){
              $(this).children("div").hide();	//숨기기
          }//이벤트 종료
      );
  ```

---

* __event__

  * 이벤트 전파 : 요소들이 서로 포함관계인 경우 요소중 하나에 이벤트가 발생하면

    ​            중첩이된 요소들도 이벤트가 전파된다.

    ​            

  *  이벤트 전파 막기

​      			`stopPropagation() `: 이벤트 전파 막기

​      			`preventDefault()` : 이벤트에 의한 기본동작 막기

​      			`return false `: stopPropagation() + preventDefault() 합쳐진 결과

```js
 $(function(){
     $("a:eq(0)").click(function(e){  
         //div태그 안에 p태그 안에 a태그를 누르면 여러 모든 이벤트가 나오는걸 막기 위해 사용
         alert("a클릭!");
         //e.stopPropagation();
         // e.preventDefault();
         return false;
     });
 });
```

---

* __effect__
  * .animate({"style":"속성들",~~},sec): 애니메이션을 자유자제로 만든다.
    * animate({},~).animate.(~)~ 체인룰이 가능하다.!!
  * .hide() : 숨기는 기능
  * .show() : 보여주는 가능
  * .toggle() : 숨기고 보여주기를 왔다갔다 하는 기능
  * .slideUp() : 애니메이션을 적용하며 숨기는 기능
  * .slideDown(): 애니메이션을 적용하며 보여주는 기능
  * slideToggle(): 애니메이션을 적용하며 숨기고 보여주기를 왔다갔다 하는 기능
  * fadeOut(): 애니메이션을 적용하며 숨기는 기능
  * fadeIn(): 애메이션을 적용하며 보여주는 기능
  * fadeTo(sec.속성) : 매개변수를 적용하여 애니메이션효과를 지정할 수 있다 
  * fadeToggle() :애니메이션을 적용하며 숨기고 보여주기를 왔다갔다 하는 기능
  * .hasClass("클래스명"): 태그에 클래스 유무 확인
  * .removeClass("클래스명"): 클래스가 포함된 태그에 class지우기
  * .addClass("클래스명"): 클래스가 포함된 태그에 class넣기

---

* __replace__

  * replaceWith : 대체하기
  * replaceAll : 대체하기

  ```js
  //적용방식이 다르나 결과는 같다. 
  <script>
       $(function(){
           $("button:first").click(function(){
               $("p").replaceWith("<b>replaceWith</b><br>");
           }); 
  
           $("button:last").click(function(){
               $("<b>replaceAll</b><br>").replaceAll("p");
           });
   	});
  </script>
  ```

---

* __insertion__

  * .prepend() : 맨앞에 추가
  * .append() : 맨뒤에 추가
  * .html() : html요소를 바꾼다.
  * .text() : text 요소를 바꾼다.

  ```js
   <script>
       $(function(){
           $("button:eq(0)").click(function(){
               $("div").prepend("123"); // 맨앞
           });
           $("button:eq(1)").click(function(){
               $("div").append($("<p>").addClass("append").text("append")); // 맨뒤
           })
           $("button:eq(2)").click(function(){
               $("div").html("<b>html 요소를 바꾼다</b>");                
           })
           $("button:eq(3)").click(function(){
               $("div").text("<b>text 요소를 바꾼다</b>");                    
           })
   	});	
  </script>	
  ```

  * after()
  * insertAfter()
  * before()
  * insertBefore()

  ```js
  <script>
      $(function(){
          $("button:eq(0)").click(function(){
              $("#base").after("<div>새로운 엘리먼트(after)</div>");
          });
          $("button:eq(1)").click(function(){
              $("<div>새로운 엘리먼트(insertAfter)</div>").insertAfter("#base");
          });
  
          $("button:eq(2)").click(function(){
              $("#base").before("<div>새로운 엘리먼트(before)</div>");
          });
          $("button:eq(3)").click(function(){
              $("<div>새로운 엘리먼트(insertBefore)</div>").insertBefore("#base");
          });
      });
  </script>
  ```

---

* __delete__

  * .remove() : element까지 제거
  * .empty() : element는 냅두고 안에 내용 싹 다 지움

  ```js
  <script>
      $(document).ready(function(){
          $("p:eq(0)").click(function(){
              $(this).parent().remove();
          });
  
          $("p:eq(1)").click(function(){
              // $(this).empty();
              $(this).parent().empty();  //element는 냅두고 안에 내용 싹 다 지움
          });
  
          $("p:eq(2)").click(function(){
              let ele = $(this).detach();
  
              $("h1").append(ele);
          });
      });
  </script>
  ```

  

