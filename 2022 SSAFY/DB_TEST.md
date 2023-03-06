## DB 01

모델: 데이터 구조를 정의하고 데이터베이스의 기록을 관리

1. 데이터베이스가 뭐게

   - 데이터와 자료가 조직적으로 구조화 되어있는 것, 즉 집합체

2. 스키마, 테이블, 열, 행, pk 설명해

   - 스키마: 자료의 구조, 표현방법, 관계 등 전반적 명세를 기술한 것
   - 테이블: 열과 행의 모델을 사용해 조직된 데이터들의 집합
   - 열: 교유한 데이터 형식이 지정됨
   - 행: 실제 데이터가 저장되는 형태
   - pk: 각 행의 고유값

3. ORM이 뭐야

   - 객체 지향 프로그래밍 언어를 사용해서 sql과 django간에 테이터를 변환하는 프로그래밍 기술

4. ORM 장점, 단점

5. **Migrations이 뭐야**

6. Migrations  명령어 + 설명 써(app이름 articles 파일번호는 0001)

   - model을 변경한 것에 기반한 새로운 마이그레이션 설계도 만드는거 

7. 추가 모델 필드 작성 후 makemigrations 진행하면 메세지가 뜨는데 이거 왜 뜨냐? 

   새로운 필드가 추가됐는데 이 때 기존행의 값을 어떻게 처리할 건지 물어보는거당

8. DB API 뭐야

   - db를 조작하기 위한 도구

9. article 전체 객체 조회

   - Article.object.all()

10. title content 만드는 세가지 방법(create) 첫번째 두번째는 save() 가 필요한 이유는?

    - 첫번째

      ```sqlite
      article = Article()
      article.title = '제목'
      article.content = '내용이다'
      article.save()
      ```

    - 두번째

      ```sqlite
      article = Article(title='두번째 제목', content='내용이라구요')
      article.save()
      ```

    - 세번째

      ```sqlite
      Article.objects.create(title='세번째 제목', title='내용!!!!!!!!')
      ```

    - save()가 필요한 이유 단순히 모델을 인스턴스화 하느 ㄴ것은 db에 영향을 미치지 않기 때문에 반드시 save()가 필요하다

11. all은 무엇을 반환해? : star:

    - 쿼리셋의 복사본
    - 쿼리셋: 전달받은 모델의 객체 목록

12. get은 무엇을 반환해?

    - 객체

13. content가 django인걸 조회해

    - Article.objects.filter(content='django')

14. title이 first인걸 조회해

    - Article.objects.filter(content='django')

15. pk가 1인걸 조회한 후에 제목을 byebye로 바꿔

    ```
    article = Article.objects.get(pk=1) 
    article.title = 'byebye' 
    article.save()
    ```

16. pk가 3인걸 조회한 후에 지우삼

    ```bash
    article = Article.objects.get(pk=3)
    article.delete()
    ```

    - 삭제된 객체 수 
    - 유형당 삭제 수가 포함된 딕셔너리 
    - articles.Article:1

17. pk가 2인 초과인걸 가져와

    ```bash
    Article.objects.get(pk__gt = 2)
    ```

18. content에 'ja'가 포함되어 있는걸 가져와

    ```python
    Article.objects.filter(content__contains='ja')
    ```

19. 게시글 정렬 순서 2개 내림차순으로 써봐 

    ```
    Article.objects.order_by('-pk')
    Article.objects.all()[::-1]
    ```

20. sqlite data type 뭐가 있게 

    * NULL, TEXT, INTEGER, REAL, BLOB

21. sqlite type affinity 뭐가 있게 + 설명

    * NULL 없고 NUMERIC 추가
    * BLOB: 입력된 그대로 정확히 저장된 데이터(별다른 타입 없이 그대로 저장)
    * NUMERIC: 나머지 4개 type에 해당하지 않는 것

22. classmates 테이블 만들고 스키마 확인하삼 name text /age int/ address text

    ```
    CREATE clasmates (name TEXT, age INT, address TEXT)
    ```

23. classmates 테이블 지워

24. classmates 테이블에 이름이 홍길동이고 나이가 23인 데이터 삽입 및 SELECT문으로 확인



## DB 02

1. 외래키가 뭐죠? 특징은

   - 관계형 데이터베이스에서 한 테이블의 필드 중 다른 테이블의 행을 식별할 수 있는 키
   - 참조하는 테이블에서 속성(field)에 해당하고, 참조되는 테이블의 기본키를 가리킴
   - 참조하는 테이블의 외래키는 참조되는 테이블 행 1개에 대응됨
   - 참조하는 테이블: N, 참조되는 테이블: 1
   - 키를 사용하여 부모 테이블의 유일한 값을 참조(참조 무결성)

2. 외래키 사용해보세요 (참조하는 model class 이름은 Article)

   ```python
   class Comment(models.Model):
       article = models.ForeignKey(Article, on_delete=models.CASCADE)
       
       def __str__(self):
           return self.content
   ```

   PROTECT, SET_NULL, SET_DEFAULT

3. 역참조: article.comment_set

   - related_name="comments"
     - 이러면 article.comments ... 이렇게 사용 가능. manager 이름변경

4. 참조: comment.article

5. save(commit=False

   * Create, but don't save the new instacne
   * 아직 데이터베이스에 저장되지 않은 인스턴스를 반환
   * 저장하기 전 객체에 대한 사용자 지정 처리 수행 시 사용

6. AUTH_USER_MODEL





## SQL 문

1. classmates라는 테이블 생성(fields: name, age, address)

2. classmates 테이블에 이름이 홍길동이고 나이가 23인 데이터 삽입 및 SELECT문으로 확인

3. classmates 테이블에 이름이 홍길동이고, 나이가 23이며 주소가 서울인 데이터 삽입(2가지

4. 이름, 나이, 주소로 구분되는 정보를 DB에 저장(랜덤한 데이터 2개 이상)

5. classmates 테이블에서 id, name  컬럼 값만 조회 :star: ORM으로 하면?

6. classmates 테이블에서 id, name  컬럼 값을 **하나**만 조회

7.  id, name 컬럼 값을 세 번째에 있는 하나만 조회하기

8. classmates 테이블에서  주소가 서울인 경우의 id, names을 조회

   ```
   ```

   

9. classmates 이블에서 age값 전체를 중복없이 조회 :star: ORM으로 하면?

   ```bash
   SELECT DISTINCT age FROM classmates;
   ```

10. classmates 테이블에 id가 5인 레코드를 삭제

    ```
    DELETE FROM classmates WHERE id=5;
    ```

11. classmates 테이블에 id가 5인 레코드를 수정(이름을 홍길동, 주소를 제주도로 바꾸자)

    ```
    UPDATE SET name='홍길동', address='제주도' FROM classmates WHERE id=5;
    ```

12. users 테이블에서 age가 30 이상인 유저의 모든 컬럼 정보를 조회

    ```
    SELECT * FROM users WHERE age >= 30;
    ```

13. users 테이블에서 age가 30 이상인 유저의 이름만 조회

    ```shell
    SELECT name FROM users WHERE age >= 30;
    ```

14. users 테이블에서 age가 30 이상**이고(AND)** 성이 '김'인 사람의 나이와 성만 조회

    ```shell
    SELECT age, last_name FROM users WHERE age >= 30 AND last_name="김";
    ```

15. 그룹의 항목 수를 가져온다(행 수)

    ```shell
    SELECT COUNT(*) FROM users;
    ```

16. 30살 이상의 사람들의 평균 나이

    ```
    SELECT AVG(age) FROM users WHERE age >= 30;
    ```

17. 계좌 잔액(balance)이 가장 높은 사람과 그 액수 조회

    ```shell
    SELECT first_name, MAX(balance) FROM users;
    ```

18. 나이가 30살 이상인 사람의 계좌 평균 잔액 조회

    ```
    SELECT AVG(balance) FROM users WHERE age>=30;
    ```

19. users 테이블에서 나이가 20대인 사람만 조회

    ```shell
    SELECT * FROM users WHERE age LIKE '2_';
    ```

20. users 테이블에서 지역 번호가 02인 사람만 조회

    ```shell
    SELECT * FROM users WHERE age LIKE '2_';
    ```

21. users 테이블에서 이름이 '준'으로 끝나는 사람만 조회

    ```shell
    SELECT * FROM users WHERE fisrt_name LIKE '%준';
    ```

22. users 테이블에서 중간 번호가 5114인 사람만 조회

23. users 에서 나이 순으로 오름차순 정렬하여 상위 10개만 조회

    ```shell
    SELECT * FROM users ORDER BY age ASC LIMIT 10;
    ```

24. 나이 순, 성 순으로 오름차순 정렬하여 상위 10개만 조회

    ```shell
    SELECT * FROM users ORDER BY age, last_name LIMIT 10;
    ```

25. 계좌 잔액 순으로 내림차순 정렬하여 해당 유저의 성과 이름을 10개만 조회

    ```shell
    SELECT last_name, first_name FROM users ORDER BY balance DESC LIMIT 10;
    ```

26. users 에서 각 성(last_name) 씨가 몇 명씩 있는지 조회

    ```shell
    SELECT last_name, COUNT(*) FROM users GROUP BY last_name;
    ```

27. column의 이름을 COUNT(*)에서 name_count로  바꾸고 싶다면

    ```shell
    SELECT last_name, COUNT(*) AS name_count FROM users GROUP BY last_name;
    ```

28. title과 content라는 컬럼을 가진 articles 라는 이름의 table을 새롭게 만들기 (단, 두 컬럼 모두 비어 있으면 안된다)

    ```shell
    CREATE TABLE article ( title TEXT NOT NULL, content TEXT NOT NULL );
    ```

29. articles테이블에 값을 추가: title은 '1번제목', content는 '1번내용'

    ```shell
    INSERT INTO articles(title, content) VALUES ('1번제목', '1번내용');
    ```

30.  테이블의 이름 변경(articles to news)

    ```shell
    ALTER TABLE articles RENAME TO news;
    ```

31. 생성한 테이블에 subtitle이라는 새로운 컬럼 추가

    (1. NOT NULL 설정 없이 추가, 2. 기본값 설정)

    ```shell
    ALTER TABLE news ADD COLUMN subtitle TEXT;
    ALTER TABLE news ADD COLUMN subtitle TEXT NOT NULL DEFAULT '어쩌꼬';
    ```

32. 컬럼 이름 수정(title을 main_title로)

    ```shell
    ALTER TABLE news RENAME COLUMN title TO main_title;
    ```

33. subtitle 컬럼 지우기

    ```shell
    ALTER TABLE news DROP COLUMN subtitle;
    ```

    



## Practice

### 1. 기본 CRUD 로직

1. 모든 user 레코드 조회

   ```python
   # orm
   ```

      ```sql
   -- sql
      ```

2. user 레코드 생성

   ```python
   # orm
   ```

   ```sql
   -- sql
   ```

   * 하나의 레코드를 빼고 작성 후 `NOT NULL` constraint 오류를 orm과 sql에서 모두 확인 해보세요.

3. 해당 user 레코드 조회

   - `102` 번 id의 전체 레코드 조회

   ```python
   # orm
   
   ```

   ```sql
   -- sql
   ```

4. 해당 user 레코드 수정

   - ORM: `102` 번 글의 `last_name` 을 '김' 으로 수정
   - SQL: `102` 번 글의 `first_name` 을 '철수' 로 수정

   ```python
   # orm
   user = User.objects.get(pk=102)
   user.last_name = "김"
   user.save()
   ```

      ```sql
   -- sql
      ```

5. 해당 user 레코드 삭제

   - ORM: `102` 번 글 삭제
   - `SQL`:  `101` 번 글 삭제 

   ```python
   # orm
   ```

   ```sql
   -- sql
   ```



### 2. 조건에 따른 쿼리문

1. 전체 인원 수 

   - `User` 의 전체 인원수

   ```python
   # orm
   User.objects.all().count()
   ```

   ```sql
   -- sql
   ```

2. 나이가 30인 사람의 이름

   - `ORM` : `.values` 활용
     - 예시: `User.objects.filter(조건).values(컬럼이름)`

   ```python
   # orm
   User.Objects.filter(age=30).values(first_name)
   ```

      ```sql
   -- sql
      ```

3. 나이가 30살 이상인 사람의 인원 수

   -  ORM: `__gte` , `__lte` , `__gt`, `__lt` -> 대소관계 활용

   ```python
   # orm
   
   ```

      ```sql
   -- sql
      ```

4. 나이가 20살 이하인 사람의 인원 수 

   ```python
   # orm
   ```

   ```sql
   -- sql
   ```

5. 나이가 30이면서 성이 김씨인 사람의 인원 수

   ```python
   # orm
   ```

      ```sql
   -- sql
      ```

6. 나이가 30이거나 성이 김씨인 사람?

   ```python
   # orm
   (User.objects.filter(age=30) | User.objects.filter(last_name='김')).count()
   User.objects.filter(Q(age=30) | Q(last_name='김')).count()
   ```

   ```sql
   -- sql
   ```

7. 지역번호가 02인 사람의 인원 수

   - `ORM`: `__startswith` 

   ```python
   # orm
   (User.objects.filter(age=30) | User.objects.filter(last_name='김')).count()
   User.objects.filter(Q(age=30) | Q(last_name='김')).count()
   ```

      ```sql
   -- sql
      ```

8. 거주 지역이 강원도이면서 성이 황씨인 사람의 이름

   ```python
   # orm
   User.objects.filter(country='강원도', last_name='황').values('first_name')
   ```

      ```sql
   -- sql
      ```



### 3. 정렬 및 LIMIT, OFFSET

1. 나이가 많은 사람순으로 10명

   ```python
   # orm
   User.objects.order_by('-age')[:10]
   ```

      ```sql
   -- sql
      ```

2. 잔액이 적은 사람순으로 10명

   ```python
   # orm
   User.objects.order_by('balance')[:10]
   ```

      ```sql
   -- sql
      ```

3. 잔고는 오름차순, 나이는 내림차순으로 10명?

   ```python
   # orm
   
   ```

   ```sql
   -- sql
   ```

4. 성, 이름 내림차순 순으로 5번째 있는 사람

   ```python
   # orm
   User.objects.order_by('-last_name','-first_name')[4]
   ```

      ```sql
   -- sql
      ```





1. 전체 평균 나이

   ```python
   # orm
   User.objects.aggregate(AVG('age'))
   ```

      ```sql
   -- sql
      ```

2. 김씨의 평균 나이

   ```python
   # orm
   User.objects.filter(last_name='김').aggregate(AVG('age'))
   ```

      ```sql
   -- sql
      ```

3. 강원도에 사는 사람의 평균 계좌 잔고

   ```python
   # orm
   User.objects.filter(country='강원도').aggregate(Avg('balance'))
   ```

   ```sql
   -- sql
   ```

4. 계좌 잔액 중 가장 높은 값

   ```python
   # orm
   User.objects.aggregate(Max('balance'))
   ```

      ```sql
   -- sql
      ```

5. 계좌 잔액 총액

   ```python
   # orm
   User.objects.aggregate(Sum('balance'))
   ```

      ```sql
   -- sql
      ```



#### 4.2 Annotate

1. 지역별 인원 수

   ```PYTHON
   # orm
   User.objects.values('country').annotate(Count('country'))
   User.objects.values('country').annotate(num_countries=Count('country'))
   User.objects.values('country').annotate(Count('country'), avg_balance=Avg('balance'))
   ```

   ```SQL
   -- sql
   ```

   

