# WEB

* Full Stack
  * Front-end
    * HTML: 웹 페이지 구조생성
    * CSS: 웹페이지 스타일링
    * JavaScript: 웹페이지 기능추가
  * Back End

* 현재의 웹 표준
  * **WHATWG**(Web Hypertext Application Technology Working Group)
* HTML, CSS 관련 질문 
  * mdn을 앞에 붙이고 구글링 (ex: mdn input)
  * [MDN WEB DOCS](https://developer.mozilla.org/en-US/docs/Web/HTML)
  * [w3school](https://www.w3schools.com/)
  * [html연습해보기:mozilla](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input)

* Alt + B : Visual Studio에서 바로 웹 창 켜기
* 들여쓰기: 2칸
* 크롬 개발자 도구: ctrl + shift + i, f12
* 주석 
  * visual studio code에서 ctrl + /
  * <!-- 주석 쓰는 법 -->

## :ballot_box_with_check: Table of Contents





## :ballot_box_with_check: HTML(Hyper Text Markup Language)

### :zero: OVERVIEW

* 마크업 언어

  * 태그로 데이터와 문서의 구조를 표현하는 언어

  * 마크(mark)로 둘러싸인 언어: mark = tag

* \<title> 제목 \</title>  

  * 크롬 탭 위에 제목으로 나타남

* 마크다운은 마크업을 이용해서 만들어진 언어라는 뜻

  * 마크다운: 문서 작성시에 구조와 내용을 함께 적기위해 만들어지 마크업 언어

* 따라서 HTML이란, 하이퍼텍스트를 이용해 문서를 넘나드는 마크업 언어. HTML을 이용해서 웹 페이지의 구조를 작성한다. 

* 확장자는 .html

### :one: HTML 기본구조

#### 1. 기본구조

![image-20220203101908153](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203101908153.png)

* html: 문서의 최상위(root) 요소
* head: 문서 메타데이터 요소
  * 문서 제목, 인코딩(문자열을 표현하는 방식 중 하나), 스타일, 외부 파일 로딩 등
  * 일반적으로 브라우저에 나타나지 않는 내용
  * meta 는 metadata의 약자
* body: 문서 본문 요소
  * 실제 화면 구성과 관련된 내용

#### 2. head 예시

* 자주 쓰는 것

  * \<title> : 브라우저 상단 타이틀
  * \<link> : 문서 레벨 메타데이터 요소
  * \<script> : 외부 리소스 연결 요소(CSS 파일, favicon 등)
  * \<style> : CSS 직접 작성

* Open Graph Protocol

  * 메타 데이터(데이터의 데이터)를 표현하는 새로운 규약

    * HTML 문서의 메타 데이터를 통해 문서의 정보를 전달

    * 메타정보에 해당하는 제목, 설명 등을 쓸 수 있도록 정의

      ![image-20220203102647203](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203102647203.png)

      * 미리보기 같은 것

        ```html
        <meta property = "og:title" content="google 뉴스"
        <meta name = "og:description" content = "google 뉴스가 전세계 매체로부터 종합한 최신 뉴스">
        ```

        

#### 3. DOM(Document Object Model) 트리

![image-20220203103024456](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203103024456.png)

* 텍스트 파일인 HTML문서를 브라우저에서 렌더링 하기 위한 구조

  * HTML 문서에 대한 모델을 구성함
  * HTML 문서 내의 각 요소에 접근 / 수정에 필요한 프로퍼티와 메서드를 제공함
  * 따라서 각 요소 접근 및 수정이 용이

* 예시

  ![image-20220203110425549](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203110425549.png)

  

#### 4. 요소(element)

* 기본 구조

  ![image-20220203103504509](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203103504509.png)

  * 태그 이름은 대소문자를 구분하지 않음. 단, 소문자로 쓰자

* HTML 요소는 시작 태그와 종료 태그 그리고 태그 사이 내용으로 구성

  * 태그(element, 요소)는 컨텐츠(내용)을 감싸는 것으로, 그 정보의 성격과 의미를 정의

* 내용이 없는 태그 목록

  * br, hr, img, input, link, meta

* 요소는 중첩(nested)이 될 수 있음

  * 요소의 중첩을 통해 하나의 문서를 구조화
  * 여는 태그와 닫는 태그의 쌍을 잘 확인해야 함
    * 오류를 반환하는 것이 아닌 그냥 레이아웃이 깨진 상태로 출력되기 때문에, 디버깅이 힘들어질 수 있음.



#### 5. 속성(attribute)

![image-20220203104032343](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203104032343.png)

* 속성 작성 방식 통일하기
  * = 양 옆 공백은 없어야 한다 
  * 이렇게 링크를 보내줄 수 있는 것이 a 태그의 역할!
* 속성을 통해서 태그의 부가적인 정보를 설정할 수 있음
* 요소는 속성을 가질 수 있으며, 경로나 크기와 같은 추가적인 정보를 제공
* 요소의 시작 태그에 작성하며 보통 이름과 값이 하나의 쌍으로 존재
* 태그와 상관없이 사용 가능한 속성(HTML Global Attribute)들도 있음
  * 모든 태그의 사용가능한 속성들 



#### 6. HTML Global Attribute

* 공통으로 사용할 수  대표적인 속성(몇몇 요소에는 아무 효과가 없을 수도 있음)
  * id: 문서 전체에서 유일한 고유 식별자 지정
  * sytle: 인라인 스타일
  * title: 요소에 대한 추가 정보 지정(툴팁.. 마우스 커서 갖다대면 네모박스 나옴)
  * data-*(데이터셋): 페이지에 개인 사용자 정의 데이터를 저장하기 ㅜ이해 사용
  * tabindex: 요소의 탭 순서
  * class: 문서 정체에서 유일한 고유 식별자 지정



#### 7. :star: 시맨틱 태그

* HTML5에서 의미론적 요소를 담은 태그의 등장

  * 기존 영역을 의미하는 div, span, p 를 대체하여 사용

* 대표적인 태그 목록

  * header: 문서 전체나 섹션의 헤더(머리말 부분)
  * nav: 네비게이션
  * aside: 사이드에 위치한 공간, 메인 콘텐츠와 관련성이 적은 콘텐츠 
  * section: 문서의 일반적ㅇ니 구분, 컨텐츠의 그룹을 표현
  * article: 문서, 페이지, 사이트 안에서 독립적으로 구분되는 영역
  * footer: 문서 전체나 섹션의 푸터(마지막 부분)

  ![image-20220203111139813](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203111139813.png)

* Non semantic 요소는 div, span 등이 있으며, h1, table 태그들도 시맨틱 태그로 볼 수 있음

* 개발자 및 사용자 뿐만 아니라 검색엔진 등에 의미 있는 정보의 그룹을 태그로 표현

* 단순히 구역을 나누는 것 뿐만 아니라, '의미'를 가지는 태그들을 활용하기 위한 노력

* 요소의 의미가 명확해지기 때문에 코드의 가독성을 높이고, 유지보수를 쉽게 함

* 검색엔진최적화(SEO)를 위해 메타태그, 시맨틱 태그 등을 활용가능







### :two: HTML 문서 구조화

#### 1. Table



#### 2. form

* \<form>은  정보(데이터)를 서버에 제출하기 위한 영역
* 기본 속성
  * :star: action: form을 처리할 서버의 url (어디로 보낼 거야)
  * :star: method: form을 제출할 때 사용할 HTTP 메서드 (GET 혹은 POST) (GET, POST의 방법으로 보낼거야)
  * enctype: method가 post인 경우 데이터의 유형
    * application/x-www-form-urlencoded:기본값
    * multipart/form-data: 파일 전송시(input type이 file인 경우)

#### 3. input

* 다양한 타입을 가지는 입력 데이터 유형과 위젯이 제공됨

* \<input>의 대표적인 속성

  * name: form control에 적용되는 이름(이름/값 페어로 전송됨)
  * value: form control에 적용되는 값(이름/값 페어로 전송됨)
  * required, readonly, autofocus, autocomplete, disabled ... etc

  ```html
  <form action = "/search" method = "GET">
      <input type = "text" name = "q">
  </form>
  ```

  * GET: querystring에 url을 넣어서 연결
    * https://www.google.com/search?q=HTML
  * type: text, email...... 만약 match가 안되면 느낌표가 뜨면서 '올바른 **을 입력해주세요'라는 메세지가 뜬다
  * POST: 

#### 4. input label

* label을 클릭하여 input 자체의 초점을 맞추거나 활성화 시킬 수 있음

  * 사용자는 선택할 수 있는 영역이 늘어나 웹/모바일(터치) 환경에서 편하게 사용할 수 있음
  * label과 input 입력의 관계가 시각적 뿐만 아니라 화면리더기에서도 label을 읽어 십게 내용을 확인할 수 있도록 함

* \<input>에 id속성을, \<label>에는 for 속성을 활용하여 상호 연관을 시킨다.

  ```html
  <label for="agreement">개인정보 수집에 동의합니다.</label>
  <!-- 개인정보수집에동의합니다를 선택했을 때 input에 체크가 되는 것-->
  <input type="checkbox" name="agreement" id="agreement"
  <!-- name은 데이터에 관한 이름, type은 타입 이름-->
  ```



#### 5. input 유형 - 일반

* 일반적으로 입력을 받기 위해 제공되며, 타입별로 HTML기본 검증 혹은 추가 속성을 활용할 수 있다

  * text: 일반 텍스트 입력
  * password: 입력시 값이 보이지 않고, 문자를 *로 표현
  * email: 이메일 형식이 아닌 경우 form 제출 불가
  * number: min, max, step 속성을 활용하여 숫자 범위 설정 가능
  * file: accept 속성을 활용하여 파일 타입 지정 가능

  

#### 6. input 유형 - 항목 중 선택

* 일반적으로 label을 사용하여 내용을 작성하여 항목 중 선택할 수 있는 input을 제공
* 동일 항목에 대해서는 name을 저장하고, 선택된 항목에 대한 value를 지정해야 함
  * checkbox: 다중 선택
  * radio: 단일 선택



#### 7. input 유형 - 기타

* 다양한 종류의 input을 위한 picker를 제공
  * color: color picker
  * date: date picker
* hidden input을 활용하여 사용자 입력을 받지 않고 서버에 전송되어야 하는 값을 설정
  * hidden: 사용자에게 보이지 않는 input







## :ballot_box_with_check: CSS(Cascading Style Sheets)

* 스타일을 지정하기 위한 언어

* 선택하고, 스타일을 지정한다

* 용어 정리

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203140805831.png" alt="image-20220203140805831" style="zoom:50%;" />



### :zero: OVERVIEW

* CSS구문은 선택자를 통해 스타일을 지정할 HTML 요소를 선택

* 중괄호 안에서는 속성과 값, 하나의 쌍으로 이루어진 선언을 진행

* 각 쌍은 선택한 요소의 속성, 속성에 부여할 값을 의미

  * 속성(Property): 어떤 스타일 기능을 변경할지 결정
  * 값(Value): 어떻게 스타일 기능을 변경할지 결정

* 정의 방법

  * inline 

    ![image-20220203142817353](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203142817353.png)

    * 해당 태그에 직접 style 속성을 활용

  * embedding(내부 참조)

    ![image-20220203142838801](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203142838801.png)

    ![image-20220203143105078](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203143105078.png)

    * \<head> 태그 내에 \<style>에 지정

  * link file(외부 참조)

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203142926011.png" alt="image-20220203142926011" style="zoom:80%;" />

    ![image-20220203143118363](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203143118363.png)

    * 같은 CSS는 하나의 파일로 묶으면 된다

    * 외부 CSS파일을 <head>내 <link>를 통해 불러오기

      

### :one: Selectors(선택자)

#### 1. 기본선택자

* 전체 선택자, 요소 선택자
  * 요소 선택자: h1, h2, div, sapn, strong .... 
* 클래스 선택자, 아이디 선택자, 속성 선택장
  * 클래스 선택자: .my_class, <a
  * 아이디선택자: #id_name, <a id="id_name"

#### 2. 결합자(Combinators)

* 자손(descendant) 결합자, 자식(child) 결합자

  * 자손 결합자: A B (A를 만족하는 모든 하위요소 중에서 B를 만족하는 모든 요소)
  * 자식 결합자: A > B (A의 자식(1차 하위요소) 중에서 B를 만족하는 애를 선택하겠다)

* 일반 형제 결합자, 인접 형제 결합자

  * 일반 형제 결합자: A ~ B(A의 모든 형제 중에서, B를 만족하는 요소)
  * 인접 형제 결합자: A + B(A의 모든 형제 중에서 바로 다음에 오는 애만 선택)

  ```html
  <!DOCTYPE html>
  <head>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="style.css"> <!-- 외부에서 데리고 오는 것 -->
    <title>나의 첫 CSS</title>
  </head>
  <body>
    <h2>H2</h2>
    <p>P</p>
    <span>SPAN</span>
  </body>
  </html>
  ```

  ```css
  h2 + span {
      color: red;
  }
  /* 안 빨개짐 */
  
  h2 ~ span {
      color: red;
  }
  /* 빨개짐 */
  ```



#### 3. 의사 클래스/요소(Pseudo Class)

* 링크, 동적 의사 클래스

  * 마우스가 올라가면 색이 바뀐다던지, 움직임에다가 지정하는 것

* 구조적 의사 클래스, 기타 의사 클래스, 의사 엘리먼트, 속성 선택자

* 예시(안 외워도 됨)

  1. 동적 의사 클래스
     - **:link** : 사용자가 아직 한 번도 해당 링크를 누르지 않은 상태 ( a요소 기본 )
     - **:visited** : 사용자가 한 번이라도 해당 링크를 누른 상태
     - **:hover** : 사용자의 마우스 커서가 위에 올라가 있는 상태
     - **:active** : 사용자의 마우스 커서가 클릭중인 상태
     - **:focus** : tab키로 focus가 맞춰진 상태

  2. 상태 의사 클래스
     - **:checked** : input의 checkbox나 raidobutton이 체크된 상태
     - **:enabled** : input의 "type=text", select, option에서 사용자가 선택한 상태
     - **:disabled** : input의 "type=text", select, option을 사용자가 선택할 수 없도록 만든 상태출처 - [https://aboooks.tistory.com/311](https://aboooks.tistory.com/311)

  3. 구조 의사 클래스
     - **:first-child** : 모든 자식 요소 중에서 첫 번째에 위치하는 자식을 선택
     - **:nth-child(n)** : 모든 자식 요소 중에서 n번째에 위치하는 자식을 선택
     - **:last-child** : 모든 자식 요소 중에서 마지막에 치하는 자식을 선택
     - **:first-of-type** : 모든 자식 요소 중에서 첫 번째에 등장하는 특정 요소를 선택
     - **:nth-of-type(n)** : 모든 자식 요소 중에서 n번째로 등장하는 특정 요소를 선택
     - **:last-of-type** : 모든 자식 요소 중에서 마지막으로 등장하는 특정 요소를 선택

  4. 선택자 

     - **::first-letter** : 요소의 텍스트에서 첫 번째 글자에 스타일을 적용한다.블록타입의 요소에만 사용 가능하다.
     - **::first-line** : 요소의 텍스트에서 첫 줄에 스타일을 적용한다.블록타입의 요소에만 사용 가능하다.
     - **::before** : 요소의 콘텐츠 시작부분에 생성된 콘텐츠를 추가한다.

     - **::after** : 요소의 콘텐츠 끝부분에 생성된 콘텐츠를 추가한다.



#### 4. 선택자 with 개발자 도구

* #sect1>ul>li:nth-child(1)

* 네이버 모자 예시

  * #header>div.special_bg>div>div.logo_area>h1>a

  

#### 5. 선택자 정리

* 요소 선택자
  * HTML 태그를 직접 선택
  
* 클래스 선택자
  * 마침표(.)문자로 시작하며, 해당 클래스가 적용된 항목을 선택
  * 여러개 전용(클래스를 정의해놓고, 여러군데 가져다가 쓴다)
  
* 아이디 선택자
  * #문자로 시작하며, 해당 아이디가 적용된 항목을 선택
  * 일반적으로 하나의 문서에 1번만 사용. 여러 번 사용해도 동작하지만, 단일id를 사용하는 것을 권장
  * id선택자를 하나만 쓰라는게 아니라, #id_name을 쓴다면, 한번만 쓰이고 html문서에 한 번만 쓰여야 하는 것이 정석
  * 그래야 제대로 한번에 가져올 수 있음(ex) #KOSPI_now)

* CSS 적용 우선순위(cascading order)

  * 중요도(Importance) - 사용시 주의(우선순위 다 무시하고 이거 먼저!, 잘 안씀)
    * !important 
  * :star: 우선순위(Specificity)
    * :star: 인라인 > id > class :star: , 속성, pseudo-class > 요소, pseudo-element
  * css파일 로딩 순서

* CSS 상속

  * [참고 웹사이트](https://www.w3.org/TR/CSS21/propidx)

  * CSS는 상속을 통해 부모 요소의 속성을 자식에게 상속한다.
    * 속성(프로퍼티) 중에는 상속이 되는 것들과 되지 않는 것들이 있다
    * 상속 되는 것 예시
      * Text 관련 요소(font, color, text-align), opacity, visibility 등
    * 상속 되지 않는 것 예시
      * Box model 관련 요소(width, height, margin, padding, border, box-sizing, display)
      * position 관련 요소(position, top/right/bottom)
      * 상속되지 않는 것도, inherit이라는 걸 쓰면 자동적으로 상속되게 만들 수 있음
    
    

### :two: 단위

#### 1. 크기 단위: 고정 vs 가변

* 고정 크기단위

  * px(픽셀)
    * 모니터 해상도의 한 화소인 '픽셀'기준
    * 픽셀의 크기는 변하지 않기 때문에 고정적
  * in(인치)
    * 고정크기단위긴 하지만, 운영체제마다 조금씩 달라진다
    * DPI가 달라지기 때문임

* 가변 크기단위

  * %()

    * 반응형
    * 백분율 단위
    * 가변적인 레이아웃에서 자주 사용(핸드폰, 아이패드, 노트북...)

  * em

    * (바로 위, 부모 요소에 대한) 상속의 영향을 받음
    * 배수 단위, 요소에 지정된 사이즈에 상대적인 사이즈를 가짐
    * 1em = 100% (of 부모요소)
    * 1.5em = 150%

  * rem

    * (바로 위, 부모 요소에 대한) 상속의 영향을 받지 않음
    * 최상위 요소(html)의 사이즈를 기준으로 배수 단위를 가짐

  * viewport

    * 웹 페이지를 방문한 유저에게 바로 보이게 되는 웹 컨텐츠의 영역(디바이스 화면)

    * 디바이스의 viewport를 기준으로 상대적인 사이즈가 결정됨

    * vw, vh, vmin, vmax

      * width의 1/100 = 1vw

        * 만약 width가 900px이면, 1vw = 9px

      * height의 1/100 = 1vh

      * 100 vw = 화면 너비 꽉 차게

      * 100 vh = 화면 세로 꽉 차게

    ```html
    <!-- 작은 화면에서는 폰트가 작게, 큰 화면에서는 크게 -->
    <style>
          div {
              background: blue;
              width: 100vmin;
              height: 100vimin;
          }
          
      </style>
    </head>
    <body>
      <div></div>
    </body>
    </html>
    
    
    <!-- 작은 화면에서도, 큰 화면에서도 정사각형 유지하고 싶을 때 -->
      <style>
          div {
              background: blue;
              width: 100vmin;
              height: 100vimin;
          }
          
      </style>
    </head>
    <body>
      <div></div>
    </body>
    </html>
    ```



#### 2. 색상 단위

* 색상 키워드
  * 대소문자를 구분하지 않음
  * red, blue, blackk과 같은 특정 색을 직접 글자로 나타냄
* RGB 색상
  * 16진수 표기법 혹은 함수형 표기법을 사용해서 특정 색을 표현하는 방식
* HSL 색상
  * 색상, 채도, 명도를 통해 특정 색을 표현하는 방식



### :three: Box model

#### 1. CSS 원칙

* 모든 요소는 네모(박스모델)이고, 위에서부터 아래로, 왼쪽에서 오른쪽으로 쌓인다(좌측 상단에 배치)

#### 2. Box model

* 모든 HTML 요소는 box 형태로 되어있음

* 하나의 박스는 네 부분(영역)으로 이루어짐

  ![image-20220203163456777](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203163456777.png)

  * content
  
  * padding
    * 내가 껴입는것
    * 컨텐트와 보더 사이의 거리
    
  * border
  
  * :star: margin ( margin, padding 둘 다 동일 )
  
    ![image-20220214024845898](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220214024845898.png)
  
    * margin-2 이면 십자가(상하좌우)
    * margin-3 이면 나누기(상 좌우 하 )
    * margin-4 이면 시계방향

#### 3. box-sizing

* 어디까지 기준으로 잡을 건지를 보는 것
* 



### :four: CSS Display

#### 1. CSS 원칙 II

* 모든 요소는 네모(박스모델)이고, 좌측 상단에 배치
* display에 따라 크기와 배치가 달라진다



#### 2. 대표적으로 활용되는 display

* block
  * 줄 바꿈이 일어나는 요소
  * 화면 크기 전체의 가로 폭을 차지한다
  * 블록 레벨 요소 안에 인라인 레벨 요소가 들어갈 수 있음.
* inline
  * 줄 바꿈이 일어나지 않는 행의 일부 요소
  * content 너비만큼 가로 폭을 차지한다
  * width, height, margin-top, margin-bottom을 지정할 수 없다. 
  * 상하 여백은 line-height로 지정한다
  * text라고 생각하면 쉬움

#### 3. 블록 레벨 요소와 인라인 레벨 요소

* block
  * div / ul, ol, li / p / hr / form 등
  * block의 기본 너비는 가질 수 있는 너비의 100%
  * 너비를 가질 수 없다면, 자동으로 부여되는 margin
* inline
  * span / a / img / input, label / b, em, i, strong 등
  * inline의 기본 너비는 컨텐츠 영역만큼



#### 4. 속성에 따른 수평 정렬

![image-20220203170428922](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203170428922.png)

* width를 꼭 줘야 반영이 된다.

  

#### 5. Display

* display: inline-block
  * 속성을 inline-block으로 준다면, block과 inline 레벨 요소의 특징을 모두 가진다.
  * inline처럼 한 줄에 표시 가능하고, block처럼 width, height, margin 속성을 모두 지정할 수 있다. 블럭 사이에 인라인 요소를 채울 수 있다고 생각하면 쉽다.
* display: none
  * 해당 요소를 화면에 표시하지 않고, 공간조차 부여되지 않음
  * 이와 비슷한 :star: visibility: hidden은 해당 요소가 공간은 차지하나, 화면에 표시만 하지 않는다. 
* [이외 다양한 display 속성을 알고 싶다면](https://developer.mozilla.org/ko/docs/Web/CSS/display)



### :five: Position

#### 1. CSS position

* 문서 상에서 요소를 위치를 지정
* 좌표 프로퍼티(top, bottom, left, right)를 사용하여 이동 가능
* static
* relative
* absolute
* fixed

#### 2. static(기준위치)

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203172143240.png" alt="image-20220203172143240" style="zoom: 67%;" />

* 모든 태그의 기본 값(기준 위치)

* 일반적인 요소의 배치 순서에 따름(좌측 상단)
* 부모 요소 내에서 배치될 때는 부모 요소의 위치를 기준으로 해서 배치 됨.



#### 3. relative(상대위치)

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203172207399.png" alt="image-20220203172207399" style="zoom:67%;" />

* 자기 자신의 static 위치를 기준으로 이동(normal flow 유지)
* 레이아웃에서 요소가 차지하는 공간은 static일 때와 같음
* 원래 있던 그 자리를 차지하고 있으면서, 움직이는 거임



#### 4. absolute(절대위치)

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203172226309.png" alt="image-20220203172226309" style="zoom:67%;" />

* 요소를 일반적인 문서 흐름에서 제거 후 레이아웃에 공간을 차지하지 않음(normal flow에서 벗어남)
* static이 아닌 가장 가까이 있는 부모/조상 요소를 기준으로 이동(없는 경우 body)
* viewport를 기준으로 하는 것이 아닌, 절대적인 위치에다가 딱 위치시키는 것
* 공중에 뜨는거임.. 원래 있던 그 자리는 빈다 
* 유튜브 썸네일에 동영상 길이 나타나는거나, 재생버튼 뜨는거나... 그런것들



#### 5. fixed(고정위치)

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203172246271.png" alt="image-20220203172246271" style="zoom:67%;" />

* 요소를 일반적인 문서 흐름에서 제거 후 레이아웃에 공간을 차지하지 않음(normal flow에서 벗어남)
* 부모 요소와 관계없이 viewport를 기준으로 이동
* 스크롤 시에도 항상 같은 곳에 위치함(광고 생각하면 편함)
* sticky와 비교 ===> 나중에 구글링해보기 :question:



#### 6. absolute vs relative



#### 7. CSS 원칙

* CSS 원칙 I, II: Normal flow
  * 모든 요소는 네모(박스모델), 좌측상단에 배치
  * display에 따라 크기와 배치가 달라짐
* CSS 원칙 III
  * position으로 위치의 **기준**을 변경
    * relative: 본인의 원래 위치
    * absolute: 특정 부모의 위치
    * fixed: 화면의 위치









# :star::star: 유용한 사이트

노션 참고!





contnet box and border box의 차이

- content box 가 default
- image와 배경색상은 padding까지 적용된다
- box-sizing의 기본은 content box, but 더 주고 싶다면 box-sizing에다가 border-box
- content+padding+border까지 합쳐서 border-box(width-height)

* class는  동일한 속성을 여러 id에다가 주고 싶을 때

  ```css
  .box {
      width:600px
      height: 400px
      border 2px solid black;
  }
  
  
  ```

  

* id는 한개

  ```html
  <div class="box" id="box-01"></div>
  ```

  ```css
  #box-01 {
      background-color: white;
  }
  ```

  



:star: 시험에 잘 나온느 부분

CSS selector

CSS 심화







Emmet

- `>`  태그를 만들고 들여쓰기
- `*n` 반복
- `+` 줄바꿈 + 다음 태그 추가
- `.` class 지정
- `#` id 지정

- `{content}` 내용 입력

```html
table>tr*5>td*3 (row 5줄, column 3줄)

div*5.box (div 다섯개 줄 건데 클래스를 다섯개 만들 것)

div>a (div 안쪽에 a 태그)

div>p (div 안쪽에다가 p 태그를 만들겠어)

div>p*5+span*3 (div안쪽에 p를 다섯 개, span을 세 개)

div.box(div에 box라는 클래스를 줄거야)

div.box>div*3#hello(div에 box라는 클래스를 줄 거고, 이 div 안에 div를 3개 더 만들건데, 이 3개의 div에 hello라는 아이디를 줄 거야)


- `>`  태그를 만들고 들여쓰기
- `*n` 반복
- `+` 줄바꿈 + 다음 태그 추가
- `.` class 지정
- `#` id 지정
- `{content}` 내용 입력
```

