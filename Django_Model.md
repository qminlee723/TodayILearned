# Django_Model

## :zero: OVERVIEW

1. Model

2. ORM
3. Migrations
4. Database API
5. CRUD
6. Admin Site



## :one: Model

### 1. 개념

* 단일한 데이터에 대한 정보 가짐
  * 사용자가 저장하는 데이터들의 필수적인 필드들과 동작들을 포함
* 저장된 데이터베이스의 구조(layout)
* :star: Django는 model을 통해 데이터에 접속하고 관리
* 일반적으로 각각의 model은 하나의 데이터베이스 테이블에 매핑 됨



### 2. 하위 개념

* 데이터베이스(DB)

  * 체계화된 데이터의 모임

* 쿼리(Query)

  * 데이터를 조회하기 위한 명령어
  * 조건에 맞는 데이터를 추출하거나 조작하는 명령어
  * "Query를 날린다" > DB를 조작한다

* 스키마(Schema)

  * 데이터베이스에서 자료의 구조, 표현방법, 관계 등을 정의한 구조(structure)

* 테이블(Table)

  * 열(column): 필드(field) or 속성
  * 행(row): 레코드(record) or 튜플

  

### 3. 데이터베이스의 기본 구조

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308113326237.png" alt="image-20220308113326237" style="zoom: 67%;" />

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308113349774.png" alt="image-20220308113349774" style="zoom:50%;" />

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308113407031.png" alt="image-20220308113407031" style="zoom:50%;" />



<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308113424983.png" alt="image-20220308113424983" style="zoom:50%;" />



### 4. 정리

* 웹 어플리케이션의 데이터를 구조화하고 조작하기 위한 도구

  



## :two: ORM

### 1. 개념

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308113636961.png" alt="image-20220308113636961" style="zoom:50%;" />

* Object-Relational-Mapping

* 객체 지향 프로그래밍 언어를 사용하여 호환되지 않는 유형의 시스템 간(Django-SQL) 데이터를 변환하는 프로그래밍 기술

* OOP 프로그래밍에서 RDBMS를 연동할 때, 데이터베이스와 객체 지향 프로그래밍 언어 간의 호환되지 않는 데이터를 변환하는 프로그래밍 기법

* Django는 내장 Django ORM 사용

  

### 2. 장점 및 단점

* 장점

  * SQL을 잘 몰라도 DB 조작이 가능
  * SQL의 절차적 접근이 아닌 객체 지향적 접근으로 인한 높은 생산성

* 단점

  * ORM만으로 완전한 서비스를 구현하기 어려운 경우가 있음

  * 속도가 느리고 효율적이지 못함(현대 웹 프레임워크의 요점은 웹 개발의 속도를 높이는 것 (생산성))

    

### 3. ORM 사용목적

* DB를 객체(object)로 조작하기 위해 ORM 사용



### 4. 작성

#### 1) 기본환경 세팅

```bash
```

#### 2) models.py 작성



![image-20220308101939167](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308101939167.png)

* 각 모델은 django.models.Model 클래스의 서브 클래스로 표현됨

  * django.db.models 모듈의 Model 클래스를 상속받음

* mdoels 모듈을 통해 어떠한 타입의 DB 컬럼을 정의할 것인지 정의

  * title, content는 모델의 필드를 나타냄
  * 각 필드는 클래스 속성으로 지정되어 있으며, 각 속성은 각 데이터베이스의 열에 매핑

  

#### 3) Field Types

* `CharField(max_length=00)`
  * max_length 필수
  * 필드의 최대 길이(문자), 데이터베이스레벨과 Django의 유효성검사(값을 검증하는 것)에서 활용
* `TextField()`
  * 길이 제한 없음(글자의 수가 많을 때 사용)
  * max_length 옵션 작성시 자동 양식 필드인 textarea 위젯에 반영은 되지만,  모델과 데이터베이스 수준에는 적용되지 않음
* `models.DateTimeField`
  * auto_now_add
  * auto_now
  * DateTimeField가 아닌 DateField의 optinos를 확인한 이유
    * DateTimeField는 Datefield와 동일한 추가 인자(extra argument)를 사용함
    * DateTimeField는 Datefiled의 서브 클래스

* 참고

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308101645717.png" alt="image-20220308101645717" style="zoom:50%;" />

  *reference: https://docs.djangoproject.com/en/4.0/ref/models/fields/*



#### 4) Field options

* `auto_now_add`
  * 최초 생성 일자
  * Django ORM이 최초 insert(테이블에 데이터 입력)시에만 현재 날짜와 시간으로 갱신(테이블에 어떤 값을 최초로 넣을 때)
* `auto_now`
  * 최초 수정 일자
  * Django ORM이 save할 때마다, 현재 날짜와 시간으로 갱신

* `null`

  * 파이썬의 none과 유사

  * Default는 False. 

  * null=True이면 없는 값도 들어갈 수 있다는 것
    * If True, Django will store empty values as NULL in the database

* 참고

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308101613530.png" alt="image-20220308101613530" style="zoom:50%;" />





## :three: Migration

### 1. 개념

* Django가 model에 생긴 변화를 반영하는 방법

* 모델이 변경된 것에 대한 히스토리

* Migration 실행 및 DB 스키마를 다루기 위한 몇가지 명령어

  ```bash
  makemigrations
  migrate
  sqlmigrate
  showmigrations
  ```

* 반드시 기억해야 할 migration 3단계

  1. `models.py` : model 변경사항 발생 시
  2. `$ python manage.py makemigrations` : migrations 파일 생성
  3. `$ python manage.py migrate` : DB반영(model과 DB의 동기화)



### 2. 모델 조작(생성, 수정, 삭제)

* Migration 생성: `makemigrations`

  ```bash
  $ python manage.py makemigrations
  ```

  * `migrations` 폴더 안에 `0001_initial.py` 와 같은 파일이 생성됨
  * model을 변경한 것에 기반한 새로운 migration(like 설계도)을 만들 때 사용

  ​	<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308102943130.png" alt="image-20220308102943130" style="zoom:50%;" />

  

* Migration 반영(적용): `migrate`

  ```bash
  $ python manage.py migrate
  ```

  * 마이그레이션을 DB에 반영하기 위해 사용

  * 설계도를 실제 DB에 반영하는 과정

  * 모델에서의 변경 사항들과 DB의 스키마가 동기화를 이룸

  * `db.sqlite3` : 데이터베이스

    ![image-20220308103533240](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308103533240.png)

  

* 각 Migration이 어떻게 sql로 변환되었는지 알고싶다면: `sqlmigrate`

  ```bash
  $ python manage.py sqlmigrate articles 0001
  ```

  * migration에 대한 SQL 구문을 보기 위해 사용
  * migration이 SQL문으로 어떻게 해석되어 동작할지 미리 확인할 수 있음

  

* 각 Migration이 실제로 데이터베이스에 반여되었는지 체크하고 싶다면: `showmigrations`

  ```bash
  $ python manage.py showmigrations
  ```

  * 프로젝트 전체의 migration상태를 확인하기 위해 사용
  * migration 파일들이 migrate 됐는지, 안됐는지 여부를 확인할 수 있음

  

* 모델 조작후(DateTimeField 넣어줌) migration 생성 및 반영과정

  ![image-20220308104819909](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308104819909.png)

  * migrate 생성

    ![image-20220308105727213](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308105727213.png)

    

    ![image-20220308105848036](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308105848036.png)

    ​		*`migration` 폴더 내에 `0002_auto_20220308_...` 하는 py파일 생성됨*

    

    

  * 반영

    ![image-20220308105802462](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308105802462.png)

  * 시각화: 이런식으로 table을 생성해 준 것

    | id   | title | content | created_at | updated_at |
    | ---- | ----- | ------- | ---------- | ---------- |
    |      |       |         |            |            |



## :four: DB API





## :five: CRUD

### 3. CRUD

#### 0) Shell 설치

* Django로 켠 shell > django 의 모든 기능들 사용가능

* 설치

  * `pip install django_extensions==3.1.5`

  * `pip install ipython`

  * `INSTALLED_APPS` 에 `django_extensions`추가

    * `ipython`은 안 넣어줘도 됨. 

    ![image-20220308132012335](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308132012335.png)

* `pip freeze > requirements.txt`

* 사용

  ```bash
  $ python manage.py shell
  
  $ python manage.py shell_plus # 가독성이 좋음 # django_extensions 설치해야 함
  ```

  

  

#### 1) CREATE

* **모델에서 데이터 가져오기**

  ![image-20220308131250570](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308131250570.png)

  ```bash
  $ python manage.py shell
  >>> from articles.models import Article # articles.models 파일 안에서 Article을 import해온다
  >>> Article.objects.all()	# 해당 class Article의 모든 객체들을 가져온다
  ```

  ```bash
  <QuerySet []>	# 데이터가 없으므로, 빈 리스트(QuerySet)을 반환
  				# 쉬운 이해: 빈 row를 생성한거
  ```

  

* **데이터 추가하기(인스턴스를 만들고, save)**

  ```bash
  # 만든 row에다가 내용을 넣어보자
  
  >>> article = Article()
  >>> article.title = "첫번째 글"
  >>> article.content = "푸틴아 정신차려"
  >>> article.save()
  ```

  

  * 추가한 데이터 확인

    ```bash
    >>> Article.objects.all()
    <QuerySet [<Article: Article object (1)>]>
    >>> article = Article.objects.all()[0]
    >>> article.title
    '첫번째 글' # 출력됨
    >>> article.content
    '푸틴아 정신차려' # 출력됨
    ```

    ![image-20220308111934133](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308111934133.png)

  

* **데이터 한꺼번에 추가하기(Keyword인자를 넘기는 방식, save)**

  ```bash
  >>> article = Article(title="두번째 글", content="점심 뭐 먹지?")
  >>> article.save()
  ```

  

* **save 없이 데이터 추가하기(Create 이용)**

  ```bash
  >>> Article.objects.create(title="세번째 글", content="살 빼야하는데?")  
  <Article: Article object (3)>
  ```

  

#### 2) READ

* `python manage.py shell_plus`

*  모델을 찾아서  import를 쫙 해줌

  ![image-20220308132445994](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308132445994.png)

  * QuerySet에 타이틀이 보이게 하고 싶다면 `models.py` `Article` 클래스 **안**에 `__str__` 을 정의해준다

    ![image-20220308134555532](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308134555532.png)

* 

![image-20220308133321232](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308133321232.png)

![image-20220308133339752](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308133339752.png)







![image-20220308133524098](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308133524098.png)

![image-20220308133605304](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308133605304.png)

get은 한가지만 반환한다 -> 따라서 제목이나 내용보다는 id를 자주 사용한다

![image-20220308133743688](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308133743688.png)

pk는 뭔가요? - 장고 내부적으로 id라는 값에 pk라는 별명을 붙여준다







* filter

  * title이 "첫번째 글"인 모든 Article을 호출하고 싶을 때

  ![image-20220308134051368](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308134051368.png)

  * ex) 어떠한 field가 정수라면, 1보다 크면 가져와, 3보다 크면 가져와... 등등 다양한 필터들이 있음

  * 참고: https://docs.djangoproject.com/en/3.2/ref/models/querysets/

  * contains

    ![image-20220308134702847](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308134702847.png)

  * in 

  * isstartwith

  * 



#### 3) Update

![image-20220308140838419](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308140838419.png)



#### 4) Delete

![image-20220308140910219](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308140910219.png)







## :six: Admin Site

### 1. Admin Site 활용하기

* Django에서 제공하는 Admin Site  들어가기

  ``` bash
  $ python manage.py runserver
  
  http://127.0.0.1:8000/admin
  ```

* Admin Site 로그인하기

  * username, password 설정

  ```bash
  $ python manage.py createsuperuser
  Username (leave blank to use 'gyumin'): gyumin
  Email address: gyumin@test.com       
  Password:						# password라서 화면에는 안 뜨지만 키보드 눌리고 있는 것임	#dlrbals12
  Password (again): 				# 너무 짧거나, 숫자로만 구성되어 있거나 하면 warning
  Superuser created successfully.
  ```

  * `articles/` > `admin.py`에 편집

    * ​	*`.models` 쩜은 장고에서 권장하는 포맷*

      ![image-20220308142005828](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308142005828.png)

  * http://127.0.0.1:8000/admin 에서 로그인

    ![image-20220308142152188](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308142152188.png)

  

  * 로그인 하면 아래 처럼  Django가 제공하는 UI 나타남. 여기서 방금까지 생성했던 데이터를 시각적으로 볼 수 있음

    * 기본 페이지

      <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308142315688.png" alt="image-20220308142315688" style="zoom:80%;" />

    * Articles안에 들어가면 데이터들을 눈으로 볼 수 있다

      <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308142451268.png" alt="image-20220308142451268" style="zoom:80%;" />

    * 직접 delete 및 edit 가능, add 도 가능

      | Edit & Delete                                                | Add                                                          |
      | ------------------------------------------------------------ | ------------------------------------------------------------ |
      | <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308142431608.png" alt="image-20220308142431608" style="zoom: 67%;" /> | <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308142401062.png" alt="image-20220308142401062" style="zoom: 67%;" /> |

      



















1. 먼저 articles 폴더 안에 urls.py 만들어준다

   * from . import views 하기
   * urlpatterns 채워준다

2. views에 index함수 설정

   * index 함수 설정해준다

3. templates/ > articles/ > `index.html`생성

   * 샌드위치 모양

4. crud 프로젝트의 urls.py 업데이트 해준다

   ![image-20220308143922314](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308143922314.png)

5. base.html적용하려면

   ![image-20220308144951873](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308144951873.png)

   







##### 실습



![image-20220308150700631](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308150700631.png)



1. 모델을 이용해서 모든 데이터를 가져온다: `views.py`

   ![image-20220308152943494](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308152943494.png)

   

2. 가져온 데이터를 템플릿으로 넘긴다: `index.html`

   ![image-20220308153401061](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308153401061.png)

   

3. 템플릿에서 데이터를 보여준다

   ![image-20220308153633724](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308153633724.png)

4. 걍 참고: `base.html`

![image-20220308153453914](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308153453914.png)



5. 글을 써 봅시당

   * `urls.py` 에 `new` 포함해주기
   * `views.py`에 `new` 정의해주기
   * `new.html`생성해주기

6. form

   * `form` 사용해서 Title과 Content 인풋박스를 만들어준다.

   * `textarea`

     ![image-20220308155106225](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308155106225.png)

     

     * textarea 쓰니까 input 지워주자

   * 이렇게 나옵니당

     ![image-20220308155138406](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308155138406.png)

   * url 다시 설정

     * <a href="/articles/index/"></a> 해 주고 싶지 않아서

     * `articles/` 내 `urls.py`에 `app_name`과 `name=""` 설정을 해준다

       ![image-20220308155257039](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308155257039.png)

     * `new.html` <a></a>태그 다시 설정

       ![image-20220308155404332](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308155404332.png)

     * `index.html` 에서도 태그 다시 설정

       <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308155722892.png" alt="image-20220308155722892" style="zoom:80%;" />

       * 어 근데 나중에 별명을 create > new로 바꿔줌 필기는 알아서 바꾸기
       * ![image-20220308160801068](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308160801068.png)
       * ![image-20220308160830478](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308160830478.png)
       * 

   * 글쓰기 기능 구현헤ㅐ보지ㅏ

     * 제출한 뒤에 데이터가 가는 곳을 만들어 주는 것

     * `urls`, `views.py` 에 새로 만듬

     * ![image-20220308161117574](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308161117574.png)

     * `new.html`에서 보내줄 곳 action에 추가해주기

       ![image-20220308161418282](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308161418282.png)

     * 주소창이 달라진 것을 볼 수 있다

     * content에 dddd 쓰고 제출한거임

       ![image-20220308161540704](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308161540704.png)

       

       * `views.py` 에서 title과 content 가져오는 함수 써주기

       * 대, 소문자 확인 잘 하기!

         ![image-20220308161813210](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308161813210.png)

         

         runserver해보면 title 제목데이터 content내용데이터 나옴

         ![image-20220308161652454](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308161652454.png)

       * ![image-20220308161740694](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308161740694.png)



* DB에 데이터 저장하기

  ![image-20220308162643502](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308162643502.png)

  ![image-20220308162655506](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308162655506.png)

  분홍: 모델에 있는 필드명

  초록: 입력된 데이터 변수

* 이 작업 이후, new에 글을 쓰면, index에 이렇게 추가됨

  * 글번호 5가 추가된것임

  ![image-20220308162935768](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308162935768.png)

* 최신 글이 가장 위로 올라오게 하려면?

  * `views.py` 조작

    1. 데이터를 가져온 다음에 바꾸는 방법

    ![image-20220308163147927](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308163147927.png)

    2. 처음부터 DB에서 가져올 때 순서를 지정하는 방법

       * pk: 오름차순
       * -pk: 내림차순

       

       ![image-20220308163607849](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308163607849.png)

    3. 내가 쓴 내용이 url에 들어가지 않게 하고 싶다면:?

       ![image-20220308163800402](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308163800402.png)

       * GET method(R only: Read)
         * 기본값, 서버 리소스를 요청할 때
         * 내용에 URL에 Query String을 포함해서 
       * POST method(CUD: Create, Update, Delete)
         * 리소스를 생성, 수정, 삭제 할 때 
         * 내용을 Body 안 쪽에 숨겨서 보낸다.

    
