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

* Model
  * 응용 프로그램의 데이터 구조를 정의하고 데이터베이스의 기록을 관리(추가, 수정, 삭제)
* Template(view)
  * 파일의 구조나 레이아웃을 정의
  * 실제 내용을 **보여주는 데** 사용(presentation)
* View(controller) 
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



### 2. 순서

 	1. 가상환경 생성 및 활성화
 	2. django 설치
 	3. 프로젝트 생성
 	4. 서버 켜서 로켓 확인



### 3. 프로젝트 구조

:exclamation: 볼드체로 작성된 파일만 사용할 것. 나머지는 건드리지 말 것!



#### firstpjt/

* \__init__.py
  * Python에게 이 디렉토리를 하나의 python package로 다루도록 지시
  * 아무것도 없고, 건들지 말자
* asgi.py
  * Asynchronous Server Gateway Interface
  * Django애플리케이션이 비동기식 웹 서버와 연결 및 소통하는 것을 도움
  * 배포시 사용
* **settings.py**
  * 애플리케이션의 모든 설정을 포함
* **urls.py**
  * 사이트의 url과 적절한 views의 연결을 지정
* wsgi.py
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

* 서버 끄는 법: `ctrl + c`



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



## :four: Template



## :five: HTML Form



## :six: URL





