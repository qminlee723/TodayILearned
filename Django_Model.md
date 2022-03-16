

# Django_Model

## :zero: OVERVIEW

1. **Model**

2. **ORM**
3. **Migrations**
4. **Database API**
5. **CRUD**
6. **Admin Site**



## :one: Model

### 1. 개념

* 단일한 데이터에 대한 정보 가짐
  * 사용자가 저장하는 데이터들의 필수적인 필드들과 동작들을 포함
* 저장된 데이터베이스의 구조(layout)
* Class로 정해주는 것
* :star: Django는 model을 통해 데이터에 접속하고 관리 :star:
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

* pk(Primary Key)
  * 자동생성된다



### 3. 데이터베이스의 기본 구조

<img src="images\image-20220308113326237.png" alt="image-20220308113326237" style="zoom: 67%;" />

<img src="images\image-20220308113349774.png" alt="image-20220308113349774" style="zoom:50%;" />

<img src="images\image-20220308113407031.png" alt="image-20220308113407031" style="zoom:50%;" />



<img src="images\image-20220308113424983.png" alt="image-20220308113424983" style="zoom:50%;" />



### 4. 정리

* 웹 어플리케이션의 데이터를 구조화하고 조작하기 위한 도구 - CRUD로 함

  



## :two: ORM

### 1. 개념

<img src="images\image-20220308113636961.png" alt="image-20220308113636961" style="zoom:50%;" />

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
$ python -m venv venv
$ django-admin startproject firstpjt .
$ python manage.py runserver
$ python manage.py startapp articles
# settings.py > INSTALLED_APPS=[]에 추가
$ source venv\Scripts\activate
$ pip install -r requirements.txt
$ touch .gitignore
```

#### 2) models.py 작성



![image-20220308101939167](images\image-20220308101939167.png)

* 각 모델은 django.models.Model 클래스의 서브 클래스로 표현됨

  * django.db.models 모듈의 Model 클래스를 상속받음

* models 모듈을 통해 어떠한 타입의 DB 컬럼을 정의할 것인지 정의

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

  <img src="images\image-20220308101645717.png" alt="image-20220308101645717" style="zoom:50%;" />

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

  <img src="images\image-20220308101613530.png" alt="image-20220308101613530" style="zoom:50%;" />





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

* **Migration 생성**: `makemigrations`

  ```bash
  $ python manage.py makemigrations
  ```

  * `migrations` 폴더 안에 `0001_initial.py` 와 같은 파일이 생성됨

    <img src="images\image-20220308212318555.png" alt="image-20220308212318555" style="zoom:80%;" />

  * model을 변경한 것에 기반한 새로운 migration(like 설계도)을 만들 때 사용

    <img src="images\image-20220308102943130.png" alt="image-20220308102943130"  />

  

* **Migration 반영(적용)**: `migrate`

  ```bash
  $ python manage.py migrate
  ```

  * 마이그레이션을 DB에 반영하기 위해 사용

  * 설계도를 실제 DB에 반영하는 과정

  * 모델에서의 변경 사항들과 DB의 스키마가 동기화를 이룸

  * `db.sqlite3` : 데이터베이스

    ![image-20220308103533240](images\image-20220308103533240.png)

  

* **각 Migration이 어떻게 sql로 변환되었는지 알고싶다면**: `sqlmigrate`

  ```bash
  $ python manage.py sqlmigrate articles 0001
  ```

  * `articles` 는 app name
  * migration에 대한 SQL 구문을 보기 위해 사용
  * migration이 SQL문으로 어떻게 해석되어 동작할지 미리 확인할 수 있음

  

* **각 Migration이 실제로 데이터베이스에 반영되었는지 체크하고 싶다면**: `showmigrations`

  ```bash
  $ python manage.py showmigrations
  ```

  * 프로젝트 전체의 migration상태를 확인하기 위해 사용

  * migration 파일들이 migrate 됐는지, 안됐는지 여부를 확인할 수 있음

    * [X]표시 된게 migrate됐다는 것

    ![image-20220308212620773](images\image-20220308212620773.png)

  

* **모델 조작후(속성 추가 created_at, updated_at) migration 생성 및 반영과정**

  ![image-20220308104819909](images\image-20220308104819909.png)

  * migrate 생성

    ![image-20220308105727213](images\image-20220308105727213.png)

    

    ![image-20220308105848036](images\image-20220308105848036.png)

    ​		*`migration` 폴더 내에 `0002_auto_20220308_...` 하는 py파일 생성됨*

    

    

  * 반영

    ![image-20220308105802462](images\image-20220308105802462.png)

  * 시각화: 이런식으로 table을 생성해 준 것

    | id   | title | content | created_at | updated_at |
    | ---- | ----- | ------- | ---------- | ---------- |
    |      |       |         |            |            |



## :four: DB API

### 1. 개념

* DB를 조작하기 위한 도구
* Django가 기본적으로 ORM을 제공함에 따른 것으로 DB를 편하게 조작할 수 있도록 도움
* Model을 만들면, Django는 객체들을 만들고 읽고 수정하고 지울 수 있는 database-abstract API를 자동으로 만듦
* database-abstract API 혹은 database-access API라고도 함



### 2. 하위 개념

* `Manager`
  * Django 모델에 데이터베이스 query 작업이 제공되는 인터페이스
  * 기본적으로 모든 Django 모델 클래스에 objects라는 Manager를 추가
* `QuerySet`
  * 데이터베이스로부터 전달받은 객체 목록(리스트 같이 활용 가능. 슬라이싱 가능)
  * queryset 안의 객체는 0개, 1개, 혹은 여러 개 일 수 있음
  * 데이터베이스로부터 조회, 필터, 정렬 등을 수행할 수 있음
* Making Queries

<img src="images\image-20220308165636552.png" alt="image-20220308165636552" style="zoom:67%;" />



### 3. Django Shell

* 일반 Python shell을 통해서는 장고 프로젝트 환경에 접근할 수 없음

  * 따라서 장고 프로젝트 설정이 load 된 Python shell을 활용해 DB API 구문 테스트 진행

  * Django로 켠 shell > django 의 모든 기능들 사용가능
  * `Django-extensions`라이브러리 기능 중 하나인`shell_plus` 를 사용(더 많은 기능)

* 설치방법

  * `pip install django_extensions==3.1.5`

  * `pip install ipython` # 필수 아님 # 가독성

  * `settings.py` > `INSTALLED_APPS` 에 `django_extensions`추가

    * `ipython`은 안 넣어줘도 됨. 

    ![image-20220308132012335](images\image-20220308132012335.png)

  * `pip freeze > requirements.txt`

    * requirements.txt는 사용된 패키지 목록이 나열되어있는 텍스트 파일임
    * 이러한 텍스트 파일을 생성시켜주는 명령어

    

* 사용 명령어

  ```bash
  $ python manage.py shell
  
  $ python manage.py shell_plus # 기능이 더 많음 # django_extensions 설치해야 함
  ```

  





## :five: :star: CRUD

:link: [참조: Django 공식문서](https://docs.Djangoproject.com/en/3.2/ref/models/querysets/#queryset-api-reference)



### 0. 데이터 가져오기(Making queries)

* **모델에서 데이터 가져오기**

  ![image-20220308131250570](images\image-20220308131250570.png)

  ```bash
  $ python manage.py shell
  >>> from articles.models import Article # articles.models 파일 안에서 Article을 import해온다
  >>> Article.objects.all()	# 해당 class Article의 모든 객체들을 가져온다
  ```

  ```bash
  <QuerySet []>	# 데이터가 없으므로, 빈 리스트(QuerySet)을 반환
  				# 쉬운 이해: 빈 row를 생성한거
  ```



### 1. CREATE(생성)

* **인스턴스 생성 후 인스턴스 변수 설정 및 SAVE해주는 방식으로 데이터 추가하기**

  ```bash
  # 만든 row에다가 내용을 넣어보자
  
  >>> article = Article()						# Article(class) 로부터 article(instance)
  >>> article.title = "첫번째 글"				 # 인스턴스 변수(title)에 값을 할당
  >>> article.content = "푸틴아 정신차려"	   # 인스턴스 변수(content)에 값을 할당
  >>> article.save()							#### 무조건 SAVE!
  ```

  * 추가한 데이터 확인

    ```bash
    >>> article
    <Article: Article object (1)>				# 데이터 한 개 들었다고 1 나오는 거
    >>> Article.objects.all()
    <QuerySet [<Article: Article object (1)>]> 
    
    
    # 인스턴스인 article을 활용하여 변수에 접근
    >>> article = Article.objects.all()[0]
    >>> article.title
    '첫번째 글' 
    >>> article.content
    '푸틴아 정신차려'
    >>> article.pk
    1
    ```

    ![image-20220308111934133](images\image-20220308111934133.png)

  

* **Keyword 인자를 넘기고 SAVE 해주는 방식으로 데이터 한꺼번에 추가하기**: 초기 값과 함께 인스턴스 생성

  ```bash
  >>> article = Article(title="두번째 글", content="점심 뭐 먹지?")
  >>> article.save()
  ```

  

* **Create 이용해서 SAVE 없이 데이터 추가하기**: QuerySet API - `create()` 사용

  ```bash
  >>> Article.objects.create(title="세번째 글", content="살 빼야하는데?")  
  <Article: Article object (3)>
  ```

  

* CREATE 관련 메서드

  * `save()`

    * 객체를 데이터베이스에 저장
    * 데이터 생성 시 save() 호출 전에는 객체의 ID 값이 무엇인지 알 수 없음
      * ID 값은 Django가 아니라, DB에서 계산되기 때문
    * 단순히 모델을 인스턴스화 하는 것은 DB에 영향을 미치지 않기 때문에 반드시 save()가 필요

  * `__str__`

    * 표준 파이썬 클래스의 method인 str()을 정의하여 각각의 object가 사람이 읽을 수 있는 문자열을 반환(return)하도록 할 수 있음. 
    * 반드시 shell_plus를 재시작해야 반영이된다

    

### 2. READ(읽기)

* QuerySet API method는 크게 2 가지로 분류된다
  * Methods that **return** new querysets
    * `all()` : 
    * `get()`: 
    * `filter()`
  * Methods that **do not return** querysets
* READ 관련 메서드
  * `all()`
    * 현재 QuerySet의 복사본 반환
  * `get()`
    * 주어진 lookup 매개변수와 일치하는 객체를 반환
    * 객체를 찾을 수 없으면 DoesNotExist
  * `filter()`

*  모델을 찾아서  import를 쫙 해줌

  ![image-20220308132445994](images\image-20220308132445994.png)

  * QuerySet에 타이틀이 보이게 하고 싶다면 `models.py` `Article` 클래스 **안**에 `__str__` 을 정의해준다

    ![image-20220308134555532](images\image-20220308134555532.png)

* 

![image-20220308133321232](images\image-20220308133321232.png)

![image-20220308133339752](images\image-20220308133339752.png)







![image-20220308133524098](images\image-20220308133524098.png)

![image-20220308133605304](images\image-20220308133605304.png)

get은 한가지만 반환한다 -> 따라서 제목이나 내용보다는 id를 자주 사용한다

![image-20220308133743688](images\image-20220308133743688.png)

pk는 뭔가요? - 장고 내부적으로 id라는 값에 pk라는 별명을 붙여준다







* filter

  * title이 "첫번째 글"인 모든 Article을 호출하고 싶을 때

  ![image-20220308134051368](images\image-20220308134051368.png)

  * ex) 어떠한 field가 정수라면, 1보다 크면 가져와, 3보다 크면 가져와... 등등 다양한 필터들이 있음

  * 조건과 일치하는 모든 데이터를 가져옴

  * 참고: https://docs.djangoproject.com/en/3.2/ref/models/querysets/

  * Field lookups

    * 조회 시 특정 검색 조건을 지정
    *  QuerySet 메서드 `filter()`, `exclude()` 및 `get()`에 대한 키워드 인수로 지정
    * 예시
      * `Article.objects.filter(pk__gt=2)`
      * `Article.objects.filter(content__contains='ja')`

  * contains (속성값 쓰고 던더 contains..)

    ![image-20220308134702847](images\image-20220308134702847.png)

  * in 

  * isstartwith

  * 



### 3. UPDATE(갱신)

* article 인스턴스 객체의 인스턴스 변수 값을 변경 후 저장
  * `article.title = "네번째 글"` 처럼 인스턴스 객체에 다른 변수를 할당

![image-20220308140838419](images\image-20220308140838419.png)



### 4. DELETE(삭제)

* QuerySet의 모든 행에 대해 SQL 삭제 쿼리를 수행하고, 삭제된 객체 수와 객체 유형당 삭제 수가 포함된 딕셔너리를 반환
  * `article.delete()` 

![image-20220308140910219](images\image-20220308140910219.png)



* * 



## :six: Admin Site

### 1. 개념

* Automatic admin interface
* 

### 2. Admin Site 활용하기

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

      ![image-20220308142005828](images\image-20220308142005828.png)

  * http://127.0.0.1:8000/admin 에서 로그인

    ![image-20220308142152188](images\image-20220308142152188.png)

  

  * 로그인 하면 아래 처럼  Django가 제공하는 UI 나타남. 여기서 방금까지 생성했던 데이터를 시각적으로 볼 수 있음

    * 기본 페이지

      <img src="images\image-20220308142315688.png" alt="image-20220308142315688" style="zoom:80%;" />

    * Articles안에 들어가면 데이터들을 눈으로 볼 수 있다

      <img src="images\image-20220308142451268.png" alt="image-20220308142451268" style="zoom:80%;" />

    * 직접 delete 및 edit 가능, add 도 가능

      | Edit & Delete                                                | Add                                                          |
      | ------------------------------------------------------------ | ------------------------------------------------------------ |
      | <img src="images\image-20220308142431608.png" alt="image-20220308142431608" style="zoom: 67%;" /> | <img src="images\image-20220308142401062.png" alt="image-20220308142401062" style="zoom: 67%;" /> |

      









1. 먼저 articles 폴더 안에 urls.py 만들어준다

   * from . import views 하기
   * urlpatterns 채워준다

2. views에 index함수 설정

   * index 함수 설정해준다

3. templates/ > articles/ > `index.html`생성

   * 샌드위치 모양

4. crud 프로젝트의 urls.py 업데이트 해준다

   ![image-20220308143922314](images\image-20220308143922314.png)

5. base.html적용하려면

   ![image-20220308144951873](images\image-20220308144951873.png)

   







##### 실습



![image-20220308150700631](images\image-20220308150700631.png)



1. 모델을 이용해서 모든 데이터를 가져온다: `views.py`

   ![image-20220308152943494](images\image-20220308152943494.png)

   

2. 가져온 데이터를 템플릿으로 넘긴다: `index.html`

   ![image-20220308153401061](images\image-20220308153401061.png)

   

3. 템플릿에서 데이터를 보여준다

   ![image-20220308153633724](images\image-20220308153633724.png)

4. 걍 참고: `base.html`

![image-20220308153453914](images\image-20220308153453914.png)



5. 글을 써 봅시당

   * `urls.py` 에 `new` 포함해주기
   * `views.py`에 `new` 정의해주기
   * `new.html`생성해주기

6. form

   * `form` 사용해서 Title과 Content 인풋박스를 만들어준다.

   * `textarea`

     ![image-20220308155106225](images\image-20220308155106225.png)

     

     * textarea 쓰니까 input 지워주자

   * 이렇게 나옵니당

     ![image-20220308155138406](images\image-20220308155138406.png)

   * url 다시 설정

     * <a href="/articles/index/"></a> 해 주고 싶지 않아서

     * `articles/` 내 `urls.py`에 `app_name`과 `name=""` 설정을 해준다

       ![image-20220308155257039](images\image-20220308155257039.png)

     * `new.html` <a></a>태그 다시 설정

       ![image-20220308155404332](images\image-20220308155404332.png)

     * `index.html` 에서도 태그 다시 설정

       <img src="images\image-20220308155722892.png" alt="image-20220308155722892" style="zoom:80%;" />

       * 어 근데 나중에 별명을 create > new로 바꿔줌 필기는 알아서 바꾸기
       * ![image-20220308160801068](images\image-20220308160801068.png)
       * ![image-20220308160830478](images\image-20220308160830478.png)
       * 

   * 글쓰기 기능 구현헤ㅐ보지ㅏ

     * 제출한 뒤에 데이터가 가는 곳을 만들어 주는 것

     * `urls`, `views.py` 에 새로 만듬

     * ![image-20220308161117574](images\image-20220308161117574.png)

     * `new.html`에서 보내줄 곳 action에 추가해주기

       ![image-20220308161418282](images\image-20220308161418282.png)

     * 주소창이 달라진 것을 볼 수 있다

     * content에 dddd 쓰고 제출한거임

       ![image-20220308161540704](images\image-20220308161540704.png)

       

       * `views.py` 에서 title과 content 가져오는 함수 써주기

       * 대, 소문자 확인 잘 하기!

         * title이라는 데이터를 가지고 올 때 쓰는 get
         * GET은 form의 메서드

         ![image-20220308161813210](images\image-20220308161813210.png)

         

         runserver해보면 title 제목데이터 content내용데이터 나옴

         ![image-20220308161652454](images\image-20220308161652454.png)

       * ![image-20220308161740694](images\image-20220308161740694.png)



* DB에 데이터 저장하기

  * 

  ![image-20220308162643502](images\image-20220308162643502.png)

  ![image-20220308162655506](images\image-20220308162655506.png)

  분홍: 모델에 있는 필드명

  초록: 입력된 데이터 변수

* 이 작업 이후, new에 글을 쓰면, index에 이렇게 추가됨

  * 글번호 5가 추가된것임

  ![image-20220308162935768](images\image-20220308162935768.png)

* 최신 글이 가장 위로 올라오게 하려면?

  * `views.py` 조작

    1. 데이터를 가져온 다음에 바꾸는 방법

    ![image-20220308163147927](images\image-20220308163147927.png)

    2. 처음부터 DB에서 가져올 때 순서를 지정하는 방법

       * pk: 오름차순
       * -pk: 내림차순

       

       ![image-20220308163607849](images\image-20220308163607849.png)

    3. 내가 쓴 내용이 url에 들어가지 않게 하고 싶다면:? - url 에 querystring으로 

       ![image-20220308163800402](images\image-20220308163800402.png)

       * GET method(R only: Read)

         * 기본값, 서버 리소스를 요청할 때
         * 내용에 URL에 Query String을 포함해서 

       * POST method(CUD: Create, Update, Delete)

         * 리소스를 생성, 수정, 삭제 할 때 
         * 내용을 Body 안 쪽에 숨겨서 보낸다.

       * `new.html` 에서 `action`부분에 `method` 를 설정해준다

         ![image-20220308164313543](images\image-20220308164313543.png)

       * `views.py`에도 바꿔줌

         ![image-20220308165309833](images\image-20220308165309833.png)

       * 만약, 내용이 url에 포함된다면

         ![image-20220308164519410](images\image-20220308164519410.png)

         * 이렇게 조작이 가능함

         * confidential한 내용이거나, 지나치게 많은 submit이 들어오게 된다면 문제가 생길 것

         * 이를 처리 하기 위해서 CSRF token을 사용

           * CSRF(Cross Site Request Forgery) 공격 

             * 인터넷 사용자가 내 의지와는 무관하게 공격자가 의도한 행위(수정, 삭제, 등록 등)을 특정 웹사이트에 요청하게 만드는 공격

           * CSRF token

             * 공격에 대응하기 위해 나온 것

             * 간단히 말하면 암호 같은 것

             * **POST method를 쓸 때 사용**합니다

               ![image-20220308165053236](images\image-20220308165053236.png)

               ALWAYS

         * MIDDLEWARE

           * 요청이 거쳐가는 곳

           * 여기 CSRF token 관련해서 설정되어 있음

             ![image-20220308165205042](images\image-20220308165205042.png)

         * 이걸 다 완료하면 url이 안지저분하고 create/에서 멈춤

           ![image-20220308165412893](images\image-20220308165412893.png)

           

       * ?? 뭔지 모르겠는데 일단 이걸 바꾸셨음

         * 질답:

           1. create view에서 return redirect를 하는 이유는 기술적인 문제라기보다 사용자가 불편하기 때문입니다 ^^

           우리가 게시판에서 글을 쓸때, 새로운 글을 쓰고나면 글 작성이 완료되었습니다. 라는 페이지를 보고나서 다시 목록보기를 누르지않고

           바로 목록 보기로 가서 새로운 글을 확인할 수 있게 되죠?


           네 그렇게 처리하기 위함이고
    
           2. render를 사용하면 데이터가 보이지 않는이유는 
           index view를 보시면 index.html을 render 할 때, 반복할 articles 데이터를 함께 넘겨주고 있습니다.
           하지만 create 에서 render 안쪽에 템플릿 이름만 바꿔준다고해도, 함께 context로 넘겨주는 articles 데이터가 없으니 안보이게 되는거죠
           우리는 단순히 template을 바꾸는게 필요한게아니라
           아예 새로운 URL로 사용자를 가도록 하는기능이 필요한거고
           그게 바로 redirect 입니다.
    
              * 사용자의 편의성을 위해서 redirect을 써 주는 것
    
     ![image-20220308165948350](images\image-20220308165948350.png)

   * render를 사용하면 데이터가 보이지 않는 이유

   * 

   * 그래서 redirect 기능을 사용해줍시다

   * `views.py` `import redirect` 해주고, ` return`도 다시

     ![image-20220308170211306](images\image-20220308170211306.png)

   * redirect page가 완성되었으니, 작성완료 페이지 필요 없으니 `create.html` 지워준다

   * ![image-20220308170355200](images\image-20220308170355200.png)

​    



1. url

![image-20220310093740284](images\image-20220310093740284.png)

![image-20220310093723269](images\image-20220310093723269.png)



2. views

![image-20220310094244941](images\image-20220310094244941.png)





3. html - detail page

   ![image-20220310101444792](images\image-20220310101444792.png)

4. html - index page에서 글 제목 누르면 디텔ㄹ로 가게 



![image-20220310101326953](images\image-20220310101326953.png)



5. settings.py > TIME_ZONE

   ![image-20220310101756701](images\image-20220310101756701.png)

   

6. 삭제

![image-20220310103559640](images\image-20220310103559640.png)

![image-20220310103541409](images\image-20220310103541409.png)

![image-20220310103428100](images\image-20220310103428100.png)

* 이 때 엔터 누르면 글 번호 10 사라짐

![image-20220310103954164](images\image-20220310103954164.png)



* GET은 데이터를 가지고 올 때만 쓰는거고, 나머지는 POST를 사용해줍니다(수정, 삭제, 생성)
* 그래서 바꿔줘야됨 + csrf token
* ![image-20220310104630744](images\image-20220310104630744.png)
  * 터미널에서 삭제시 POST로 바뀐 걸 알 수 있음

![image-20220310104604376](images\image-20220310104604376.png)

* 이렇게 설정을 해 줘도, url을 통해서 삭제가 가능함(GET방식)

* 그래서 view.py에 다시 설정

  ![image-20220310105107991](images\image-20220310105107991.png)







* 업데이트 할 때
* url![image-20220310110456684](images\image-20220310110456684.png)
* view
* ![image-20220310110604352](images\image-20220310110604352.png)
* html
* new.html을 복붙 한 다음에 수정 해준다
* 빈 input을 원래 내용들로 채워준다
* ![image-20220310111342957](images\image-20220310111342957.png)
* 수정하기 버튼 만들기(<a></a> 왜냐면 edit에 액션 보내서 처리할 거고, 페이지로 이동할 거라서 a 태그 써줌) :question: 왜 a 태그?
* 
* ![image-20220310111606181](images\image-20220310111606181.png)





update 페이지

![image-20220310112503866](images\image-20220310112503866.png)



이걸 한번에 아래처럼 표현도 가능

![image-20220310112624909](images\image-20220310112624909.png)



![image-20220310112814315](images\image-20220310112814315.png)











***

SQLite

`ctrl + shift + p` > `SQLite: Open Database` > `db.sqlite3`

outline 밑에 `SQLITE EXPLORER`나옴

![image-20220310125246187](images\image-20220310125246187.png)

![image-20220310125445236](images\image-20220310125445236.png)



`articles_article` 은 우리가 생성한 데이터베이스. 그 밑은 장고자 자동으로 생성

저기 세모난 버튼 누르면

![image-20220310125543431](images\image-20220310125543431.png)

이렇게 시각적으로 볼 수 있음









*** form 안 써서

*** csrf token 안 써서

*** form 안에는 a 태그 안됨









![image-20220311164436085](images\image-20220311164436085.png)