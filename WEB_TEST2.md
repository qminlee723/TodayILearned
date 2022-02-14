# HTML

1. HTML 문서의 기본구조

   ```html
   <!DOCTYPE>
   <html lang="eng">
   <head>
       <meta charset="UTF-8">
       <title>hello</title>
   </head>
   <body>
   </body>
   </html>
   ```

2. DOM Tree (Document Object Model Tree)

   * 텍스트 파일인 HTML 문서를 브라우저에 렌더링 하기 위한 구조

3. 시맨틱 태그

   * <span>, <div> 빼고 다
   * aside: 사이드에 위치한 공간, 메인 콘텐츠와 관련성이 적은 콘텐츠 
   * section: 문서의 일반적인 구분, 컨텐츠의 그룹을 표현
   * article: 문서, 페이지, 사이트 안에서 독립적으로 구분되는 영역

4. 주요 태그와 속성

   * id: 문서 전체에서 유일한 고유 식별자 지정

   * sytle: 인라인 스타일
   * title: 요소에 대한 추가 정보 지정(툴팁.. 마우스 커서 갖다대면 네모박스 나옴)
   * data-*(데이터셋): 페이지에 개인 사용자 정의 데이터를 저장하기 ㅜ이해 사용
   * tabindex: 요소의 탭 순서
   * class: 문서 정체에서 유일한 고유 식별자 지정



# CSS

1. 크기 **단위**

   * 고정 크기단위

     * px(픽셀)
     * in(인치)
       * 고정크기단위긴 하지만, 운영체제마다 조금씩 달라진다(DPI가 달라서)
   * 가변 크기단위

     * %()

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

2. 색상 단위

   * RGB 색상 - 16진수 
   * HSL 색상 - 색상, 채도, 명도를 통해 특정 색을 표현

   

3. 선택자 및 우선순위

   * 선택자 정리해놓은거 보기
     * A > B: A의 자식 요소 B 선택
     * A B: A의 자손 요소 B 선택
     * A + B: 인접 형제 선택자 - 다음 형제 요소 B 하나만 선택
     * A ~ B: 일반 형제 선택자 - 다음 형제 요소 B 모두 선택
   * 우선순위:
     * !important > 인라인 > id > class, 속성, pseudo-class > 요소, pseudo-element

4. 상속되는 속성, 상속안되는 속성 구분

   * 상속되는 속성: 
     * text관련 요소(font, color, text-align), opacity, visibility
   * 상속 안되는 속성: 
     * boxmodel(widh, height, margin, padding, border, box-sizing, display)
     * position 관련 속성(position, top/right/bottom/left/z-index)

5. 박스 모델

   * content - padding - border - margin

     * 이미지는 padding 까지 적용됨
     * margin에는 배경색 지정 불가

   * 위에서부터 아래로, 왼쪽에서 오른쪽으로

   * margin shorthand

     ![image-20220214025129414](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220214025129414.png)

   * box-sizing

     * 기본적으로 모든 요소의 box-sizing은 content-box
     * border-box로 설정해서 볼 수 있음

6. 인라인, 블록 요소 특징

   * inline
     * 줄 바꿈이 일어나지 않는 행의 일부 요소
     * content 너비만큼 가로 폭을 차지
     * width, height, margin-top, margin-bottom을 지정할 수 없다.
     * 상하여백은 line-height으로 지정
     * span, a, img, input, label, b, em, i, strong
   * block
     * 줄 바꿈이 일어난다
     * 화면 크기 전체의 가로 폭을 차지한다
     * 블록 레벨 요소 안에 인라인 레벨 요소가 들어갈 수 있다
     * div, ul, ol, li, p, hr, form
   * inline-block
     * block 과 inline레벨 요소의 특징을 모두 가진다
     * inline처럼 한 줄에 표시 가능하고, block 처럼 width, height, margin 속성을 모두 가진다.

7. CSS position

   * static (normal flow): 기본 값(좌측 상단)

   * relative (normal flow)
     * static 위치를 기준으로 이동
   * absolute (out of flow - 부모 요소 기준)
     * 요소를 일반적인 문서 흐름에서 제거 후 레이아웃에 공간을 차지하지 않음
     * static이 아닌 가장 가까이 있는 부모/조상 요소를 기준으로 이동 (없으면 body)
   * fixed (out of flow)
     * 요소를 일반적인 문서 흐름에서 제거 후 레이아웃에 공간을 차지하지 않음
     * 부모요소와 관계없이, viewport를 기준으로 이동
   * sticky

8. Flexbox

   * Flex 속성
     * space-between: 아이템 **사이의 간격**을 균일하게 분배
     * space-around: **아이템을 둘러싼 영역**을 균일하게 분배
     * space-evenly: **전체 영역**에서 아이템 간 간격을 균일하게 분배

   *  flex-grow는 나온다

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

9. color

   * rgb(0~225)
   * rgba: a는 완전 투명 0 , 불투명 1
   * hex

10. font 

    * font size

      * html의 root 글꼴 크기는 16px

        <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220214033156369.png" alt="image-20220214033156369" style="zoom:50%;" />

      * mx-auto: 수평 중앙 정렬



## Bootstrap

1. Grid system
   * column 12개
   * grid breakpoints 6개
   * grid-system(class container>row>col) 
2. Grid system breakpoints
   * none
   * 576(sm)
   * 768(md)
   * 992(lg)
   * 1200(xl)
   * 1400(xxl)
3. Media query