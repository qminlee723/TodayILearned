# DB SQL

# :zero: OVERVIEW

1. [TOC]
   



---

# :one: DATABASE

## 1. Database

### 1) 개념

* DB는 **체계화**된 데이터의 모임
* 여러 사람이 고유하고 사용할 목적으로 통합 관리되는 정보의 집합
* 논리적으로 연관된 (하나 이상의) 자료 모음으로 그 내용을 고도로 구조화 함으로써 검색과 갱신의 효율화를 꾀한 것
* 즉, **몇 개의 자료 파일을 조직적으로 통합**하여 자료 항목의 **중복을 없애고** 자료를 **구조화**하여 기억시켜놓은 자료의 **집합체**
* 데이터와 자료가 조직적으로 구조화되어있는 집합체

### 2) 장점

* 데이터 중복 최소화
* 데이터 무결성(정확한 정보 보장)
* 일관성
* 독립성(물리적/논리적)
* 표준화
* 보안 유지



## 2. 관계형 데이터베이스(RDB: Relational Database)

### 1) 개념

* 키(key)와 값(value)들의 간단한 관계를 표의 형태로 정리한 데이터베이스
* 관계형 모델에 기반

### 2) 용어

* 스키마(schema)

  * 데이터베이스에서 자료의 구조, 표현방법, 관계 등 전반적인 명세 기술

  <img src="images\image-20220314090855831.png" alt="image-20220314090855831" style="zoom:50%;" />

* 테이블

  * 열과 행의 모델을 사용해 조직된 데이터 요소들의 집합

    <img src="images\image-20220314091047746.png" alt="image-20220314091047746" style="zoom: 67%;" />

* 열(column): 필드

  * 각 열에는 고유한 데이터 형식이 지정

  * 아래 예시에서는 name이라는 필드에 고객의 이름(TEXT) 정보가 저장됨

    <img src="images\image-20220314091200797.png" alt="image-20220314091200797" style="zoom:67%;" />

* 행(row): 레코드, 값

  * 실제 데이터가 저장되는 형태

  * 총 3명의 고객정보가 저장되어 있음(3개의 레코드)

    <img src="images\image-20220314091240900.png" alt="image-20220314091240900" style="zoom:67%;" />

* 기본 키(Primary Key)

  * 각 행(레코드)의 고유 값

  * 반드시 설정해야 하며, 데이터베이스 관리 및 관계 설정시 주요하게 활용됨

    <img src="images\image-20220314091316306.png" alt="image-20220314091316306" style="zoom:67%;" />





## 3. 관계형 데이터베이스 관리 시스템(RDBMS: Relational Database Management System)

### 1) 개념

* 관계형 모델을 기반으로 하는 데이터베이스 관리시스템을 의미
* 예시
  * MySQL, SQLite, ORACLE ... etc



### 2) SQLite

* 서버 형태가 아닌 파일 형식으로 응용 프로그램이 넣어서 사용하는 비교적 가벼운 데이터베이스. 구글 안드로이드 운영체제에 기본적으로 탑재된 데이터베이스이며, 임베디드소프트웨어에도 많이 활용됨. 로컬에서 간단한 DB 구성 가능, 오픈소스프로젝트이므로 자유로운 사용가능

  

### 3) Sqlite Date Type

* 동적 데이터 타입 가진다

* NULL
  * 데이터 없음
* INTEGER
  * 크기에 따라 0, 1, 2, 3, 4, 6 또는 8바이트에 저장된 부호 있는 정수
* REAL
  * 8바이트 부동소숫점 숫자로 저장된 부동 소수점 값(float)
* TEXT
  * 문자열
* BLOB
  * Binary Data
  * 입력된 그대로 정확히 저장된 데이터(별다른 타입 없이 그대로 저장)



### 4) Sqlite Data Affinity

* 타입 선호도. 특정 컬럼에 저장하도록 권장하는 데이터 타입
* INTEGER
* TEXT
* BLOB
* REAL
* NUMERIC





---

# :two: SQL

## 1. SQL

* 개념

  * Structured Query Language

  * 관계형 데이터베이스 관리시스템의 데이터 관리를 위해 설계된 특수 목적의 프로그래밍 언어

  * 데이터베이스 스키마 생성 및 수정

  * 자료의 검색 및 관리

  * 데이터베이스 객체 접근 조정 관리

    

    

* 분류

  * DDL: 정의(definition)

  * DML: 조작(manipulate)

  * DCL: 제어(control)<img src="images\image-20220314092248843.png" alt="image-20220314092248843" style="zoom:67%;" />



* 데이터 조작 언어(DML)

  * INSERT: C

  * SELECT: R

  * UPDATE: U

  * DELETE: D

  

* 명령어 끝에 `;` 꼭 써주기!



## 2. 테이블 생성 및 삭제

### 1) 기본 설정

* scv 파일 있는 곳에서 Sqlite shell 환경 오픈

  ```bash
  $ sqlite3 tutorial.sqlite3
  ```

* 데이터베이스 생성

  * '.' 은 sqlite 프로그램의 기능을 실행하는 것

  ```bash
  sqlite> .database
  ```

  ![image-20220314094846138](images\image-20220314094846138.png)

  ![image-20220314094919674](images\image-20220314094919674.png)

* 테이블 생성

  * 모드 활성화 및 csv 파일 import

    ```bash
    sqlite> .mode csv
    sqlite> .import hellodb.csv examples #examples는 테이블 이름
    ```

  * 테이블 목록 확인

    ```bash
    sqlite> .tables
    ```

  * Sqlite extensions 활용

    * tutorial.sqlite3 >  마우스 오른쪽 > open database 

    ![image-20220314095433334](images\image-20220314095433334.png)

    * Explorer 아래쪽에 sqlite explorer 나타남

      <img src="images\image-20220314095532655.png" alt="image-20220314095532655" style="zoom:67%;" />

    * 재생 표시 클릭시 표 형태로 된 데이터베이스를 볼 수 있다

      ![image-20220314095656712](images\image-20220314095656712.png)

      <img src="images\image-20220314095740314.png" alt="image-20220314095740314" style="zoom:67%;" />

    * 참고: 원본 csv 파일

      <img src="images\image-20220314095815374.png" alt="image-20220314095815374" style="zoom:67%;" />

* SELECT

  * 특정 테이블의 레코드(행) 정보를 반환

  ```bash
  sqlite> SELECT * FROM examples;
  # examples라는 테이블에서 모든(*) 데이터를 SELECT
  ```

  ![image-20220314100332908](images\image-20220314100332908.png)

* 터미널 view 변경하기

  * headers 추가

  ```bash
  sqlite> .headers on
  ```

  <img src="images\image-20220314100453244.png" alt="image-20220314100453244" style="zoom:67%;" />

  * column 정리

  ```bash
  sqlite> .mode column
  ```

  <img src="images\image-20220314100511410.png" alt="image-20220314100511410" style="zoom:67%;" />

* 자동완성, colorizing 되는 확장프로그램 사용

  * tutorial.sqlite3 마우스 오른쪽 > New Query 선택

    <img src="images\image-20220314100649612.png" alt="image-20220314100649612" style="zoom:67%;" />

  * `-- SQLite.sql`이라는 파일 생성될 것 > 저장

    <img src="images\image-20220314100826637.png" alt="image-20220314100826637" style="zoom:67%;" />

  * 해당 파일에서 sql 명령문 실행 가능

    * Run Query
      * 현재 파일에 작성된 모든 sql 문을 실행
    * Run Selected Query
      * 블록지정된, 혹은 커서가 위치한 곳의 sql문 실행

    <img src="images\image-20220314101407414.png" alt="image-20220314101407414" style="zoom:67%;" />

    * 어떤 데이터베이스에서 실행할 것인지 선택

      ![image-20220314101544982](images\image-20220314101544982.png)

    * 실행화면 (명령어 왼쪽, 결과 출력화면 오른쪽)

      * 나중에 명령어 정리 등 한눈에 보기 쉬움
      * SQL 문은 왠만하면 대문자 사용 - SQL문임을 구별하기 위해! (소문자 작동은 함)

      ![image-20220314101614525](images\image-20220314101614525.png)

    * 새로운 데이터베이스 생성시 Sqlite explorer 새로고침해주기

      <img src="images\image-20220314102004125.png" alt="image-20220314102004125" style="zoom:67%;" />



### 2) "테이블" 생성 및 삭제

* CREATE TABLE

  * 테이블 생성

    ```sqlite
    CREATE TABLE classmates (
    	id INTEGER PRIMARY KEY,
    	name TEXT
    );
    ```

    

* DROP TABLE

  * 테이블 제거 

    ```sqlite
    DROP TABLE classmates;
    ```

    * 새로고침 하면 사라진 것 볼 수 있음

    ![image-20220314103524634](images\image-20220314103524634.png)





## 3. :star: CRUD ("데이터" 조작)

![image-20220314133713427](images\image-20220314133713427.png)

### 1) CREATE

* **INSERT**

  * insert a single row into a table

    ```sql
    INSERT INTO 테이블이름 (컬럼1, 컬럼2, ...) VALUES (값1, 값2, ...)
    ```

* **id 조회**

  * 표에는 id가 출력되지 않음. 따로 조회하고 싶다면:

    ```sql
    sqlite> SELECT rowid, * FROM classmates;
    ```

  * SQLite는 따로 PK속성의 컬럼을 작성하지 않으면, 값이 자동으로 증가하는 PK를 가진 rowid컬럼을 정의

  * 64bit가 가질 수 있는 최댓값까지 생성됨(약 922경)

    * 만약 이 숫자 이상으로 데이터를 넣고 싶다면, 전체 데이터 중 중간에 삭제된 부분이 있다면 그 삭제된 부분에 데이터를 채워넣는다
    * 만약 그 테이블이 꽉 찬 경우, 더 이상 데이터를 넣을 수 없음

* **NULL**

  * 주소가 꼭 필요한 정보라면, 공백으로 비워두면 안된다. (NOT NULL 설정 필요)

  * 테이블 생성시 NOT NULL 설정 필요

    ```sql
    CREATE TABLE classmates (
      id INTEGER PRIMARY KEY,
      name TEXT NOT NULL,
      age INT NOT NULL,
      address TEXT NOT NULL
    );
    ```

    <img src="images\image-20220314110051874.png" alt="image-20220314110051874" style="zoom: 67%;" />

    * 이 상태에서 위에 실행한 INSERT 문을 실행한다면, 아래와 같은 에러 발생

      ```sql
      INSERT INTO classmates VALUES ('홍길동', 30, '서울');
      ```

      ![image-20220314110204258](images\image-20220314110204258.png)

    * 에러 발생시 해결방안

      1. id를 포함한 모든  value 작성(권장 X)

         ```sql
         INSERT INTO classmates VALUES (1, '홍길동', 30, '서울');
         ```

      2. :star:각 value에 맞는 column 들을 명시적으로 작성

         ``` sql
         INSERT INTO classmates (name, age, address) VALUES ('홍길동', 30, '서울');
         ```

* **AUTOINCREMENT** 

  ```sql
  CREATE TABLE 테이블이름 (
  	id INTEGER PRIMARY KEY AUTOINCREMENT,
  	. . . 
  	);
  ```

  * Column attribute
  * SQlite 가 사용되지 않은 값이나 이전에 삭제된 행의 값을 재사용하는 것을 방지



### 2) READ

* SELECT
  * query data from a table
  * 테이블에서 데이터를 조회
  * 다양한 절(clause)과 함께 사용
    * ORDER BY, DISTINCT, WHERE, LIMIT, GROUP BY....



* **SELECT의 기본형태**

  ```sql
  SELECT 컬럼1, 컬럼2, ... FROM 테이블이름;
  ```

  

* SELECT와 함께 사용하는 clause

  * **LIMIT**

    ```sql
    SELECT 컬럼1, 컬럼2, ... FROM 테이블이름 LIMIT 숫자;
    ```

    * constrain the number of rows returned by a query
    * 쿼리에서 반환되는 행 수를 제한
    * 특정 행부터 시작해서 조회하기 위해 **OFFSET** 키워드와 함께 사용하기도 함

  * **WHERE**

    ```sql
    SELECT 컬럼1, 컬럼2, ... FROM 테이블이름 WHERE 조건;
    ```

    * specify the search condition for rows returned by the query
    * 쿼리에서 반환된 행에 대한 특정 검색 조건을 지정

  * **DISTINCT**

    ```sql
    SELECT DISTINCT 컬럼1, 컬럼2, ... FROM 테이블이름;
    ```

    * remove duplicate rows in the result set
    * 조회 결과에서 중복 행을 제거
    * DISTINCT 절은 SELECT 키워드 바로 뒤에 작성해야 함 (SELECT DISTINCT)

  * **OFFSET**

    ```sql
    SELECT 컬럼1, 컬럼2, ... FROM 테이블이름 LIMIT 숫자 OFFSET 숫자;
    ```

    * 동일 오브젝트 안에서 오브젝트 처음부터 주어진 요소나 지점까지의 변위차(**위치 변화량**)을 나타내는 정수형

    * 예시

      1. 문자열 'abcdef'에서 문자 'c'는 시작점 'a'에서 2의 OFFSET을 지님

      2. `SELECT * FROM MY_TABLE LIMIT 10 OFFSET 5`

         \- 6번째 행부터 10개 행의 조회(6번째 행부터 10개를 출력)

         \- 0부터 시작



### 3) DELETE 

* DELETE

  * removes rows from a table
  * 조건을 통해 특정 레코드 삭제

* 기본형태

  ```sql
  DELETE FROM 테이블이름 WHERE 조건;
  ```

* 기준

  * 중복 불가능한(UNIQUE) 값인 rowid를 기준으로 삭제
  * 나중에 삽입을 하게되면, 삭제된 rowid를 재사용하여 값을 넣어주는 것을 알 수 있다.
  * 이때, 재사용 없이 사용하지 않은 다음 행 값을 사용하게 하려면 생성시 AUTOINCREMENT

  

### 4) UPDATE

* UPDATE

  * update data of existing rows in the table
  * 기존 행의 데이터를 수정
  * SET clause에서 테이블의 각 열에 대해 새로운 값을 설정

* 기본형태

  ```sql
  UPDATE 테이블이름 SET 컬럼1=값1, 컬럼2=값2, ... WHERE 조건;
  ```

* 기준

  * 중복 불가능한(UNIQUE) 값인 rowid를 기준으로 삭제





## 4. WHERE

### 1. Table users 생성

* Tables users 생성

  * `05_where.sql` 파일에 SQL 명령문 입력

  ```sql
  CREATE TABLE users (
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    age INTEGER NOT NULL,
    country TEXT NOT NULL,
    phone TEXT NOT NULL,
    balance INTEGER NOT NULL
  );
  ```

  * csv 파일 정보를 테이블에 적용

  ![image-20220314140934536](images\image-20220314140934536.png)

  * 결과

  <img src="images\image-20220314141019828.png" alt="image-20220314141019828" style="zoom:80%;" />

  





## 5. 집계 함수(AGGREGATE FUNCTIONS)

### 1. Aggregate functions

* 값 집합에 대한 계산을 수행하고 단일 값을 반환

  *  여러 행으로부터 하나의 결괏값을 반환하는 함수

* SELECT 구문에서만 사용됨

* 해당 컬럼이 숫자(INTEGER)일 때만 사용가능

* 예시

  * 테이블 전체 행 수를 구하는 `COUNT(*)`
  * age 컬럼 전체 평균을 구하는 `AVG(age)`

  

### 2. 용어

* COUNT

  * 그룹의 항목 수를 가져옴

    ```sql
    SELECT COUNT(컬럼) FROM 테이블이름;
    ```

    

* AVG

  * 모든 값의 평균을 계산

    ```sql
    SELECT AVG(컬럼) FROM 테이블이름;
    ```

    

* MAX

  * 그룹에 있는 몯느 값의 최대값을 가져옴

    ```sql
    SELECT MAX(컬럼) FROM 테이블이름;
    ```

    

* MIN

  * 그룹에 있는 모든 값의 최솟값을 가져옴

    ```sql
    SELECT MIN(컬럼) FROM 테이블이름;
    ```

    

* SUM

  * 모든 값의 합을 계산

    ```sql
    SELECT SUM(컬럼) FROM 테이블이름;
    ```

    

## 6. LIKE

### 1. Like

* 개념
  * query data based on pattern matching
  *  패턴 일치를 기반으로 데이터를 조회
  * SQLite는 패턴 구성을 위한 2개의 wildcards를 제공
    * `%`: 0개 이상의 문자
    * `_`: 임의의 단일 문자



* 기본 구조

  ``` sql
  SELECT * FROM 테이블 WHERE 컬럼 LIKE '와일드카드패턴';
  ```

  

### 2. Wildcard character

* Wildcard character

  * 파일을 지정할 때, 구체적인 이름 대신에 여러 파일을 동시에 지정할 목적으로 사용하는 특수 기호
    * `*`, `?` 등

  * 주로 특정한 패턴이 있는 문자열 혹은 파일을 찾거나, 긴 이름을 생략할 때 쓰임

  * 텍스트 값에서 알 수 없는 문자를 사용할 수 있는 특수문자로, 유사하지만 동일한 데이터가 아닌 여러 항목을 찾기에 매우 편리한 문자

  * 지정된 패턴 일치를 기반으로 데이터를 수집하는 데도 도움이 될 수 있음



* 와일드 카드 패턴
  <img src="images\image-20220314143143935.png" alt="image-20220314143143935" style="zoom:80%;" />
  * `%` 이 자리에 문자열이 있을 수도, 없을 수도 있다.
  * `_` 반드시 이 자리에 한 개의 문자가 존재해야 한다.

###  



## 7. ORDER BY & GROUP BY

### 1. ORDER BY

#### 1) 개념

* sort a result set of a query
* 조회 결과 집합을 정렬
* SELECT  문에 추가하여 사용
* 정렬 순서를 위한 2개의 keyword 제공
  * **ASC** - 오름차순*(default)*
  * **DESC**  - 내림차순

#### 2) 기본구조

```sql
SELECT * FROM 테이블 ORDER BY 컬럼 ASC; # default
SELECT * FROM 테이블 ORDER BY 컬럼1, 컬럼2 DESC;
```



### 2. GROUP BY

#### 1) 개념

* make a set of summary rows from a set of rows
* 행 집합에서 요약 행 집합을 만듦
* SELECT문의 optional 절
* 선택된 행 그룹을 하나 이상의 열 값으로 요약 행으로 만듦
* 문장에 WHERE절이 포함 경우, 반드시 WHERE 절 뒤에 작성해야 함
* 지정된 기준에 따라 행 세트를 그룹으로 결합
* 데이터를 요약하는 상황에 주로 사용

#### 2) 기본구조

```sql
SELECT 컬럼1, aggregate_function(컬럼2) FROM 테이블 GROUP BY 컬럼1, 컬럼2;
```





## 8. ALTER TABLE

* 개념

  * 테이블 수정하는 명령어
  * 명령어 암기

* ALTER TABLE의 3 가지 기능

  * 테이블 이름 변경

    ```sql
    ALTER TABLE 기존테이블이름 RENAME TO 새로운테이블이름;
    ```

  * 테이블에 새로운 column 추가

    ```sql
    ALTER TABLE 테이블이름 ADD COLUMN 컬럼이름 데이터타입설정;
    ```

  * column 이름 수정(new in sqlite 3.25.0)

    ```sql
    ALTER TABLE 테이블이름 RENAME COLUMN 현재열이름 TO 새로운열이름;
    ```

  * column 삭제하기

    ```sql
    ALTER TABLE 테이블이름 DROP COLUMN 삭제할열이름;
    ```

  
  



---

# :three: SQL 장고에서 활용하기

* sqlmigrate

  * 설계도번호(`migrations/` 내 파일)
  * 설계도(ORM)가 어떤 SQL 문으로 넘어갈지 보여줌
    * "articles_article": 테이블 이름
    * 장고는 기본적으로 NOT NULL이 설정되어 있음

  ```bash
  $ python manage.py sqlmigrate 앱이름 설계도번호
  $ python manage.py sqlmigrate articles 0001
  ```

  <img src="images\image-20220314131044126.png" alt="image-20220314131044126"  />

  ```bash
  $ python manage.py sqlmigrate articles 0002
  ```

  <img src="images\image-20220314131654795.png" alt="image-20220314131654795" style="zoom:67%;" />

  * 이 때, 장고에서 DateTimeField 넣어줬었음. 이걸 SQL 문으로 쓰면 위의 사진처럼 나옴

    ![image-20220314132339595](images\image-20220314132339595.png)

    





---

# :four: 실습(CRUD) :keyboard:

## 1. CREATE

* 테이블 생성 실습 및 스키마 확인

  ```sql
  CREATE TABLE classmates (
  	name TEXT,
  	age INT,
  	address TEXT
  );
  ```

  <img src="images\image-20220314103812086.png" alt="image-20220314103812086" style="zoom:67%;" />

  * shell에서 확인하려면

    ```bash
    sqlite> .schema classmates
    ```

    <img src="images\image-20220314103911992.png" alt="image-20220314103911992" style="zoom:67%;" />

* **INSERT 연습**

  * 기본

    * 새로운 데이터베이스에서 연습

    * `tutorial.sqlite3` > 마우스 우클릭 > `New Query` > 저장

      <img src="images\image-20220314104621123.png" alt="image-20220314104621123" style="zoom:67%;" /> 

    * classmates 테이블에 이름이 홍길동이고 나이가 23인 데이터 삽입 및 SELECT문으로 확인

    ```sql
    INSERT INTO classmates (name, age) VALUES ('홍길동', 23);
    ```

    ![image-20220314104855916](images\image-20220314104855916.png)

    * 주소 서울 추가

    * 모든 열에 데이터가 있는 경우, column을 명시하지 않아도 됨

      ```sql
      INSERT INTO classmates VALUES ('홍길동', 30, '서울')
      ```

    * SELECT문으로 확인

      ```sql
      SELECT * FROM classmates;
      ```

  * 연습2: 이름/나이/주소로 구분되는 정보를 db에 저장 및 확인

    ![image-20220314111436176](images\image-20220314111436176.png)

    

## 2. READ

* classmates 테이블에서 id, name  컬럼 값만 조회

  ```sql
  SELECT rowid, name FROM classmates;
  ```

  <img src="images\image-20220314112132076.png" alt="image-20220314112132076" style="zoom: 67%;" />

* **LIMIT**: classmates 테이블에서 id, name  컬럼 값을 **하나**만 조회

  ```sql
  SELECT rowid, name FROM classmates LIMIT 1
  ```

  <img src="images\image-20220314112258140.png" alt="image-20220314112258140" style="zoom:80%;" />

* **OFFSET**: id, name 컬럼 값을 **세 번째**에 있는 **하나**만 조회하기

  ```sql
  SELECT rowid, name FROM classmates LIMIT 1 OFFSET 2;
  ```

  <img src="images\image-20220314112353493.png" alt="image-20220314112353493" style="zoom:80%;" />

* **WHERE**: classmates 테이블에서  주소가 서울인 경우의 id, names을 조회

  ```sql
  SELECT rowid, name FROM classmates WHERE address = '서울';
  ```

  <img src="images\image-20220314113318399.png" alt="image-20220314113318399" style="zoom: 67%;" />

* **DISTINCT**: classmates 이블에서 age값 전체를 중복없이 조회

  ```sql
  SELECT DISTINCT age FROM classmates;
  ```

  <img src="images\image-20220314113442617.png" alt="image-20220314113442617" style="zoom:67%;" />

  

## 3. DELETE

* DELETE: classmates 테이블에 id가 5인 레코드를 삭제

  ```sql
  DELETE FROM classmates WHERE rowid=5;
  ```

  <img src="images\image-20220314115612777.png" alt="image-20220314115612777" style="zoom:67%;" />

* 지워진 id(5)가 어떻게 되는지 데이터를 다시 추가해서 확인

  ```sql
  INSERT INTO classmates VALUES ('최전자', 28, '부산');
  
  SELECT rowid, * FROM classmates;
  ```

  <img src="images\image-20220314115717815.png" alt="image-20220314115717815" style="zoom:67%;" />

  * 다시 집어넣었을 때, id 5를 **재활용**해서 넣은 것을 알 수 있음 unlike 장고

* **AUTOINCREMENT**: 재사용 없이 사용하지 않은 다음 행 값을 사용하게 하는 SQL 명령어

  

## 4. UPDATE

* classmates 테이블에 id가 5인 레코드를 수정(이름을 홍길동, 주소를 제주도로 바꾸자)

  ```sql
  UPDATE classmates 
  SET name='홍길동',
  address='제주도'
  WHERE rowid=5;
  
  SELECT rowid, * FROM classmates;
  ```

  <img src="images\image-20220314133342053.png" alt="image-20220314133342053" style="zoom:67%;" />

  * 최전자가 홍길동으로 바뀐 것을 알 수 있음



## 5. WHERE

* users 테이블에서 age가 30 이상인 유저의 모든 컬럼 정보를 조회

  ```sql
  SELECT * FROM users WHERE age >= 30;
  ```

  <img src="images\image-20220314141435536.png" alt="image-20220314141435536" style="zoom:67%;" />

* users 테이블에서 age가 30 이상인 유저의 이름만 조회

  ```sql
  SELECT first_name FROM users WHERE age >= 30;
  ```

  <img src="images\image-20220314141415366.png" alt="image-20220314141415366" style="zoom:67%;" />

* users 테이블에서 age가 30 이상**이고(AND)** 성이 '김'인 사람의 나이와 성만 조회

  ```sql
  SELECT age, last_name FROM users WHERE age >= 30 AND last_name = '김';
  ```

  <img src="images\image-20220314141615005.png" alt="image-20220314141615005" style="zoom:67%;" />



## 6. AVG, SUM, MIN, MAX

* 그룹의 항목 수를 가져온다(행 수)

  ```sql
  SELECT COUNT(*) FROM users;
  ```

  <img src="images\image-20220314142029635.png" alt="image-20220314142029635" style="zoom:67%;" />

* 30살 이상의 사람들의 평균 나이

  ```sql
  SELECT AVG(age) FROM users WHERE age >= 30;
  ```

  <img src="images\image-20220314142138083.png" alt="image-20220314142138083" style="zoom:67%;" />

* 계좌 잔액(balance)이 가장 높은 사람과 그 액수 조회

  ```sql
  SELECT first_name, MAX(balance) FROM users;
  ```

  <img src="images\image-20220314142222299.png" alt="image-20220314142222299" style="zoom:67%;" />

* 나이가 30살 이상인 사람의 계좌 평균 잔액 조회

  ```sql
  SELECT AVG(balance) FROM users WHERE age >= 30;
  ```

  <img src="images\image-20220314142307241.png" alt="image-20220314142307241" style="zoom:67%;" />

  

## 7. LIKE

* users 테이블에서 나이가 20대인 사람만 조회

  ```sql
  SELECT * FROM users WHERE age LIKE '2_';
  ```

  <img src="images\image-20220314143449033.png" alt="image-20220314143449033" style="zoom:67%;" />

  * 만약 `%`  를 쓴 경우, 2살, 200살 2000살인 사람도 조회가 되므로, 20대를 지정하기 위해서는 `_`를 쓰는 것이 바람직.

* users 테이블에서 지역 번호가 02인 사람만 조회

  ```sql
  SELECT * FROM users WHERE phone LIKE '02-%';
  ```

  <img src="images\image-20220314143845166.png" alt="image-20220314143845166" style="zoom:67%;" />

  * "02-" 까지는 무조건 맞아야 하므로.

* users 테이블에서 이름이 '준'으로 끝나는 사람만 조회

  ```sql
  SELECT * FROM users WHERE first_name LIKE '%준';
  ```

  <img src="images\image-20220314144037634.png" alt="image-20220314144037634" style="zoom:67%;" />

* users 테이블에서 중간 번호가 5114인 사람만 조회

  ```sql
  SELECT * FROM users WHERE phone LIKE '%-5114-%';
  ```

  <img src="images\image-20220314144357627.png" alt="image-20220314144357627" style="zoom:67%;" />



## 8. ORDER BY

* users 에서 나이 순으로 오름차순 정렬하여 상위 10개만 조회

  ```sql
  SELECT * FROM users ORDER BY age ASC LIMIT 10;
  ```

  <img src="images\image-20220314150047834.png" alt="image-20220314150047834" style="zoom:67%;" />

* 나이 순, 성 순으로 오름차순 정렬하여 상위 10개만 조회

  ```sql
  SELECT * FROM users ORDER BY age, last_name ASC LIMIT 10;
  ```

  <img src="images\image-20220314150325418.png" alt="image-20220314150325418" style="zoom:67%;" />

  * 정렬 기준이 2개 이상인 경우, 어떤 것이 우선적으로 기준이 되는지 
    * 먼저 쓴 것 (age, last_name 이면 age, last_name, age이면 last_name) :question:

* 계좌 잔액 순으로 내림차순 정렬하여 해당 유저의 성과 이름을 10개만 조회

  ```sql
  SELECT last_name, first_name FROM users ORDER BY balance DESC LIMIT 10;
  ```

  <img src="images\image-20220314150744166.png" alt="image-20220314150744166" style="zoom:67%;" />



## 9. GROUP BY

* users 에서 각 성(last_name) 씨가 몇 명씩 있는지 조회

  ```sql
  SELECT last_name, COUNT(*) FROM users GROUP BY last_name;
  ```

  <img src="images\image-20220314151448869.png" alt="image-20220314151448869" style="zoom:67%;" />

* column의 이름을 바꾸고 싶다면

  ```sql
  SELECT last_name, COUNT(*) AS name_count FROM users GROUP BY last_name;
  ```

  <img src="images\image-20220314151912204.png" alt="image-20220314151912204" style="zoom:67%;" />



## 10. ALTER TABLE

* 잠깐 복습

  * title과 content라는 컬럼을 가진 articles 라는 이름의 table을 새롭게 만들기

    * 단, 두 컬럼 모두 비어 있으면 안되며, rowid를 사용

    ```sql
    CREATE TABLE articles (
      title TEXT NOT NULL,
      content TEXT NOT NULL
    );
    ```

  * articles테이블에 값을 추가

    * title은 '1번제목', content는 '1번내용'

    ```sql
    INSERT INTO articles VALUES ('1번제목', '1번내용');
    ```

    <img src="images\image-20220314152607700.png" alt="image-20220314152607700" style="zoom:67%;" />

* 바로 위에 생성한 테이블의 이름 변경

  ```sql
  ALTER TABLE articles RENAME TO news;
  ```

  <img src="images\image-20220314153150851.png" alt="image-20220314153150851" style="zoom:67%;" />

* 생성한 테이블에 새로운 컬럼 추가

  ```sql
  ALTER TABLE news ADD COLUMN created_at TEXT;
  ```

  * 주의: 데이터 타입 NOT NULL은 추가가 불가능하다

    ```sql
    ALTER TABLE news ADD COLUMN created_at TEXT NOT NULL;
    ```

    <img src="images\image-20220314153400853.png" alt="image-20220314153400853" style="zoom: 67%;" />

    * 테이블에 있던 기존 레코드들에게는 새로 추가할 필드에 대한 정보가 없으므로.

* 해결 방법 2가지

  * NOT NULL  설정 없이 추가

    ```sql
    ALTER TABLE news ADD COLUMN created_at TEXT;
    ```

    <img src="images\image-20220314154321508.png" alt="image-20220314154321508" style="zoom:67%;" />

    ```sql
    INSERT INTO news VALUES ('제목', '내용', datetime('now'));
    ```

    <img src="images\image-20220314154451229.png" alt="image-20220314154451229" style="zoom:67%;" />

  * 기본값(DEFAULT) 설정

    ```sql
    ALTER TABLE news ADD COLUMN subtitle TEXT NOT NULL DEFAULT '소제목';
    ```

    <img src="images\image-20220314154820402.png" alt="image-20220314154820402" style="zoom:67%;" />

* 컬럼 이름 수정

  ```sql
  ALTER TABLE news RENAME COLUMN title TO main_title;
  ```

  <img src="images\image-20220314154956638.png" alt="image-20220314154956638" style="zoom:67%;" />

* 컬럼 지우기

  ```sql
  ALTER TABLE news DROP COLUMN subtitle;
  ```

  <img src="images\image-20220314155142121.png" alt="image-20220314155142121" style="zoom:67%;" />

