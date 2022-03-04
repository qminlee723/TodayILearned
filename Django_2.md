# Django 2

## :zero: OVERVIEW

1. Namespace
2. Static files



## :one: Namespace

### 1. Namespace

* 문제 발생

  * articles 앱의 index페이지에서 두번 째 앱 pages의 index로 이동하는 하이퍼링크를 클릭 시 현재 페이지로 이동됨

    * URL namespace

  * pages앱 index url로 이동해도 articles 앱의 index 페이지가 출력됨

    * template namespace

    * 왜냐면 `settings` > `INSTALLED_APPS = []` 안에 `articles`가 `pages`보다 먼저 등록되어있음

      <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304094354451.png" alt="image-20220304094354451" style="zoom:67%;" />

  * 예시: 

    articles>templates>index와 pages>templates>index와 이름이 같아서 Django가 구분을 못하는 상황

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304093917562.png" alt="image-20220304093917562" style="zoom:50%;" />

    ![image-20220304094039860](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304094039860.png)

    ![image-20220304094126905](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304094126905.png)

    

    

* Namespace(이름공간)

  * 객체를 구분할 수 있는 범위를 나타내는 말로, 일반적으로 하나의 이름 공간에서는 하나의 이름이 단 하나의 객체만을 가리키게 된다
  * 프로그래밍을 하다 보면, 모든 변수명과 함수명 등 이들 모두를 겹치지 않게 정의 하는 것은 매우 어려운 일
  * 그래서 django에서는
    * 서로 다는 app의 다른 이름을 가진 url name은 이름 공간을 설정해서 구분
    * template, static 등 django는 정해진 경로 하나로 모아서 보기 때문에, 중간에 폴더를 임의로 만들어 줌으로써 이름공간을 설정



### 2. URL namespace(app_name 설정)

* URL namespace를 사용하면, 서로 다른 앱에서 동일한 URL 이름을 사용하는 경우에도 이름이 지정된 URL을 고유하게 사용할 수 있음

* urls.py에 "app_name" attribute값 작성

* 참조

  * `:` 연산자를 사용하여 지정

* 예시

  * `articles` > `views`

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304095521541.png" alt="image-20220304095521541" style="zoom:67%;" />

  * `articles`>`index.html`

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304100105651.png" alt="image-20220304100105651" style="zoom:67%;" />

    * url 이후에 `'articles:name'` 써서 따로 **이름공간 설정**해줌

    * pages의 `views` , `index.html`에도 똑같이 적용

      * `app_name = 'pages'` `'pages:name'`

    * action 부분이 있다면 신경써서 바꿔주기

      ![image-20220304101935974](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304101935974.png)

  * `articles`>`views`

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304100728907.png" alt="image-20220304100728907" style="zoom:67%;" />

  * `pjtfolder` > `base.html`

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304100905745.png" alt="image-20220304100905745" style="zoom: 80%;" />

    * _nav.html을 찾을 수 없다고 에러 메시지가 뜰 것
    * 이 때, `articles/_nav.html` 을 확인해 볼 것 

    

### 3. Template namespace

* Django는 기본적으로 `app_name/templates` 경로에 있는  templates 파일만 찾을 수 있으며, `INSTALLED_APPS`에 작성한 app 순서로 template을 검색 후 렌더링함
* 그래서 임의로 templates의 폴더 구조를 `app_name/templates/app_name` 형대로 변경해 임의로 이름 공간을 생성 후 변경된 추가 경로로 수정
* 폴더 구조 변경 및 템플릿 경로 재작성





## :two: Static files

### 1. 웹 서버와 정적 파일

* 웹 서버는 특정 위치(URL)에 있는 자원(resource)을 요청(HTTP request)받아서 제공(serving)하는 응답(HTTP response)을 처리하는 것을 기본 동작으로 함
* 이는 자원과 접근 가능한 주소가 정적으로 연결된 관계
  * 예를 들어, 사진 파일은 자원이고 파일 경로는 웹 주소
* 즉, 웹 서버는 요청 받은 URL로 서버에 존재하는 정적 자원(static resource)를 제공



### 2. Static file

* 정적 파일
* 응답할 때 별도의 처리 없이 파일 내용을 그대로 보여주면 되는 파일
  * 사용자의 요청에 따라 내용이 바뀌는 것이 아니라, 요청한 것을 그대로 보여주는 파일
* 예를 들어, 웹 서버는 일반적으로 이미지, 자바스크립트 또는 CSS와 같은 미리 준비된 추가 파일(움직이지 않는)을 제공해야 함
* 파일 자체가 고정되어 있고, 서비스 중에도 추가되거나 변경되지 않고 고정되어 있음
* Django에서는 이러한 파일들을 Static File 이라고 함
  * staticfiles앱을 통해 정적 파일과 관련된 기능을 제공



### 3. Static file 구성

1. `django.contrib.staticfiles`가 settings.py > INSTALLED_APPS에 포함되었는지 확인(기본)

2. settings.py에서  STATIC_URL을 정의

3. 템플릿에서 static 템플릿 태그를 사용하여 지정된 상대경로에 대한 URL을 빌드

   ![image-20220304102448121](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304102448121.png)

4. 앱의 static 디렉토리에 정적 파일을 저장

   예) `my_app/static/my_app/example.jpg`

   

### 4. The staticfiles app

* `STATICFILES_DIRS`

  ![image-20220304103433895](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304103433895.png)

  * `app/static/` 디렉토리 경로(기본 경로)를 사용하는 것 외에 추가적인 정적 파일 경로 목록을 정의하는 리스트
  * 추가 파일 디렉토리에 대한 전체 경로를 포함하는 문자열 목록으로 작성되어야 함

* `STATIC_URL`

  ![image-20220304103419856](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304103419856.png)

  * `STATIC_ROOT`에 있는 정적 파일을 참조할 때 사용할 URL
    * 개발 단계에서는 실제 정적 파일들이 저장되어 있는 'app/static/'경로(기본 경로) 및 `STATICFILES_DIRS`에 정의된 추가 경로들을 탐색함
    * 앞뒤로 `/` 있는거 무조건 주의하기! 
      * 뒤에 있어야 되는 이유는 그 이후에 static 파일 주소가 와야되기 때문
  * 실제 파일이나 디렉토리가 아니며,  URL로만 존재
  * 비어 있지 않은 값으로 설정한다면 반드시 slash(/)로 끝나야 함

* `STATIC_ROOT`

  * `collectstatic`이 배포를 위해 정척 파일을 수집하는 디렉토리의 절대 경로
  * django 프로젝트에서 사용하는 모든 정적 파일을 한 곳에 모아 넣는 경로
  * 개발 과정에서 settings.py의 DEBUG 값이 True 로 설정되어 있으면, 해당 값은 작용되지 않음
    * `DEBUG = False` 란 배포할 때 바꾸는 것(일반인들이 debug할 일 없으므로)
    * 직접 작성하지 않으면 django 프로젝트에서는 settings.py에 작성되어 있지 않음
  * 실 서비스 환경(배포 환경)에서 django의 모든 정적 파일을 다른 웹 서버가 직접 제공하기 위함

* [참고] `collectstatic`명령어

  * STATIC_ROOT에 정적 파일을 수집(정리해서 만들어줌)

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304104027760.png" alt="image-20220304104027760" style="zoom:67%;" />



### 5. Django template tag

* `load`

  * 사용자 정의 템플릿 태그 세트를 로드(load)

    ![image-20220304105138488](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304105138488.png)

    * built-in tag가 아니므로 `{% load static %}`
    * load만 치고 엔터 하면 나옴

  * 로드하는 라이브러리, 패키지에 등록된 모든 태그와 필터를 불러옴

* `static`

  * `STATIC_ROOT`에 저장된 정적 파일에 연결

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304105607990.png" alt="image-20220304105607990" style="zoom:200%;" />

    ![image-20220304105008816](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304105008816.png)

    (예시랑 다르긴 한데.. 폴더명 따르려면 `{% static 'sample-img.jpg' %}` 가 되면 됨)

  * `extends`가 가장 위로 오게! `load`는 그 밑에 쓰자

    ![image-20220304105054459](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304105054459.png)

    

    

  

### 6. 정적 파일 사용하기

* 파일

  ![image-20220304105515093](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304105515093.png)

![image-20220304105506357](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304105506357.png)

* 스태틱 파일에 추가경로 작성하기

  * 최상단에 static이라는 폴더 확인

  ![image-20220304110029351](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304110029351.png)

  * static folder만든 후, css파일(static)만들어 줌 

    * 이 css파일을 `index.html`에 적용시킬 것임

  *  `base.html`가서 `{% block style %}`을 만들어줌

    ![image-20220304110401721](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304110401721.png)

  * `index.html`에서 block설정

    ![image-20220304110801779](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220304110801779.png)

    

