1. DTL

   - built-in template system

2. DTL syntax

   * variables, tags, comments, filters

3. 부모템플릿

   * TEMPLATES = [ { 

     'DIRS': [BASE_DIR / 'templates',],

     }]

4. HTML 'input' element

   - GET 방식에서는 URL이 `?key=value&key=value`
   - `http://127.0.0.1:8000/create/?title=안녕하세요&content=반갑습니다&my-site=파이팅`

5. HTTP

   - Hyper Text Transfer Protocol
   - HTTP request method: GET POST PUT DELETE
   - GET
     - Query String Parameters를 통해 전송
   - POST
     - body를 통해 전송

6. Variable Routing

   - URL 주소를 변수로 사용하여 동적으로 주소를 만드는 것

     ![image-20220321063408716](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321063408716.png)

7. URL mapping

   - 각 app 에 url.py 작성하는 것

8. 명시적 상대경로

   - `from .models import Article`

9. Namespace

   - template namespace

   - url namespace

     - `url` 파일에

       `app_name: 'articles'` 써주기

     - `html`파일에

       <a href="{% url 'app_name:index' %}"></a>

     - `views`파일에

       `return render(request, 'articles/index', context)`

       

   - 객체를 구분할 수 있는 범위르 ㄹ나타냄. 일반적으로 하나의 이름 공간은 하나의 이름이 단 하나의 객체만을 가리킴

10. static file

    - `my_app/static/my_app/example.jpg`

    - ```html
      {% load static %}
      
      <img src="{% static 'my_app/image.jpg' %}">
      ```

    - Static URL: `/static/`

    - [BASE_DIR / 'static',] 이거 해놓으면 my_app 없어도됨.

    - collectstatic은 STATICROOT에 정적 파일을 폴더별로 정리

11. Model

    - 모델은 데이터 구조를 정의하고 데이터베이스의 기록을 관리하는 것

12. Query

    - 데이터를 조회하기 위한 명령어

13. ORM(Object relational Mapping)

    - 객체 지향 프로그래밍 언어를 사용해서 SQL과 장고 간 데이터를 변환하는 프로그래밍 기술
    - DB를 객체로 조작하기 위해서 ORM사용

14. 명령어

    ``` bash
    $ python -m venv venv
    $ django-admin startproject firstpjt .
    $ python manage.py runserver
    $ python manage.py startapp articles
    # settings.py > INSTALLED_APPS=[]에 추가
    $ source venv\Scripts\activate
    $ pip install -r requirements.txt
    $ touch .gitignore
    ```

15. models.py

    ```python
    class Article(models.Model):
        title = models.CharField(max_length=10)
        content = models.TextField()
        created_at = models.DateTimeField(auto_now_add=True)
        updated_ate = modesl.DateTimeField(auto_now=True)
    ```

16. migrations

    ```bash
    makemigrations
    # 모델을 변경한 것에 기반한 새로운 migration을 만들 때 사용
    migrate
    sqlmigrate app_name 0001
    showmigrations
    ```

17. DB API

    - DB를 조작하기 위한 도구
    - `Article.objects.all()`
    - class, manager, queryset api

18. Create

    ```bash
    #1
    article = Article()
    article.title = '첫번째 글'
    article.content = '첫번째 내용'
    article.save()
    
    #2
    article = Article(title="두번째 글", content="점심 뭐 먹지?")
    article.save()
    
    #3
    Article.objects.create(title='세번째 글', content='세번째 내용')
    ```

19. Read

    - all, filter: 새 쿼리셋 반환

    - get: 새 쿼리셋 반환 안함

    - `__str__`

      ```python
      def __str__(self):
          return self.title
      ```

    - Fieldlookup

      * `Article.objects.filter(pk__gt=2)`
      * `Article.objects.filter(content__contains='ja')`

20. Update

    ```bash
    article = Article.objects.get(pk=1)
    article.title = "바꾼 제목"
    article.save()
    ```

21. Delete

    ```bash
    article.delete()
    ```

22. Admin site

    ```bash
    # 로그인하기
    $ python manage.py createsuperuser
    ```

    ```python
    # 등록하기(models.py)
    from .models import Article
    
    admin.site.register(Article)
    ```

23. Order_by

    ```python
    Article.objects.all()[::-1]
    Article.objects.order_by('-pk')
    ```

24. csfr

    ```html
    {% csfr_token %}
    ```

    

25. GET vs POST

    * :star: **GET method(**R only: Read)

      * 기본값, 서버 리소스를 요청할 때
      * 내용에 URL에 Query String을 포함해서 
      * DB에 변화를 주지 않음

    * **:star: POST method**(CUD: Create, Update, Delete)
      * 리소스를 생성, 수정, 삭제 할 때 
      * 내용을 Body 안 쪽에 숨겨서 보낸다.
      * 서버에 변경사항을 만듦

    