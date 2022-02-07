# Web CSS layout

## :ballot_box_with_check: OVERVIEW

* CSS Layout
  * float
  * flexbox
  * grid
* bootstrap
  * bootstrap grid system
* Responsive web



## :ballot_box_with_check: CSS Layout

### :one: Float

* 인라인 요소로 블럭 요소를 감쌀 때 쓴다
* left, right 속성이 존재 
* float를 이용해 normal flow를 벗어난다
* inline 지정시 span
* div 지정시 block 
* 박스를 왼쪽 혹은 오른쪽으로 이동시켜 텍스트를 포함 인라인요소들이 주변을 wrapping 하도록 함. 요소가 Normal flow를 벗어나도록 함 by using positioning -> absolute: static이 아닌 부분, fixed: 브라우저(viewport기준
* float clearing
  * float를 사용했을 때 다음에 오는 정렬 요소를 지워주겠다
  * clear: both;
  * ::after ==> 의사요소 생성자
  * : 의사 클래스
  * :: 의사 요소

#### 속성

* none: 기본
* left: 요소를 왼쪽으로 띄움
* right: 요소를 오른쪽으로 띄움



:star: margin과 padding 계산하는 문제 

이 element의 margin과 padding이 얼마일까?

:star: 정렬 (가운데 왼쪽 오른쪽 정렬)

inline에서 ... lineheight를 높이랑 똑같이 줘서!

#### 예시

10rem => 160 px (root => 16px)



### :two: Flexbox

#### 1. Flexible Box Layout

* 축(axis)와 컨테이너(container)

  * 메인 축과 교차 축(main and cross)
  * 부모/자식(container/item)

* 내부 영역 안에서의 배치가 가능하게 됨 (1차원 레이아웃 모델)

* 사용해야 하는 이유?

  * 수평 구조 만들기 어려웠는데 컨테이너 안에 넣어서 수평 구조 만들기 
  * 수직 정렬이 용이해짐
  * 아이템의 너비와 높이 혹은 간격을 동일하게 배치

* 수평 요소를 배열하는게 쉬워졌다

  ```css
  .container { 
      display:flex
  }
  ```

* container에 넣을 수 있는 속성

  * display
    * flex
      * block 방식의 container를 만들겠다는 것
    * flex-inline
      * inline 방식의 container를 만들겠다는 것
  * flex-flow
  * justify-content

* - `display` - Flex Container를 정의
  - `flex-flow` - `flex-direction` 과 `flex-wrap` 을 줄여서 쓸 수 있음
    - flex-direction과 flex-wrap 두 개를 같이 쓰고 싶을 때 쓸 수 있는 것
  - `flex-direction` - item들의 주 축(main-axis) 설정
    - 메인 축, 교차축
      * 아이템들을 어떻게 정렬할건지
      * 아이템들의 메인축을 어떻게 잡을 건지를 명시해 주는 것이 
      * flex direction 입니다.
    - row, row-reverse, column, column-reverse
  - `flex-wrap` - item들의 줄 바꿈 설정
    - 아이템들을 어떻게 묶어서 줄 바꿈을 할 것인가 
    - nowrap(default)
      - 아이템들을 묶지 않고 한 줄로 표현하겠다는 것이 no wrap
      - 아이템들을 wrapping해서 여러 줄로 표시하지 않고, 아이템을 무조건 한줄로 보여달라는 것
      - 그래서 줄이면 박스들의 사이즈가 줄어든다
    - wrap
      - 크기가 줄어들 때 여러줄이 되는 것 
      - 아이템을 여러 줄로 표시하겠다
      - 내 viewport 크기에 따라서 item들이 여러 줄로 표시되게 된다. 
    - wrap-reverse
  - `justify-content` - 주 축(main-axis)의 정렬  방법 설정
  - `align-content` - 교차 축(cross-axis)의 정렬 방법 설정 (2줄 이상)

  - `align-items` - 교차 축(cross-axis)의 정렬 방법 설정 (1줄)

* item(축 이라는 개념을 가지고있다)에 넣을 수 있는 속성

  * * 
  * order
  * flex
  * align-self

* 

#### 2. Flex-direction

* Main axis 기준 방향 설정
* reverse... right to left script 같은거 쓸 때 (일본어)
* justify-content
* align-content
* 



* flexbox MDN 파일



#### 3. 활용





### :three: Grid





## :ballot_box_with_check: Bootstrap

### bootstrap grid system



## :ballot_box_with_check: Responsive Web









:star:

* 부트스트랩에서 많이 나옴
* 12!!!!