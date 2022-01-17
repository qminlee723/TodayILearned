# PYTHON



#### 변수(Variable)

* 컴퓨터 메모리 어딘가에 저장되어 있는 객체를 참조하기 위해 사용되는 이름
* 객체(object): 숫자, 문자, 클래스 등 값을 가지고 있는 모든 것
  * 파이썬은 객체지향 언어
* 동일 변수에 다른 객체를 언제든 할당할 수 있기 때문에, 즉, 참조하는 객체가 바뀔 수 있기 떄ㅜㅁㄴ에 변수라고 불린다. 
* type()
  * 변수에 할당된 값의 타입
* id()
  * 변수에 할당된 값(객체)의 고유한 아이덴티티 값



##### 변수 연산

* 숫자 연산

  ```python
  i = 5
  j = 3
  s = '파이썬'
  ```

  ```python
  i + j = 2
  ```

* 문자 연산

  ```python
  s * 3 = '파이썬파이썬파이썬'
  ```



##### 변수 할당

* 같은 값을 동시에 할당할 수 있음
* 다른 값을 동시에 할당할 수 있음(multiple assignment)



#### 실습 문제

x = 10, y = 20일 때, 각각 값을 바꿔서 저장하는 코드를 작성하시오

1)

```python
x, y = 10, 20
tmp = x
x = y
y = tmp
print(x, y)
```

2)

``` 
y, x = x, y
print(x, y)
```





#### 식별자(Identifiers)

* 변수(박스)의 이름ㅇ르 어떻게 지을 수 있을까?

* 파이썬 객체(변수, 함수, 모듈, 클래스 등)를 식별하는데 사용하는 이름(name)

* 규칙

  * 식별자의 이름은 영문 알파벳, 언더스코어, 숫자

  * RedApple: Camel case, Red_Apple: Snake case

  * 첫 글자에 숫자가 올 수 없음

  * 길이제한 X, 대소문자 구별

  * 다음의 키워드는 예약어(reserved words)로 사용할 수 없음

    ```
    False, None, True, and, as, assert, async, aswait, break, class, continue, def, del, elif, else, except, finally, for, from, global, if, import, in, is, lambda, nonlocal, not, or, pass, raise, return, try, while, with, yield
    ```

    ```
    print 등
    ```

    



* 사용자 입력

  * input([prompt])

  * 대괄호 부분에 문자열을 넣으면 입력시, 해당 문자열을 출력할 수 있다. 

  * 반환값은 항상 문자열의 형태로 반환

  * ```python
    name = input('이름을 입력해주세요: ')
    print(name)
    ```

  * ```
    이름을 입력해주세요 : 김싸피
    김싸피
    ```

    

* 주석

  * 한 줄 주석: #
  * 여러 줄 주석: \``` 
  * VS code: ctrl + /
  * 특수한 형태의 주석: docstring



#### 파이썬 자료형(Python Datatype)

##### None

* 값이 없음을 표현하기 위해

* ```
  print(type(None))
  ```

* ```
  a = None
  print (a)
  ```

  None



##### 불린(Boolean)

* True/False값
* 비교, 논리 연산을 수행할 시 활용
* 다음은 모두 False로 변환(비어 있는 것들)
  * 0, 0.0, (). [], {}, '', None
  * 단, bool([0]) = TRUE: 0이라는 값이 안에 들어있는 것이기 때문에 비어있는 것이 아님



##### 수치형(Numeric Type)

* Int(integer)

  * overflow: 데이터 타입별로 사용할 수 있는 메모리의 크기를 넘어서는 상황
  * 오버플로우가 발생하지 않음
  * **b**inary(0b), **o**ctal(0o), **h**exadecimal(0h)

* float(floating point number)

  * 정수가 아닌 모든 실수는 float

  * 부동소수점

  * ```python
    1e-1 = 0.1
    1/-10**100 = -1e-100
    10**100/3 = 3.33333333333e+99
    ```

  * **Floating point rounding error**: 값 비교하는 과정에서 정수가 아닌 실수인 경우 주의

    ```python
    #왼쪽의 계산 결과와 오른쪽 값은 같은 값일까요?
    3.14 - 3.02 == 0.12
    
    False
    
    3.14 - 3.02 
    0.1200000000000001
    ```

  * 매우 작은 수보다 작은지를 확인하거나 math 모듈 활용

    ```python
    #1. 임의의 작은 수
    abs(a - b) <= 1e-10
    
    True
    
    #2. system상의 machine epslion
    import sys
    print(abs(a - b) <= sys.float_info.epsilon)
    print(sys.float_info.epsilon)
    
    True
    2.220446049250313e-16
    
    #3. Python 3.5이상
    import math
    math.isclose(a, b)
    
    True
    ```

* complex(complex number:복소수)

  * 허수부를 j로 표현

  * ```python
    a = 3 + 4j
    print(type(a))
    ```

    <class 'complex'>

  * ```python
    a.real
    ```

    3.0

    ```python
    a.imag
    ```

    4.0



##### 문자열(String Type)

* 문자열은 작은 따옴표나 큰 따옴표를 활용하여 표기 

* Immutable

  * 불변하다

    ```python
    a = 'my string?'
    a[-1] = '!'
    ----------------------------------------------------------------------
    TypeError: 'str' object does not support item assignment
    ```

  * 특정 값 하나만 바꿀 수 없다!

* Iterable

  * ```
    a = '123'
    for char in a:
    	print(char)
    ```

    1

    2

    3

* 중첩따옴표(Nested Quotes)

  * 따옴표 안에 따옴표를 표현할 경우

  * 작은 따옴표가 들어 있는 경우는 큰 따옴표로, 큰 따옴표가 들어 있는 경우는 작은 따옴표로(중복되지 않게) 사용한다

    ```
    print("문자열 안에 '작은 따옴표'를 사용하려면 큰 따옴표로 묶는다.")
    ```

    

* 삼중따옴표(Triple Quotes)

  * 

* Escape sequence

  * 문자열 내에서 특정 문자나 조작을 위해서 역슬래시(\)를 활용해서 구분

  * | 예약문자 | 내용(의미)      |
    | -------- | --------------- |
    | \n       | 줄 바꿈         |
    | \t       | 탭              |
    | \r       | 캐리지리턴      |
    | \0       | 널(Null)        |
    | (\\)\    | \\ 표기         |
    | \\'      | 단일인용부호(') |
    | \\"      | 이중인용부호(") |

    ```
    print(철수\'안녕\'')
    ```

    철수 '안녕'

    ```
    print('이 다음은 엔터.\n그리고 탭\t탭')
    ```

    이 다음은 엔터.

    그리고 탭 탭

    

* String Interpolation

  * 문자열 사이에 변수

  * 문자열을 변수를 활용하여 만드는 법

    * %-formatting: 대부분의 타 프로그래밍의 언어에서 사용

      ```
      print('Hello, %s' % name)
      print('내 성적은 %d' % score)
      print('내 성적은 %f' % score)
      ```

      Hello, Kim

      내 성적은 4

      내 성적은 4.500000

    * str.format()

      ```python
      print('Hello, {}! 성적은 {}'.format(name, score))
      ```

      Hello, Kim! 성적은 4.5

    * f-strings : python 3.6+

      ```python
      print(f'Hello, {name}! 성적은 {score}')
      ```

      ```
      60p/156[]
      ```



#### 컨테이너형

* 여러 개의 값을 담을 수 있는 것(객체)으로, 서로 다른 자료형을 저장할 수 있음.

  * ex. List, tuple
  * Ordered/Unordered
  * 순서가 있다 != 정렬되어 있다

  ![image-20220117110240905](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220117110240905.png)

  

  ##### List

  * 순서를 가지는 0개 이상의 객체를 참조하는 자료형

  * 생성된 이후 내용 변경이 가능하다 (가변자료), 유연성이 높다

  * 항상 **대괄호[]** 형태로 출력

  * 생성과 접근

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

  * List 예시

    ```
    boxes = ['A', 'B', ['apple', 'banana', 'cherry']]
    ```

    ![image-20220117102216300](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220117102216300.png)



##### Tuple

* 순서를 가지는 0개 이상의 객체를 참조하는 자료형

* 생성 후, 담고있는 객체 변경이 불가능하다(immutalbe) 

* 항상 소괄호 형태로 출력

* 생성과 접근

  * 소괄호(()) 혹은 tuple()을 통해 생성

  * 튜플은 수정이 불가능(immutable) 시퀀스로 인덱스로 접근 가능하다

    * 값에 대한 접근은 my_tuple[i]

  * 튜플 생성 주의사항

    * 단일 항목의 경우

      - 하나의 항목으로 구성된 튜플은 생성 시 값 뒤에 쉼표를 붙여야 함

    * 복수 항목의 경우

      ```python
      a = 1, 
      print(a)
      print(type(a))
      ```

      (1,)

      <class 'tuple'>

      ```python
      b = 1, 2, 3
      print(b)
      print(type(b))
      ```

      (1, 2, 3)

      <class 'tuple'>

      

  * 튜플 대입

    * 우변의 값을 좌변의 변수에 한번에 할당하는 과정

  * 튜플은 일반적으로 파이썬 내부에서 활용

    * 추후 함수에서 복수의 값을 반환하는 경우에도 활용

      ```
      x, y = 1, 2
      print(x, y)
      ```

      1, 2

      ```
      #실제로 tuple로 처리
      x, y = (1, 2)
      print(x, y)
      ```

      1 2



##### 레인지(Range)

* 숫자의 시퀀스를 나타내기 위해 사용

* **기본형**

  

  * range(n)	

    0부터 n-1까지의 숫자 시퀀스

  * range(n, m)

    n부터 m-1까지의 숫자 시퀀스

  * range(n, m, s)

    n부터 m-1까지 s마늠 증가시키는 숫자 시퀀스

  * 예제 84/156

  * 

##### 패킹/언패킹 연산자(Packing/Unpacking Operator)

​	모든 시퀀스형(리스트, 튜플)은 패킹/언패킹 연산자 *를 사용하여 객채의 패킹 또는 언패킹 가능

​	*"순서"가 포인트*, but 잘 안씀

​	x, *y = i , j, k ...

* 패킹

  * x, *y = i, [j, k, ...]

* 언패킹

  * argument 이름이 *로 시작하느 ㄴ경우, argument unpacking이라고 함

  * 패킹의 경우, 리스트로 대입

  * 언패킹의 경우, 튜플 형태로 대입

  * ```python
    def multiply(x, y, z):
    	return x * y * z
    ```

    ```python
    numbers = [1, 2, 3]
    multiply(*numbers)
    ```

    6

  * 언패킹의 경우, 튜플형태로 대입

* 주의사항

  * *가 곱셈을 의미하는지, packing/unpacking을 의미하는지 구분
  * packing/unpacking 연산자
    * 대입식(numbers)의 좌측에 위치(*numbers)
    * 하나로만 보이는 경우(단항 연산자)
  * 곱셈
    * 두개짜리 항의 식에서 중간에 있는 경우
    * ex) a * b



#### 비시퀀스형 컨테이너 (Associative Container)

##### Set

* 순서없이 0개 이상의 해시가능한 객체를 참조하는 자료형
* 해시가능한 객체(immutable)만 담을 수 있다.
* 담고 있는 객체를 삽입 및 변경 가능(mutable)
* 수학에서의 집합과 동일한 구조를 가진다
* 집합 연산이 가능
* 중복된 값이 존재하지 않음

* 셋 생성

  * 중괄호({}) 혹은 set()을 통해 생성
  * 순서가 없어 별도의 값에 접근할 수 없음

* 셋 활용

  * 셋을 활용하면 다른 컨테이너에서 중복된 값을 쉽게 제거할 수 있다

  * 단, 순서가 중요한 경우 사용불가능

  * 예제) 아래의 리스트에서 고유한 지역의 개수는?

    ```python
    my list = ['서울', '서울', '대전', '광주', '서울', '대전', '부산', '부산']
    ```

    ```python
    len(set(m_list))
    ```

    4

  * 예제) 이를 등장한 순서대로 출력하시오

    ```python
    set(my_list)
    ```

    ('광주', '대전', '부산', '서울')

    * 이처럼 set을 사용하는 순간 순서가 사라진다. 순서가 중요하면 set 사용하면 안됨

    

##### Dictionary

순서 없이 키 - 값(key - value) 쌍으로 이루어진 객체를 참조하는 자료형

Dictionary 의 키(key) - 해시 가능한 불변 자료형만 가능

각 키의 값(values) - 어떠한 형태든 관계 없음

* 딕셔너리 생성

  * 중괄호({}) 혹은 dict()

    ```python
    dict_a = {}
    print(type(dict_a))
    ```

    ```python
    dict_b = dict()
    print(type(dict_b))
    ```

  * Key 와 value가 쌍으로 이루어진 자료구조

    * key는 변경 불가능한 데이터(immutable)만 활용이 가능
    * string, integer, float, voolean, tuple, range
    * value는 모든 값으로 설정이 가능하다(list, dictionary)



#### Typecasting(형 변환)

##### 자료형 변환

* 암시적 형 변환(implicit)

  * 사용자가 의도하지 않고, 파이썬 내부적으로 자료형으로 변환하는 경우

  * bool/Numeric Type

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

    

* 명시적 형 변환(explicit)

  * 사용자가 특정 함수를 활용하여 
  * int
    * str*, float => int
  * float
    * str*, int => float
  * str
    * int, float, list, tuple, dict => str
  * 



#### 연산자(Operator)

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

* 비교연산자(Comparison Operator)

  | 연산자 | 내용      |
  | ------ | --------- |
  | ==     | 같음      |
  | !=     | 같지 않음 |

* 논리 연산자(Logical Operator)

  | 연산자  | 내용                                |
  | ------- | ----------------------------------- |
  | A and B | A와 B 모두 True이면 True            |
  | A or B  | A와 B 모두 False이면 False          |
  | Not     | True를 False로, False를 True로 (역) |

* 복합 연산자(In-place Operator)

  * 연산과 대입이 함께 이루어진다

* 식별 연산자(Identity Operator)

  * is 연산자를 통해 동일한 객체(object)인지 확인 가능하다

* 멤버십 연산자(Membershipe Operator)

  * 포함 여부 확인

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

* 시퀀스형 연산자(Sequence Type Operator)

  * 반복연산자(*)
  * 시퀀스를 반복(리스트, 튜플, 문자열) .. range는 안됨

* 기타

  * 인덱싱(Indexing)

    * 시퀀스의 특정 인덱스 값에 접근

    * 해당 인덱스가 없는 경우 IndexError - 없는 인덱스에 접근한 것

      ```
      [1, 2, 3][100]
      ```

      IndextError

  * 슬라이싱(Slicing)

    * 문자열 슬라이싱 예제

      ```
      # List
      [1, 2, 3, 5][1:4]
      ```

      [2, 3, 5]

    * s[2:5] => 'cde'

      s[-6:-2] => 'defg'

      s[2:-4] => 'cde'

      s[2:5:2] => 'ce'

      s[-6:\-1:3] => 'dg'

      s[2:5:-1] => ' '

      s[5:2:-1] => 'fed'

      s[:3] => 'abc'

      s[5:] => 'fghi'

      | heading | a    | b    | c    | d    | e    | f    | g    | h    | i    |
      | ------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
      | index   | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    |
      | index   | -9   | -8   | -7   | -6   | -5   | -4   | -3   | -2   | -1   |

  * set 연산자

    | 연산자 | 내용   |
    | ------ | ------ |
    | \|     | 합집합 |
    | &      | 교집합 |
    | -      | 여집합 |
    | ^      | 대칭차 |

    * 예시

      ```
      A_set = {1, 2, 3, 4}
      B_set
      ```

      







1. 박스가 무엇인지
2. 박스에 할당
3. 박스에 레이블링
4. ? 가의 타입들





1. 숫자
2. boolean
3. none
4. string: 문자열의 나열
5. list: 요소들의 시퀀스
6. tuple: 변경불가능한 요소들의 시퀀스
7. set: 중복없는 요소들의 시퀀스
8. {k:v} dictionary: key-value조합의 시퀀스
9. 







Interpreter 언어 <-> Complie 언어

사람이 작성한 언어를 기계가 이해할 수 있게 해주는 것을 complier

파이썬은 중간에 interpreter가 존재

C, C++ 은 전체적으로 exe 파일 만든담에 실행

Python은 느림. 왜냐면 C나 C++은 실행 파일을 미리 만들어 놓으면, 그 다음 과정은 없음. 코드를 전체적으로 다 작성한 후에 한꺼번에 실행하는 것. 

그런데 Python은 ``a=2+2`` , ``print(a)``가 있으면 한 줄 읽고 실행, 읽고 실행, 읽고 실행...따라서 느림





## CS 도서 추천: 재미있는거!



