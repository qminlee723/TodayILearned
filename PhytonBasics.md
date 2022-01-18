# PYTHON BASICS

## 파이썬이란?

* Expressive Language
* Interpreter
* Object Oriented Programming (<-> 절차지향/함수형)
  * Object: 숫자, 문자, 클래스 등 값을 가지고 있는 모든 것 
  * 장점: 유지보수가 쉽다(데이터+함수)
  * 단점: 프로그래밍의 크기가 점점 커지므로 객체를 설계하기가 어렵다
    * 이러한 단점을 개선하기 위해 함수형 프로그래밍이 나욤
    * but 많이 사용하지 X
      * 함수형 프로그래밍: 외부에서의 정보를 받아들이지 X. 간단하게 설계 가능

### 파이썬 개발환경

* Pycharm: Python에 특화, debugging이 VS code보다 자세함
  * 유료버전: Django - 외부에 있는 서버 컴퓨터를 내 컴퓨터처럼 쓸 수 있게 지원(유료)
* VS code: MS사에서 내놓은 IDE, 거의 모든 소스코드 포맷을 지원



 





---



## 기초 문법

### 코드 스타일 가이드

* PEP8 (https://www.python.org/dev/peps/pep-0008)
* Google Style guide



### 들여쓰기(Indentation)

* Space sensitive

  * space 4번 혹은 tab 1번
  * 한 코드 안에서는 *반드시 한 종류*의 들여쓰기를 사용(Space, tab 혼용 불가)

  

---

### 변수(Variable)

* 컴퓨터 메모리 어딘가에 저장되어 있는 객체를 참조하기 위해 사용되는 이름

* 객체(object): 숫자, 문자, 클래스 등 값을 가지고 있는 모든 것

* 동일 변수에 다른 객체를 언제든 할당할 수 있기 때문에, 즉, 참조하는 객체가 바뀔 수 있기 때문에 변수라고 불린다. 

* type()
  * 변수에 할당된 값의 타입
  
* id()
  * 변수에 할당된 값(객체)의 고유한 아이덴티티 값
  
  

#### 1. 변수 연산

* **숫자 연산**

  ```python
  i = 5
  j = 3
  s = '파이썬'
  ```

  ```python
  i + j 
  ```

  8

* **문자 연산**

  ```python
  s = s * 3
  ```
  
  '파이썬파이썬파이썬'
  
  

#### 2. 변수 할당

* **같은 값을 동시**에 할당할 수 있음

  ```python
  x = y = 1004
  print(x, y)
  ```

  1004 1004

  

* **다른 값을 동시**에 할당할 수 있음(multiple assignment)

  ```python
  x, y = 1, 2
  print(x, y)
  ```

  



#### 3. 실습 문제 :white_check_mark:

x = 10, y = 20일 때, 각각 값을 바꿔서 저장하는 코드를 작성하시오

- [x] 1) tmp 활용 :question:

```python
tmp = x
x = y
y = tmp
print(x, y)
```

- [x] 2. phytonic!

``` python
y, x = x, y
print(x, y)
```



---

### 식별자(Identifiers)

* 변수(박스)의 이름

* 파이썬 객체(변수, 함수, 모듈, 클래스 등)를 식별하는데 사용하는 이름(name)

* 규칙

  * 식별자의 이름은 영문 알파벳, 언더스코어, 숫자

  * RedApple: Camel case, Red_Apple: Snake case

  * 첫 글자에 숫자가 올 수 없음

  * 길이제한 X, 대소문자 구별

  * 다음의 키워드는 예약어(reserved words)로 사용할 수 없음

    ```python
    False, None, True, and, as, assert, async, await, break, class, continue, def, del, elif, else, except, finally, for, from, global, if, import, in, is, lambda, nonlocal, not, or, pass, raise, return, try, while, with, yield
    ```

    ```
    print 등
    ```

    

### 사용자 입력

* input([prompt])

* 대괄호 부분에 문자열을 넣으면 입력시, 해당 문자열을 출력할 수 있다. 

* 반환값은 항상 문자열의 형태로 반환

* ```python
  name = input('이름을 입력해주세요: ')
  print(name)
  ```

  이름을 입력해주세요: 김싸피
  
  김싸피
  
   

### 주석

* 코드에 대한 설명, 사용자만을 위한 부연 설명
  * 프로그램 속도 및 용량에 영향 미치지 않음

#### 1. 한 줄 주석

* **#**

  ```python
  # 이름을 출력합니다
  print('ssafy kim') #ssafy kim을 출력합니다
  ```

  

#### 2. 여러 줄 주석

* 한 줄씩 **#**
* ***```***
* **'''**: docstring :label: *함수 부분에서 다시 다룰 예정*

* **VS code**: ctrl + /





---



## :star: 파이썬 자료형(Python Datatype)



### 1. None

* 값이 없음을 표현

* ```python
  print(type(None))
  ```

* ```python
  a = None
  print (a)
  ```

  None



### 2. 불린형(Boolean)

* True/False값

* 비교, 논리 연산을 수행할 시 활용

* 다음은 모두 False로 변환(비어 있는 것들)
  * 0, 0.0, (). [], {}, '', None
  * 단, bool([0]) = TRUE: 0이라는 값이 안에 들어있는 것이기 때문에 비어있는 것이 아님
  
* 연습문제

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118003101439.png" alt="image-20220118003101439" style="zoom: 50%;" />



### 3. 수치형(Numeric Type)

#### 1) 정수 (integer)

* **int()**

* 매우 큰 수를 나타낼 때도 overflow가 발생하지 않음

  * overflow: 데이터 타입별로 사용할 수 있는 메모리의 크기를 넘어서는 상황
  * 임의 정밀도 산술(Arbitrary precision arithmetic)을 통해 고정된 형태의 메모리가 아닌 가용 메모리들을 활용하여 모든 수 표현에 활용

* 진수 표현

  * binary(0b)

    ```python
    0b10
    ```

    2

  * octal(0o)

    ```python
    0o30
    ```

    24

  * hexadecimal(0x)

    ```python
    0x10
    ```

    16



#### 2) 부동소수점, 실수 (floating point number)

* **float()**

* 정수가 아닌 모든 실수, 부동소수점

  ```python
  11/2
  ```

  5.5

  ```python
  10**100/3
  ```

  3.33333333333e+99

  ```python
  1/-10**100
  ```

  -1e-100

  ```python
  1e-1
  ```

  0.1

* :question:**Floating point rounding error**: 값 비교하는 과정에서 정수가 아닌 실수인 경우 주의

  ```python
  #왼쪽의 계산 결과와 오른쪽 값은 같은 값일까요?
  3.14 - 3.02 == 0.12
  ```

  False

  ```python
  3.14 - 3.02 
  ```

  0.1200000000000001

  

  * 같은 값임을 증명하기 위해서 *<u>매우 작은 수보다 작은지</u>*를 확인하거나 <u>*math 모듈*</u> 활용

    ```python
    #1. 임의의 작은 수
    abs(a - b) <= 1e-10
    ```

    True

    ```python
    #2. system상의 machine epslion
    import sys
    print(abs(a - b) <= sys.float_info.epsilon)
    print(sys.float_info.epsilon)
    ```

    True

    2.220446049250313e-16

    ```python
    #3. Python 3.5이상
    import math
    math.isclose(a, b)
    ```

    True

    

#### 3) 복소수 (complex number)

* 실수부와 허수부로 구성된 복소수는 모두 complex 타입. 허수부를 j로 표현

  ```python
  a = 3 + 4j
  print(type(a))
  ```

  <class 'complex'>

  ```python
  a.real
  ```

  3.0

  ```python
  a.imag
  ```

  4.0



### :star: 4. 문자열(String Type)

* 문자열은 작은 따옴표나 큰 따옴표를 활용하여 표기. 소스코드 내 하나의 문장부호 선택해 유지 추

#### 1) Immutable

* 불변하다

  ```python
  a = 'my string?'
  a[-1] = '!'
  ----------------------------------------------------------------------
  TypeError: 'str' object does not support item assignment
  ```

* 특정 값 하나만 바꿀 수 없다!

  

#### 2) Iterable

* ```python
  a = '123'
  for char in a:
  	print(char)
  ```

  1

  2

  3
  
  

#### 3) 중첩따옴표(Nested Quotes)

* 따옴표 안에 따옴표를 표현할 경우

* 작은 따옴표가 들어 있는 경우는 큰 따옴표로, 큰 따옴표가 들어 있는 경우는 작은 따옴표로(중복되지 않게) 사용한다

  ```python
  print("문자열 안에 '작은 따옴표'를 사용하려면 큰 따옴표로 묶는다.")
  ```

  

#### 4) 삼중따옴표(Triple Quotes)

* 따옴표 안에 따옴표를 넣을 때, 여러줄을 나누어 입력할 때 편리하다.

  ```python
  print('''문자열 안에 '작은 따옴표'나 
  "큰 따옴표"를 사용할 수 있고 
  여러 줄을 사용할 때도 편리하다.''')
  ```

  문자열 안에 '작은 따옴표'나 
  "큰 따옴표"를 사용할 수 있고 
  여러 줄을 사용할 때도 편리하다.

  

#### 5) Escape sequence

* 문자열 내에서 특정 문자나 조작을 위해서 역슬래시(\\)를 활용해서 구분

  | 예약문자 | 내용(의미)                                   |
  | -------- | -------------------------------------------- |
  | \n       | 줄 바꿈                                      |
  | \t       | 탭                                           |
  | \r       | 캐리지리턴 (커서를 맨 앞으로 옮겨주는 역할 ) |
  | \0       | 널(Null)                                     |
  | (\\)\    | \\ 표기                                      |
  | \\'      | 단일인용부호(')                              |
  | \\"      | 이중인용부호(")                              |

  ```python
  print(철수\'안녕\'')
  ```

  철수 '안녕'

  ```python
  print('이 다음은 엔터.\n그리고 탭\t탭')
  ```

  이 다음은 엔터.

  그리고 탭	탭

  

#### :star: 6) String Interpolation

* 문자열을 변수를 활용하여 만드는 법

  * **%-formatting**: 대부분의 타 프로그래밍의 언어에서 사용

    ```python
    print('Hello, %s' % name)
    print('내 성적은 %d' % score)
    print('내 성적은 %f' % score)
    ```

    Hello, Kim

    내 성적은 4

    내 성적은 4.500000

  * **str.format()**

    ```python
    print('Hello, {}! 성적은 {}'.format(name, score))
    ```

    Hello, Kim! 성적은 4.5

  * **f-strings**: python 3.6+ :sparkles: <- *제일 자주 씀*

    ```python
    print(f'Hello, {name}! 성적은 {score}')
    ```

    Hello, Kim! 성적은 4.5
    
    ```python
    import datetime
    today = datetime.datetime.now()
    print(today)
    ```
    
    2021-06-24 15:01:21.704852
    
    ```python
    f'오늘은 {today:%y}년 {today:%m}월 {today:%d}일'
    ```
    
    '오늘은 21년 06월 24일'
    
    ```python
    pi = 3.141592
    f'원주율은 {ㅔㅑ:.3}. 반지름이 2일 때 원의 넓이는 {pi * 2 * 2}'
    ```
    
    '원주율은 3.14. 반지름이 2일 때 원의 넓이는 12.566368'



---

## 컨테이너형

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118010239211.png" alt="image-20220118010239211" style="zoom: 50%;" />

* 여러 개의 값을 담을 수 있는 것(객체)으로, 서로 다른 자료형을 저장할 수 있음.
  * Ordered/Unordered
  * 순서가 있다 != 정렬되어 있다

* **컨테이너 형 변환(Container Typecasting)**: 컨테이너 간 형 변환은 아래와 같이 가능

  ![image-20220118021829653](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118021829653.png)





### 1. 시퀀스형(Sequence Container)

#### 1) List (mutable)

* **list[i]**

* <u>순서를 가지는</u> 0개 이상의 객체를 참조하는 자료형

* 생성과 접근

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118010609122.png" alt="image-20220118010609122" style="zoom:50%;" />

  ```python
  my_list = []
  another_list = list()
  print(type(my_list))
  print(type(another_list))
  ```

  <class 'list'>

  <class 'list'>

  ```python
  location = ['서울', '대전', '구미', '광주', '부울경']
  print(location)
  print(type(location))
  ```

  ['서울', '대전', '구미', '광주', '부울경']

  <class 'list'>

  ```python
  location[0]
  ```

  '서울'

  

* **List 예시**

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118010837508.png" alt="image-20220118010837508" style="zoom:50%;" />



#### 2) Tuple (immutable)

* **tuple()**

* <u>순서를 가지는</u> 0개 이상의 객체를 참조하는 자료형

* 생성과 접근

  * 튜플은 수정이 불가능(immutable) 시퀀스로 인덱스로 접근 가능하다

    * 값에 대한 접근은 my_tuple[i]

    ```python
    (1, 2, 3, 1)
    ```

    (1, 2, 3, 1)

    ```python
    tuple(1, 2, 3, 1)
    ```

    (1, 2, 3, 1)

    ```python
    type((1, 2, 3, 1))
    ```

    tuple

    ```python
    # 값 접근
    a = (1, 2, 3, 1)
    a[1]
    ```

    2

    ```python
    # 값 변경 => 불가능
    a[1] = '3'
    -------------------------------------------------------------------------
    TypeError: 'tuple' object does not support item assignment
    ```

    

* 튜플 생성시 **주의사항**

  * **단일 항목**의 경우: 하나의 항목으로 구성된 튜플은 생성 시 값 뒤에 쉼표를 붙여야 함

    ```
    a = 1, 
    print(a)
    print(type(a))
    ```

    (1, )

    <class 'tuple'>

  * **복수 항목**의 경우: 마지막 항목에 붙은 쉼표는 불필요

    ```python
    b = 1, 2, 3
    print(b)
    print(type(b))
    ```

    (1, 2, 3)

    <class 'tuple'>

    

* :question: **튜플 대입**

  * 우변의 값을 좌변의 변수에 한번에 할당하는 과정
  * 튜플은 일반적으로 파이썬 내부에서 활용된다. 

  * 추후 함수에서 복수의 값을 반환하는 경우에도 활용

    ```python
    x, y = 1, 2
    print(x, y)
    ```

    1 2

    ```python
    # 실제로 tuple로 처리
    x, y = (1, 2)
    print(x, y)
    ```

    1 2

    * 첫번째 예제에서 가능한 것 처럼(박스 넣기) 튜플에서도 가능하다는거 보여주는거임



#### 3) Range (immutable)

* **range(n)**: 기본형

  * 0부터 n-1까지의 숫자 시퀀스

    ```python
    # 0부터 특정 숫자까지
    list(range(3))
    ```

    [0, 1, 2]

* **range(n, m)**: 범위 지정

  * n부터 m-1까지의 숫자 시퀀스

    ```python
    # 숫자의 범위
    list(range(1, 5))
    ```

    [1, 2, 3, 4]

* **range(n, m, s)**: 범위 및 스텝 지정

  * n부터 m-1까지 s만큼 증가시키는 숫자 시퀀스

    ```python
    #step 활용
    list(range(1, 5, 2))
    ```

    [1, 3]

  

* 용도

  * range는 숫자의 시퀀스를 나타내기 위해 사용

    ```python
    range(4)
    ```

    range(0, 4)

    ```python
    list(range(4)) # 0부터 특정 숫자까지
    ```

    {0, 1, 2, 3}

    ```python
    print(type(range(4)))
    ```

    <class 'range'>

    ```python
    #역순
    list(range(6, 1, -1))
    ```

    [6, 5, 4, 3, 2]

    ```python
    list(range(1, 3, -1))
    ```

    [ ]

    ```python
    list(range(6, 1, 1))
    ```

    [ ]

    



---



### 패킹/언패킹 연산자(Packing/Unpacking Operator)

모든 시퀀스형(리스트, 튜플)은 패킹/언패킹 연산자 *를 사용하여 객채의 패킹 또는 언패킹 가능*

*"순서"가 포인트*, but 잘 안씀

​	x, *y = i , j, k ...



#### 패킹

* 대입문의 좌변 변수에 위치

* 우변의 객체 수가 좌변의 변수 수보다 많을 경우 객체를 순서대로 대입

* 나머지 항목들은 모두 별 기호로 표시된 변수에 리스트로 대입

* x, *y = i, [j, k, ...]

* **예제**

  ```python
  x, *y = 1, 2, 3, 4
  ```

  ```python
  print(x)
  type(x)
  ```

  1

  int

  ```python
  print(y)
  type(y)
  ```

  [2, 3, 4]

  list
  
* ![image-20220118103827982](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118103827982.png)



#### 언패킹

* argument 이름이 *로 시작하는 경우, argument unpacking이라고 함

* 패킹의 경우, 리스트로 대입

* 언패킹의 경우, **튜플 형태**로 대입

* **예시**
  
  ```python
  def multiply(x, y, z):
  	return x * y * z
  ```
  
  ```python
  numbers = [1, 2, 3]
  multiply(*numbers)
  ```

  6

  ![image-20220118103851257](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118103851257.png)
  
* :question:

![image-20220118104007428](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118104007428.png)

여기서 패킹이랑 언패킹 구분 다시



* **주의사항**: *가 곱셈을 의미하는지, packing/unpacking을 의미하는지 구분

  * packing/unpacking 연산자
    * 대입식(numbers)의 좌측에 위치(*numbers)
    * 하나로만 보이는 경우(단항 연산자)

  * 곱셈
    * 두개짜리 항의 식에서 중간에 있는 경우
    * ex) a * b



---



### 2. 비시퀀스형(Associative Container)

#### 1) Set (mutable)

* **{}** or **set()**

* 순서없이 0개 이상의 :question:*해시가능한* 객체를 참조하는 자료형

  * 해시가능한: 1:1 대응이 가능한 것. 중복이 없는 것 

* 수학에서의 집합과 동일한 구조를 가진다
  * 집합 연산이 가능
  * 중복된 값이 존재하지 않음

* **셋 활용**
  * 셋을 활용하면 다른 컨테이너에서 중복된 값을 쉽게 제거할 수 있다
    * 단, 순서가 중요한 경우 사용불가능

* **연습문제** :white_check_mark:

  1. 아래의 리스트에서 고유한 지역의 개수는?

     ```python
     my list = ['서울', '서울', '대전', '광주',	 
                '서울', '대전', '부산', '부산']
     ```

     ```python
     len(set(my_list))
     ```

     4

     

  2.  이를 등장한 순서대로 출력하시오

     ```python
     set(my_list)
     ```

     ('광주', '대전', '부산', '서울')

     - 이처럼 set을 사용하는 순간 순서가 사라진다. 순서가 중요하면 set 사용하면 안됨



#### 2) Dictionary (mutable)

* **{}** or **dict()**
* 순서 없이 키 - 값(key - value) 쌍으로 이루어진 객체를 참조하는 자료형
* Dictionary 의 키(key) - 해시 가능한 불변 자료형만 가능
* 각 키의 값(values) - 어떠한 형태든 관계 없음

* 딕셔너리 생성. Key를 통해 value에 접근 **{key: value}**

  ```python
  dict_a = {}
  print(type(dict_a))
  ```

  ```python
  dict_b = dict()
  print(type(dict_b))
  ```

  <class 'dict'>

  ```python
  dict_a = {'a': 'apple', 'b': 'banana', 'list': [1, 2, 3]}
  ```

  ```python
  dict_a
  ```

  {'a': 'apple', 'b': 'banana', 'list': [1, 2, 3]}

  ```python
  dict_a['list']
  ```

  [1, 2, 3]

  ```python
  dict_b = dict(a = 'apple', b = 'banana', list = [1, 2, 3])
  ```

  ```python
  dict_b
  ```

  {'a': 'apple', 'b': 'banana', 'list': [1, 2, 3]}

  

* Key 와 value가 쌍으로 이루어진 자료구조

  * key는 변경 불가능한 데이터(immutable)만 활용이 가능

    * string, integer, float, boolean, tuple, range

      ```python
      dict_c = {[1, 2, 3]: 'hi'}
      ------------------------------------------------------------
      TypeError: unhashable type: 'list'
      ```

  * value는 모든 값으로 설정이 가능하다(list, dictionary)

    ```python
    dic_d = {'a': 'apple', 3: '삼', '지역': ['서울', '광주']}
    ```

    ```python
    dic_d['지역'][0]
    ```

    '서울'



---



## Typecasting(자료형 변환)

### 암시적 형 변환 (implicit)

* 사용자가 *의도하지 않고*, 파이썬 내부적으로 자료형으로 변환하는 경우

  * 편하다! 그런데 위험하다(파이썬이 어떻게 변환시킬지도 생각하면서 코딩)

* bool/Numeric Type (int, float, complex)

  ```python
  True + 3	#True = 1
  ```

  4

  ```python
  3. + 5.0	#int + float = float
  ```

  8.0

  ```python
  3 + 4j + 5
  ```

  (8+4j)

  

### 명시적 형 변환 (explicit)

* 사용자가 특정 함수를 활용하여 의도적으로 자료형을 변환하는 경우

* **int**
  
  * str*, float => int
  
    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118015328036.png" alt="image-20220118015328036" style="zoom:67%;" />
  
* **float**
  
  * str*, int => float
  
    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118015415376.png" alt="image-20220118015415376" style="zoom:67%;" />
  
* **str**
  
  * int, float, list, tuple, dict => str



---



## 연산자(Operator)

### 1) 산술 연산자(Arthmetic Operator)

* 기본적인 사칙연산 및 수식 계산

| 연산자    | 내용                               |
| --------- | ---------------------------------- |
| //        | 몫                                 |
| %(modulo) | 나머지(홀 짝을 구분할때 자주 쓰임) |
| **        | 거듭제곱                           |

* 기본적인 사칙연산 및 수식 계산

  ```python
  print(5 % 2)
  ```

  1

  ```python
  print(divmod(5,2))
  quotient, remainder = divmod(5, 2)
  print(quotient, remainder)
  ```

  (2, 1)

  2 1

  

### 2) 비교 연산자(Comparison Operator)

* 값을 비교하며, True/False 값을 리턴

| 연산자                  | 내용                        |
| ----------------------- | --------------------------- |
| ==                      | 같음                        |
| !=                      | 같지 않음                   |
| is :label: OOP 할 때    | 객체 아이덴티티(OOP)        |
| is not :label: OOP할 때 | 객체 아이덴티티가 아닌 경우 |



### 3) 논리 연산자(Logical Operator)

| 연산자  | 내용                                |
| ------- | ----------------------------------- |
| A and B | A와 B 모두 True이면 True            |
| A or B  | A와 B 모두 False이면 False          |
| Not     | True를 False로, False를 True로 (역) |

* 일반적으로 비교연산자와 함께 사용됨

  ```python
  num = 100
  num >= 100 and num % 3 == 1
  ```

  True

* 논리 연산자 단축평가: 결과가 확실한 경우 두 번째 값은 확인하지 않는 것

  * and 연산에서 첫 번째 값이 False인 경우, 무조건 False
  * or 연산에서 첫 번째 값이 True인 경우, 무조건 True

  

### 4) 복합 연산자(In-place Operator)

* 연산과 대입이 함께 이루어진다

* 예시

  ```python
  cnt = 100
  cnt += 1
  print(cnt)
  ```

  101

  ```python
  cnt = 0
  while cnt < 3:
  	print(cnt)
  	cnt += 1
  ```

  0

  1

  2

  

  :bulb: **+= 뜻!**
  
  ```python
  cnt = cnt + 1
  cnt += 1
  
  # "+" 더하고 "=" 저장!
  ```
  
  cnt = 0이라고 했을 때, 
  
  cnt = 0 + 1 되어서 cnt = 1
  
  cnt += 1이어도 cnt =1
  
  같은거임! 
  
  cnt += (value) 만큼 더해서 다시 저장한다고 생각하면 됨.
  
  문자열도 가능!
  
  cnt = " "
  
  cnt += 'a'
  
  cnt = 'a'

### 5) 식별 연산자(Identity Operator)

* is 연산자를 통해 동일한 객체(object)인지 확인 가능하다
* :label: OOP에서 추가 학습할 예정



### 6) 멤버십 연산자(Membershipe Operator)

* 시퀀스 포함 여부 확인 :question:: 멤버십 연산자 in을 통해 특정 요소가 속해 있는지 여부를 확인

  * in

  * not in

    ```python
    # List
    1 in [3, 2]
    ```

    Flase

    ```python
    # Tuple
    4 in (1, 2, 'hi')
    ```

    False

    ```python
    # range
    -3 in range(3)
    ```

    False

    ```python
    # String
    'a' in 'apple'
    ```

    True

    ```python
    #not in
    'b' not in 'apple'
    ```

    True
    
    

### 7) 시퀀스형 연산자(Sequence Type Operator)

* **산술연산자 (+)**

  * 시퀀스 간의 concatenation(연결/연쇄)

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118020535004.png" alt="image-20220118020535004" style="zoom:67%;" />

* **반복연산자(*)**

  * 시퀀스(리스트, 튜플, 문자열)를 반복

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118020637935.png" alt="image-20220118020637935" style="zoom:67%;" />

  

### 8) 기타

#### 인덱싱(Indexing)

* 시퀀스의 특정 인덱스 값에 접근

* 해당 인덱스가 없는 경우 IndexError - 없는 인덱스에 접근한 것

  ```python
  [1, 2, 3][100]
  -----------------------------------------------------------------------------
  IndexError: list index out of range
  ```
  
  

#### :question:슬라이싱(Slicing)

* 문자열 슬라이싱 예제

  1) **시퀀스를 특정 단위로 슬라이싱**

  ```python
  # List
  [1, 2, 3, 5][1:4] #[1:4]에서 1은 포함, 4는 미포함(4-1까지)
  ```

  [2, 3, 5]

  ```python
  # 튜플
  (1, 2, 3)[:2]
  ```

  (1, 2)

  ```python
  #range
  range(10)[5:8]
  ```

  range(5, 8)

  ```python
  # 문자열
  'abcd'[2:4]
  ```

  

  2. **시퀀스를 k 간격으로 슬라이싱**

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118021043387.png" alt="image-20220118021043387" style="zoom:67%;" />

  3. **문자열 슬라이싱**

     s[2:5] => 'cde'

     s[-6:-2] => 'defg'

     s[2:-4] => 'cde'

     s[2:5:2] => 'ce'

     s[-6:\-1:3] => 'dg'

     s[2:5:-1] => ' '

     s[5:2:-1] => 'fed'

     s[:3] => 'abc'

     s[5:] => 'fghi'

     s[::] => 'abcdefghi' .............. s[0:len(s):1]과 동일

     s[::-1] => 'ihgfedcba' .............. s[-1:-(len(s)+1):-1]과 동일

  | heading | a    | b    | c    | d    | e    | f    | g    | h    | i    |
  | ------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
  | index   | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    |
  | index   | -9   | -8   | -7   | -6   | -5   | -4   | -3   | -2   | -1   |



#### set 연산자

| 연산자 | 내용   |
| ------ | ------ |
| \|     | 합집합 |
| &      | 교집합 |
| -      | 여집합 |
| ^      | 대칭차 |

* **예시**

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118021541026.png" alt="image-20220118021541026" style="zoom:67%;" />



#### 연산자 우선순위

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118021638643.png" alt="image-20220118021638643" style="zoom: 67%;" />



---



## 프로그램 구성 단위

1.  함수(Function)
2. 모듈(Module)
3. 패키지(Package)
   - 프로그램과 모듈 묶음
4. 라이브러리(Library)























**기타**



Interpreter 언어 <-> Complie 언어

사람이 작성한 언어를 기계가 이해할 수 있게 해주는 것을 complier

파이썬은 중간에 interpreter가 존재

C, C++ 은 전체적으로 exe 파일 만든담에 실행

Python은 느림. 왜냐면 C나 C++은 실행 파일을 미리 만들어 놓으면, 그 다음 과정은 없음. 코드를 전체적으로 다 작성한 후에 한꺼번에 실행하는 것. 

그런데 Python은 ``a=2+2`` , ``print(a)``가 있으면 한 줄 읽고 실행, 읽고 실행, 읽고 실행...따라서 느림

