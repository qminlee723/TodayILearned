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
  - :star: `justify-content` - 주 축(main-axis)의 정렬  방법 설정
    - flex-start
      - 정렬 기준에 따라서 
    - flex-end
    - center
    - space-between
      - 가장 가에 있는 아이템을 가장 왼쪽 오른쪽에 두고, 나머지 아이템들을 간격이 동일하게 정렬해준다 
    - space-around
      - 아이템들 + 마진이라고 생각하면 쉬울 것 같음(그런데 마진 아님!!)
      - 
    - space-evenly
      - 모든 여백을 균등한 여백으로 만들어서 정렬
  - `align-content` - 교차 축(cross-axis)의 정렬 방법 설정 (2줄 이상일 때 적용됨. 한줄일 때는 align-items를 쓴다.)
    - flexwrap이 no wrap이면 정렬의 의미가 없다
    - stretch(default)
    - flex-start
    - flex-end
    - center ==> 교차축을 기준으로 한다. (flex-direction은 메인축을 기준으로 )
    - space-between
    - space-around

  - `align-items` - 교차 축(cross-axis)의 정렬 방법 설정 (1줄)
    - :star: align-content와 유사하지만, baseline이라는 코드가 추가가된다
    - item들 안에 

  

* item(축 이라는 개념을 가지고있다)에 넣을 수 있는 속성

  - :star: `order` - Item의 순서를 설정
    - 
  - `flex` - `flex-grow` , `flex-shrink` , `flex-basis` 에 대한 단축 속성!
    - 더하기(상하)
    - 나누기(위 중간 아래)
    - 시계방향
    - flex-grow(default)
    - flex-basis의 기본 값은 auto인데 flex만 쓸 땐 auto가 아니라 0이 됨
  - :star: `flex-grow` - Item의 너비 증가(grow) 비율 설정
    * 각각의 아이템이 너비가 증가할 수 있는 상태여야 한다. 
    * == no wrap이 아니면 의미가 없다 (wrap인 경우 동작하지 않는다)
    * 
  - :x: `flex-shrink` - Item의 너비 감소(shrink) 비율 설정
    - viewport가 줄어들면 감소하는 아이템의 비율 
  - `flex-basis` - Item의 기본 너비 설정
  - ``align-self`` - 교차축을 기준으로 아이템을 정렬하는 방법을 설정한다
    - align-self > align-items (우선순위 더 높다)
    - stretch, start, end, center, baseline.... default값은 auto

#### 2. Flex-direction

* Main axis 기준 방향 설정
* reverse... right to left script 같은거 쓸 때 (일본어)
* justify-content
* align-content
* 



* flexbox MDN 파일



#### 3. 활용





### :three: Grid

resume



## :ballot_box_with_check: Bootstrap

### 활용방법

* 다운받아서 이용

* 

* CDN(Content Delivery(distribution) Network)

  * 컨텐츠(CSS, JS, Image, Text 등)을 효율적으로 전달하기 위해 여러 노드에 

* JS: 화면 요소들을 변경하는 것, 사용자의 반응에 response를 주는 것 

* 이건 </body> 바로 위쪽에 위치하게 둔다.

  * 화면 요소를 읽기도 전에 script를 읽는 것을 방지하기 위해

  <script src="https://cdn.jsdelivr.net/npm/bootstrap05.1.3/dist/is/bootstrap"

* :star: m-3 = rem1 = 16px

### :star: bootstrap grid system

* :star: container, rows, column
* container는 부트스트랩의 가장 기본적 class (class="container")
  * container
    * 반응형
  * container-fluid
    * width를 100%로 지정하는 것
    * 
  * container-{BP}
* container를 만들고, row를 만든 후에 column은 row에 들어가는 각각의 컨텐츠를 의미한다
* column은 아무런 조건을 걸지 않음녀 블록 요소처럼 한줄을 차지한다. 
* :star: 12개의 column 시스템 (약수 많음~~~)
* :star: 6개의 gridpoint
* col-A-B



## :ballot_box_with_check: Responsive Web









:star:

* 부트스트랩에서 많이 나옴
* 12!!!!