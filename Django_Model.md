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

#### 3)





## :three: Migration



Model

* 

| <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308101613530.png" alt="image-20220308101613530" style="zoom:50%;" /> | <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308101645717.png" alt="image-20220308101645717" style="zoom:50%;" /> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

*reference: https://docs.djangoproject.com/en/4.0/ref/models/fields/*



* Field options
  * null
    * 파이썬의 none과 유사
    * Default는 False. 
    * null=True이면 없는 값도 들어갈 수 있다는 것
      * If True, Django will store empty values as NULL in the database
  * blank
* Field types



* 모델 조작(생성, 수정, 삭제)

  * Migration: 모델이 변경된 것에 대한 히스토리

  * Migration 생성

    ```bash
    $ python manage.py makemigrations
    ```

    `migrations` 폴더 안에 `0001_initial.py` 와 같은 파일이 생성됨

    ​	<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308102943130.png" alt="image-20220308102943130" style="zoom:50%;" />

    

  * Migration 반영(적용)

    ```bash
    $ python manage.py migrate
    ```

    * `db.sqlite3` : 데이터베이스

      ![image-20220308103533240](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308103533240.png)

  * 각 Migration이 어떻게 sql로 변환되었는지 알고싶다면

    ```bash
    $ python manage.py sqlmigrate articles 0001
    ```

  * 각 Migration이 실제로 데이터베이스에 반여되었는지 체크하고 싶다면

    ```bash
    $ python manage.py showmigrations
    ```

* `models.DateTimeField`

  * auto_now_add
  * auto_now

  ![image-20220308104819909](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220308104819909.png)

  * 모델을 조작했으면 migration을 만들고, DB에 반영해 주어야 한다

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

      

      이제 CRUD(Create, Read, Update, Delete) 

      ORM 을 사용할 것

      Model 은 뷰에서 조

      

* ORM 연습

  * django로 켠 shell > django 의 모든 기능들 사용가능
  * 모델에서 데이터 가져오기

  ```bash
  $ python manage.py shell
  >>> from articles.models import Article # articles.models 파일 안에서 Article을 import해온다
  >>> Article.objects.all()	# 해당 class Article의 모든 객체들을 가져온다
  ```

  ```bash
  <QuerySet []>	# 데이터가 없으므로, 빈 리스트(QuerySet)을 반환
  				# 쉬운 이해: 빈 row를 생성한거
  ```

  

  * 데이터 추가하기(인스턴스를 만들고, save)

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

  * 데이터 한꺼번에 추가하기(Keyword인자를 넘기는 방식, save)

  ```bash
  >>> article = Article(title="두번째 글", content="점심 뭐 먹지?")
  >>> article.save()
  ```

  

  * save 없이 데이터 추가하기(Create 이용)

  ```bash
  >>> Article.objects.create(title="세번째 글", content="살 빼야하는데?")  
  <Article: Article object (3)>
  ```

  

  
