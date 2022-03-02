# Django Basic

## :zero: OVERVIEW

1. Web Framework
2. Django Intro
3. 요청과 응답
4. Template
5. HTML Form
6. URL

:heavy_heart_exclamation: **클라이언트, 서버, 요청, 응답** :heavy_heart_exclamation:



## :one: Web Framework

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302090755215.png" alt="image-20220302090755215" style="zoom:67%;" />

### 1. Django

* A high-level Python Web framework that encourages rapid development and clean, pragmatic design.
* It takes care of much of the hassle for Web development, so you can focus on writing your app without needing to reinvent the wheel



### 2. Web(World Wide Web)

* 정적 웹 페이지(Static web page)
  * 서버에 미리 저장된 파일이 사용자에게 그대로 전달되는 웹 페이지
  * 서버가 **요청**을 받은 경우, 서버는 추가적인 처리 과정 없이 클라이언트에게 **응답**을 보냄
  * 모든 상황에서 모든 사용자에게 동일한 정보를 표시
  * HTML, CSS, JavaScrpit
  * flat page라고도 한다.
* 동적 웹 페이지(Dynamic web page)
  * 서버가 요청을 받은 경우, 서버는 추가적인 처리 과정 이후 클라이언트에게 응답을 보냄
  * 동적 페이지는 방문자와 **상호작용**하기 때문에 페이지 내용은 그때그때 다름
  * 서버 사이드 프로그램이언어(python, java, c++등)가 사용되며, 파일을 처리하고 데이터베이스와의 상호작용(수정, 삭제, 조회 등)이 이루어짐

### 3. Framework

* Framework

  * 프로그래밍에서 특정 운영 체제를 위한 응용 프로그램 표준 구조를 구현하는 클래스와 라이브러리 모임

  * 재사용할 수 있는 수많은 코드를 프레임워크로 통합합으로써 개발자가 새로운 애플리케이션을 위한 표준 코드를 다시 작성하지 않아도 같이 사용할 수 있도록 도움

  * Application Framework라고도 함

  * 개발을 하는데 필요한 개발툴, 환경 등을 제공함

* Web Framework

  * 웹 페이지를 개발하는 과정에서 겪는 어려움을 줄이는 것이 주 목적
  * 데이터베이스 연동, 템플릿 형태의 표준, 세션 관리, 코드 재사용 등의 기능을 포함
  * 동적 웹 페이지, 웹 어플리케이션, 웹 서비스 개발 보조용으로 만들어지는 Application Framework의 일종

* Framework Architecture

  * MVC Design Pattern(model-view-controller)
    * 앱이 어떤식으로 디자인 되어 있는지?
  * 소프트웨어공항에서 사용되는 디자인 패턴 중 하나
  * 사용자 인터페이스로부터 프로그램 로직을 분리하여 애플리케이션의 시각적 요소나 이면에서 실행되는 부분을 서로 영향 없이 쉽게 고칠 수 있는 애플리케이션을 만들 수 있음
  * Django = MTV pattern (명칭만 다를 뿐 기능은 동일함)

  

### 4. MTV Pattern

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302092215079.png" alt="image-20220302092215079" style="zoom:50%;" />

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302092233985.png" alt="image-20220302092233985" style="zoom:67%;" />

* Model - *database, data*
  * 응용 프로그램의 데이터 구조를 정의하고 데이터베이스의 기록을 관리(추가, 수정, 삭제)
* Template(view) -  *HTML*
  * 파일의 구조나 레이아웃을 정의
  * 실제 내용을 **보여주는 데** 사용(presentation)
* View(controller)  - *조작, 가공*
  * **HTTP 요청을 수신하고 HTTP 응답을 반환**
  * Model을 통해 요청을 충족시키는 데 필요한 데이터에 접근
  * template에게 응답의 서식 설정을 맡김



### 5. 장고를 사용해야 하는 이유

* 검증된 Python 기반 Web framework
  * Spotify, Instagram, Dropbox, Delivery Hero



## :two: Django Intro

### 1. LTS

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302094859741.png" alt="image-20220302094859741" style="zoom:67%;" />

* Long Term Support(장기 지원 버전)
* 일반적인 경우보다 장기간에 걸쳐 지원하도록 고안된 소프트웨어 버전
* 컴퓨터 소프트웨어의 제품 수명주기 관리 정책
* 배포자는 LTS 확정을 통해 장기적이고 안정적인 지원을 보장



### 2. 설치 순서

 1. 가상환경 생성 및 활성화(해당 폴더에서)

    `python -m venv venv` 

 2. django 설치

    `pip install django==3.2.12`

 3. 프로젝트 생성

    `$ django-admin startproject` firstpjt `. `

    * *여기서 '.' 은 현재 디렉토리를 의미*
    * firstpjt는 프로젝트이름
    * 쩜(.) 은 한칸 띄우고

 4. 서버 실행 로켓 확인

    `python manage.py runserver`

 5. 앱 생성

    `$ python manage.py startapp articles`

 6. 앱 등록

    settings.py > INSTALLED_APPS = [] 리스트 안에 추가

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302140216832.png" alt="image-20220302140216832" style="zoom:50%;" />

    

    

     

### 3. 프로젝트 구조

:exclamation: 볼드체로 작성된 파일만 사용할 것. 나머지는 건드리지 말 것 :exclamation:



#### firstpjt/

* \__init__.py
  * Python에게 이 디렉토리를 하나의 python package로 다루도록 지시
  * 아무것도 없고, 건들지 말자
* asgi.py (애스기)
  * Asynchronous Server Gateway Interface
  * Django애플리케이션이 비동기식 웹 서버와 연결 및 소통하는 것을 도움
  * 배포시 사용
* **settings.py**
  * 애플리케이션의 모든 설정을 포함
* **urls.py**
  * 사이트의 url과 적절한 views의 연결을 지정
* wsgi.py (위스기)
  * Web Server Gateway Interface
  * 웹서버와 연결 및 소통하는 것을 도움
  * 배포시 사용
* manage.py
  * Django 프로젝트와 다양한 방법으로 상호작용 하는 커맨드라인 유틸리티



#### articles/

* **admins.py**
  * 관리자용 페이지를 설정하는 곳
* apps.py
  * 앱의 정보가 작성된 곳
  * 사용 X
* **models.py**
  * 앱에서 사용하는 model을 정의하는 곳
* tests.py
  * 프로젝트의 테스트 코드를 작성하는 곳
  * 사용 X
* **views.py**
  * view 함수들이 정의되는 곳



### 4. 어플리케이션 생성

* 어플리케이션 생성

  * 일반적으로 어플리케이션명은 *복수형*으로 하는 것을 권장

  ```bash
  $ python manage.py startapp articles
  ```

  * vs code에 등록해야 함
    * `settings.py` > `INSTALLED_APPS` 리스트 안에 앱 이름 등록해주기
    * 생성 이후 등록!!! (otherwise 생성 안 됨)

* 서버 끄는 법: `ctrl + c`

* 등록 시 주의사항

  * 순서 꼭 지켜주세요 ( `Local apps` > `Third party apps` > `Django apps`)

    

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302102853270.png" alt="image-20220302102853270" style="zoom:50%;" />

    



### 5. Project 와 Application  관계

* Project
  * project(이하 프로젝트)는 Application(이하 앱)의 집합(collection of apps)
  * 프로젝트에는 여러 앱이 포함될 수 있음
  * 앱은 여러 프로젝트에 있을 수 있음(수업에선 안함)
* Application
  * 앱은 실제 요청을 처리하고 페이지를 보여주고 하는 등의 역할을 담당
  * 하나의 프로젝트는 여러 앱을 가짐
  * 일반적으로 앱은 하나의 역할 및 기능 단위로 작성함



## :three: 요청과 응답

### 

장고 실행하고 싶으면

`python manage.py runserver`

`https://127.0.0.1:8000/` 이 서버 주소 받고 들어가면 로켓 페이지 나옴

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302103407358.png" alt="image-20220302103407358" style="zoom: 33%;" />

`https://127.0.0.1:8000/admin` 더해주면 아래 페이지 나옴





<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302103224079.png" alt="image-20220302103224079" style="zoom:67%;" />



주소의 비밀

![image-20220302175112169](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302175112169.png)







### 1. URLs

* `urls.py` > `urlpatterns` 리스트 안에 설정가능

  * path('index/', )

* view함수는 firstpjt안에 있는게 아니라, articles하에 있음

  ![image-20220302104515310](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302104515310.png)

  * `from articles import views` 를 `urlpatterns` 위에 적어줌

* trailing comma

  ![image-20220302104420158](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302104420158.png)

  * 리스트 안에 요소가 하나 있는데도, 리스트 바깥에 콤마를 찍어줌
  * 생산성을 높이기 위해(이후에 연결시킬 때 편하라고)

* view 함수 만들어주기

  * articles/ views.py

  ![image-20220302104843902](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302104843902.png)

* 다시 url에 써주기

  ![image-20220302105109617](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302105109617.png)

  

* app/ > **templates > index.html**

  * templates라고 쓰느

  

### 2. 참고

* USE_I18N
  * Django의 번역 시스템을 활성화해야 하는지 여부를 지정
* USE_L10N
  * 데이터의 지역화 된 형식(localized formatting)을 기본적으로 활성화할지 여부를 지정
  * True 일 경우, Django는 현재 locale의 형식을 사용하여 숫자, 날짜를 표시
* USE_TZ
  * datetimes가 기본적으로 시간대를 인식하는지 여부를 지정
  * True인 경우, Django는 내부적으로 시간대 인식 날짜/시간을 사용





## :four: Template

### 1.  Django Template

* 데이터 표현을 제어하는 도구이자 표현에 관련된 로직
* 사용하는 built-in system
  * Django template language

### 2. Django Tempalte Language(DTL)

* Django template에서 사용하는 built-in template system
* 조건, 반복, 변수 치환, 필터 등의 기능 제공
* python이 HTML에 포함된 것이 아니며, 프로그래밍적 로직이 아니라 프레젠테이션을 표현하기 위한 것
* Python처럼 일부 프로그래밍 구조(if, for문 등)를 사용할 수 있지만, 이것은 해당 python코드로 실행되는 것이 아님



### 3. DTL Syntax

#### 1) 변수(Variable)

* `{{variable}}`

* render()를 사용하여 views.py에서 정의한 변수를  template 파일로 넘겨 사용하는 것

* `render(request, 'templatefile.html', {'key': 'value'})`

  * 첫 번째 인자(고정): request
  * 두 번째 인자: 템플릿 파일 이름
  * 세 번째 인자: {'key': value}와 같이 딕셔너리 형태로 넘겨주며, 여기서 정의한 key에 해당하는 문자열이 template에서 사용 가능한 변수명이 된다. optional.

* 변수명은 영어, 숫자, 밑줄의 조합으로 구성될 수 있으나, 밑줄로는 시작할 수 없음

* dot(.)를 사용하여 변수 속성에 접근가능

* 예시

  * views.py

    ![image-20220302143550096](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302143550096.png)

    

  * greeting.html

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302143500813.png" alt="image-20220302143500813" style="zoom: 50%;" />

  * urls.py

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302143608546.png" alt="image-20220302143608546" style="zoom:50%;" />

  * 만약, 변수가 많아진다면?

    * context 안에 포함

      <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302145004185.png" alt="image-20220302145004185" style="zoom: 67%;" />

    * ``{{ }}` 을 사용해서 view 안의 값을 불러올 수 있다. 

    * name은 info 안에 있으므로 `info.name`

    * foods 리스트 안의 첫번째 인자를 받아오고 싶다면 `foods.0`

      <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302144235398.png" alt="image-20220302144235398" style="zoom: 67%;" />

    * 출력

      <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302145147839.png" alt="image-20220302145147839" style="zoom:50%;" />





#### 2) 필터(Filter)

* `{{ variable|filter }}`

* 표시할 변수를 수정할 때 사용

* 60개 종류의 built-in filters 제공

* chained가 가능하며, 일부 필터는 인자를 받기도 함

  * join 필터 다음에 ', ' 로 이어질 수 있게 되어있다.

  ![image-20220302150218136](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302150218136.png)

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302150926625.png" alt="image-20220302150926625" style="zoom:50%;" />

* 예시1

  * 소문자로 바꿈

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302145102354.png" alt="image-20220302145102354" style="zoom:50%;" />

  * 출력 예시: 소문자로 바뀌어서 

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302145224333.png" alt="image-20220302145224333" style="zoom:50%;" />

* 예시2: 랜덤한 value 추천하는 웹 만들기! (순서: **url > view > html**)

  1. url

     <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302145859812.png" alt="image-20220302145859812" style="zoom:67%;" />

  2. view

     * random import해주기

     <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302150006791.png" alt="image-20220302150006791"  />

     <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302150019197.png" alt="image-20220302150019197" style="zoom: 50%;" />

     

  3. html

  

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302145723260.png" alt="image-20220302145723260" style="zoom: 67%;" />

  



#### 3) :star: Tags

* `{% tag %}`

* 출력 텍스트를 맏늘거나, 반복 또는 논리를 수행하여 제어 흐름을 만드는 등 변수보다 복잡한 일들을 수행

* 일부 태그는 시작과 종료 태그 필요

  * `{% if %}{% endif %}`

* 약 24개의 built-in template tags를 제공

* 예시

  * html에서 for 문 돌리기

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302151319660.png" alt="image-20220302151319660" style="zoom:67%;" />

  * 출력

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302151240309.png" alt="image-20220302151240309" style="zoom:67%;" />

#### 4) Comments

* 한 줄 주석: `{# #}`

* 여러 줄 주석

  ```html
  {% comment %}
  	주석
  	주석
  {% endcomment %}
  ```

* html 주석도 사용가능 `<!-- comment -->`

* Django template에서 라인의 주석을 표현하기 위해 사용

* :question: 아래처럼 유효하지 않은 템플릿 코드가 포함될 수 있음

  * `{# {% if ... %} text {% else %} #}`

* 한 줄 주석에만 사용할 수 있음(줄바꿈 허용안됨)

* 여러 줄 주석은 

### 4. 코드 작성 순서

* 데이터 흐름을 따라서 작성
  1. URL
  2. VIEW
  3. TEMPLATE



### 5. 다양한 built-in template tags and filters

* for tag

  `{{ forloop }}`

  `{{ forloop.counter }}`

  `{{ for _ in empty }}`

* if tag

  `{% if forloop.first %}`: 첫 바퀴일 때만 true`{% endif %}`

  `{% lorem %}`

  `{% lorem 4 w  %}`

* 연산

  `{{ 4.add:6 }}`

* 다양한 날짜 표현

  `{% now "DATETIME_FORMAT" %}`

  `{% now "SHORT_DATETIME_FORMAT" %}`

  `{% now "DATE_FORMAT" %}`

  `{% now "SHORT_DATE_FORMAT" %}`

  `{% now "Y년 m월 d일 (D) h:i" %}`

  `{% now "Y" as current_year %}`

  Copyright `{{ current_year }}`

  



* 장고가 최대한 파이썬과 유사하게 만들어졌으나, 파이썬처럼 구동되는거 아님. 함수() 이걸로 호출 안됨

1. URL

![image-20220302151910527](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302151910527.png)

2. VIEW

   

3. HTML





### 6. 템플릿 상속(Template inheritance)

* 템플릿 상속은 기본적으로 코드의 재사용성에 초점

* 템플리 삿ㅇ속을 사용하면 사이트의 모든 공통 요소를 포함하고, 하위 템플릿이 재정의(override)할 수 있는 블록을 정의하는 기본 'skeleton' 템플릿을 만들 수 있다.

* 부트스트랩 사용하고 싶을 때

  * 부모 클래스에 bootstrap CDN을 넣어두면, 자식 클래스는 자동으로 CDN이 적용

  

*  `{% extends ' ' %}`

  * 자식 템플릿이 부모 템플릿을 확장한다는 것을 알림
  * 반드시 템플릿 최상단에 작성되어야 함
  * ' ' 사이에 부모 템플릿의 이름이 들어가야 함

* `{% block content %} {% endblock %}`

  * 하위 템플릿에서 재지정(overridden)할 수 있는 블록을 정의

  * 즉, 하위 템플릿이 채울 수 있는 공간

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302154041239.png" alt="image-20220302154041239" style="zoom:50%;" />

* 예시

  1. settings > `TEMPLATES = []`

     * DIRS: [] 빈 리스트 안에 추가 경로를 설정해 줄 것

     <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302154255599.png" alt="image-20220302154255599" style="zoom:67%;" />

  2. 최상단에 새 `templates` 폴더 만들고 안에 base.html(부모템플릿)을 만들어줌 (그래야 가장 먼저 읽음)

     ![image-20220302154603995](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302154603995.png)

  3. 그리고 DIRS (directories)에 경로 추가

     ![image-20220302154730161](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302154730161.png)

     *객체 지향 경로시스템*

     *장고 프로젝트를 포함하고 있는 최상단의 폴더* 

     *base directory다음 템플릿 파일에도 템플릿이 있으니까 찾아*

  4. 부모 템플릿 조작

     ![image-20220302160501543](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302160501543.png)

     a. Bootstrap CDN

     b. Navbar

     c. :star: 상속 

     - `{% block content %} {% endblock content %}` (endblock  뒤 content 쓰는건 optional)
     - 대신, 상속할 자식 템플릿과 **이름은 꼭 맞춰줘야** 함!

     d. JS

  5. 자식 템플릿 조작

     ![image-20220302160052735](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302160052735.png)

     * 최상단에 `{% extends '부모템플릿.html' %} `
     * html 기본 구조 다 지우고, <body></body> 안의 내용만 남긴다.
     * 그 내용들을 `{% block content %} {% endblock %}` 사이에 넣어줌

  6. 만약 Navbar를 따로 관리하고 싶다면?

     * articles > templates 에 새로 파일을 만들어서 관리가능

     * 새로 만든 파일 `_nav.html` 에 navbar 코드를 뜯어서 붙여넣고

       <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302161310929.png" alt="image-20220302161310929" style="zoom:67%;" />

     * 부모템플릿인 `base.html`에 `{% include '_nav.html' %}` 추가해주면 더 깔끔한 코드정리 가능

       <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220302161215725.png" alt="image-20220302161215725" style="zoom: 67%;" />

     * :honey_pot: 파일 이름 앞에 언더바(_)를 쓰면: (예시에서는 `_nav_`라고 했지만.. 그냥 앞에만)

       * include 되는 템플릿이라는 것을 명시적으로 나타내는 것
       * 그냥 추천되는 분류체계! 나중에 관리가 쉬워짐!

  

### 7. Django template system (feat. Django 설계철학)

* 표현과 로직(view)을 분리
  * 템플릿 시스템은 표현을 제어하는 도구이자 표현에 관련된 로직일 뿐이라고 생각함
  * 즉, 템플릿 시스템은 이러한 기본 목표를 넘어서는 기능을 지원하지 말아야
* 중복을 배제
  * 대다수의 동적 웹사이트는 공통 header, footer, navbar 같은 공통 디자인 가짐
  * Django템플릿 시스템은 이러한 요소를 한 곳에 젖아하기 쉽게 해 중복 코드를 없애야 함
  * 이것이 템플릿 상속의 기초가 되는 철학





## :five: HTML Form



## :six: URL





