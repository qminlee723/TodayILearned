## 관통프로젝트



## Modal

1. 구조 이해하기

2. 모달의 id와 data-bs-target이 무조건 일치해야 합니다!

3. data-bs-target 은 #id

4. data-bs-toggle="modal" 넣어줘야한다

5. html, css, js

6. `position: fixed`

7. html <body> tag 안에 모달을 넣어준다 => 버튼과 연결작업을 해야한다

   (버튼의 data-bs-target에다가 #id 작업 해주는것)

8. 모달의 id는 하나만 있어야되니까 id는 1, 2.. 이런식으로 유일하게 주



```
MODAL 주의사항
```



## Bootstrap

1. cheatsheet





# :star: 천기누설

## HTML (Hyper Text Markup Language)

* HTML 문서의 기본구조 (!+tab하면 나오는거)
* 시맨틱 태그

  * 이름에 의미를주는 것
* OM tree 구조
* 주요 태그와 속성

  * table, form, input 안나옵니다
  * span 은 인라인 요소이므로 height, margin top bottom 안됨


* 인라인 요소(span등)에 margin top bottom 가능? ㄴㄴ

* d-inline, d-block, d-flex... d stands for display

  



## CSS

* 단위, 크기, 속성
  * 단위(크기, 속성)
    * 컬러, 사이즈(vh, vem, rem, pixel, %) 암기
  
* **선택자(selector) 및 우선순위**
  
  * 선택자 내용 다 정리
  * 우선순위
  * A B, A + b, A ~ B 구분
  
* 박스모델
  * content - padding - border - margin
  * 마진을 선택shortend
    * 1일때 전부, 2개 상하/좌우 각각, 3개 좌우만 묶여서, 4개 시계방향
  
* 인라인, 블록요소 특징

* Block, inline, inlineblock 어떤 차이 있는지

* Position 
  * static (normal flow)
  * relative (normal flow)
  * absolute (out of flow - 부모 요소 기준)
  * fixed (out of flow)
  * sticky
  
* Float 안나온다 

* Flex
  * axis, container-item... 
  * 각 속성 다 정리(Flexbox)
  * 
  * - flex-shrink는 안나오고, flex-grow는 나온다
  
  ```html
  ###Flex-grow 이해하기
  
  <!DOCTYPE html>
  <html>
  <head>
  <style>
  #main {
    width: 600px;
    height: 100px;
    border: 1px solid #c3c3c3;
    display: flex;
  }
  
  #main div:nth-of-type(1) {flex-grow: 1;}
  #main div:nth-of-type(2) {flex-grow: 2;}
  #main div:nth-of-type(3) {flex-grow: 3;}
  #main div:nth-of-type(4) {flex-grow: 4;}
  #main div:nth-of-type(5) {flex-grow: 0;}
  </style>
  </head>
  <body>
  
  <h1>The flex-grow Property</h1>
  
  <div id="main">
    <div style="background-color:coral; width:100px;"></div>
    <div style="background-color:lightblue; width:50px;"></div>
    <div style="background-color:khaki; width:30px;"></div>
    <div style="background-color:pink; width:70px;"></div>
    <div style="background-color:lightgrey; width:50px;"></div>
  </div>
  
  <p><b>Note:</b> Internet Explorer 10 and earlier versions do not support the flex-grow property.</p>
  
  </body>
  </html>
  
  ```
  
  이런 코드가 있다고 하면, main의 width는 600px이고 아래 요소의 width 합은 300px이므로 300px의 빈공간이 생긴다. flex-grow의 기본값은 0이므로 따로 설정하지 않는다면 오른쪽 300px의 공간은 비어있게 된다.
  
  위 코드와같이 설정하면,flex-grow 1당 30px의 빈공간을 채우게된다. flex-grow의 총합이 10이므로 오른쪽 빈공간 300px을 10로 나누면 된다.
  
  coral:100+30*1=130px
  
  lightblue:50+30*2=110px
  
  khaki:30+30*3=120px
  
  pink:70+30*4=190px
  
  lightgrey:50+30*0=50px
  
  
  
  
  
  - align-items는 컨테이너속성
  - align-self는 아이템속성, 우선순위가 더 높음, 디폴트는 auto로 align-items를 상속받음
  
* color
  * rgba
  * rgb(A, B, C) 
    * 0~225
    * 극단으로 줬을때는 알아야 됨

  * hex

* * * 

  


## 반응형 웹

* Bootstrap
  * Grid System :star:
    * column이 12개
    * none + 5개: 6개의 grid breakpoints
      * 어떤게 tablet, phone, windows로 변하는지 .... dimensions 숫자 외우기
      * media query
  * Breakpoint
* Grid system
  * container
  * row
  * col

* Grid system breakpoints연습하기
  * 코드를 주고 구멍 뚫어놓으면 그 코드 완성하기



Bootstrap 문제 많이낼거임

- spacing 암기하기(0.25 0.5 1 1.5 3)
- color (0 or 255),(0 or 255),(0 or 255)일때 얼만지는 알아야함, rgba도 있는데 a는 0~1 범위임
- breakpoint 576 768 992 1200 1400
- grid-system(class container>row>col) 










# 웹사이트 만들기

## Markup

* 각 태그별 속성
  * 인라인, 블록
  * `li` -> list-decoration
  * `a` -> href..



## 스타일링

### 레이아웃

> 어떠한 display를 가지고 있는지 분석, Box model

* Position
  * 네모 위 네모 => absolute
  * 브라우저 기준 => fixed, sticky
* Flex
* Bootstrap Grid System(반응형)



### 스타일

* 컬러
* 사이즈
* 각 태그별 속성..





### 웹 개발시 :honey_pot:팁

* 마이리얼트립 웹사이트 성능 최적화
* animate.css cdn으로 받아올 수 있습니다
* 



