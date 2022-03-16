# Python_TEST



## :one: 파이썬 기초



### 1. 데이터 타입

<img width="634" alt="자료형" src="https://user-images.githubusercontent.com/45934087/148158891-fe28256b-1df4-4b83-ab51-54d06c107d20.png">



* Python은 임의 정밀도 산술(Arbitrary-precision arithmetic)을 사용하기 때문에, integer에서 오버플로우가 없음



### 2. Float

```python
# Round() 쓰기: 소숫점 두 자리 수까지

c = 3.5 - 3.12
round(c, 2)
```

```python
a = 3.5 - 3.12
b = 0.38

abs(a - b) <= 1e-10
```

```python
import sys
abs(a - b) <= sys.float_info.epsilon
```



### 2. String Interpolation

* %-formatting

  ```python
  name = '이규민'
  score = 100
  
  print('%s이고, %d이 목표입니다' % (name, score))
  ```

* str.format()

  ```python
  str.format(name)
  ```

* f-string

  ```python
  print(f'My name is {name}')
  ```



* datetime

  ```python
  import datetime
  today = datetime.datetime.now()
  print(today)
  
  print(f'오늘은 {today:%y}년 {today:%m}월 {today:%d}일 {today:%A}')
  ```

  

* 원주율

  ```python
  pi = 3.141592
  
  print(f'원주율은 {pi:.2f}, 반지름이 2일 때 원의 넓이는 {2*2*pi}')
  ```

  

### 3. 컨테이너

<img width="712" alt="container" src="https://user-images.githubusercontent.com/45934087/148164052-3b12d3a2-a95e-4d4d-ae25-86ca1ba9657b.png">

* 튜플 쓸 때 요소 하나만 쓸 때는 뒤에 ',' 꼭 써줄 것

  ```python
  ('a',)	# comma 없으면 에러남
  ```

  

### 4. 종류

* Iterable한 것
  * numeric type 제외 모두
  * dictionary, tuple, list, set... etc
* Index 있는 것(순서 있는 것) : iterable 하지 않으면 indexing X
  * 있는 것 : list, tuple, string
  * 없는 것 : dict, set {}
* Immutable
  * immutable: tuple, range, string
  * mutable : list, dict, set(add, delete가 가능한 것)
* 차이점 
  * set 특성: 중복이 없다
  * dict의 특성: key: value



### 5. 비시퀀스(non-sequence)형 컨테이너

* Set
  * 교집합 &
  * 합집합 |
  * 차집합 -
  * 중복된 값이 있을 수 없다
* Dictionary
  * .keys() : dictionary의 key 목록 확인 가능
  * .values() : value 목록을 확인 가능
  * .items : key와 value 목록 확인 가능



### 6. 형변환(Typecasting)

<img width="708" alt="typecasting" src="https://user-images.githubusercontent.com/18046097/61180466-a6a67780-a651-11e9-8c0a-adb9e1ee04de.png">

* 결론: range랑 dictionary만 안된다
* True = 1 인 것은 자동적은 형변환



### 7. 복합 연산자

![image-20220203004655861](images\image-20220203004655861.png)



### 8. 식별 연산자

* **is** 연산자

* 파이썬에서 -5부터 256까지의 id는 동일

* 257이후의 id는 각각 다르다

  ![image-20220203005023726](images\image-20220203005023726.png)



### 9. 멤버십 연산자

* **in** 연산자, **not in** 연산자
* 요소가 **시퀀스**에 속해있는지 확인할 수 있음



### 10. 시퀀스형 연산자

* 산술형 연산자(+), 반복 연산자(*)

* 슬라이싱 

* range는 시퀀스형 연산자 사용 불가능

* integer + 'string'도 불가능

* slicing 

  ```python
  print([1, 2, 3, 4][1:4])
  print((1, 2, 3)[:2])
  print(range(10)[5:8])
  print('abcd'[2:4])
  
  # [2, 3, 4]
  # (1, 2)
  # range(5, 8)
  # cd
  ```

* slicing vs range

  | slicing                                 | range                          |
  | --------------------------------------- | ------------------------------ |
  | [첫번째 포함안함 : 끝나는 숫자 : 스텝 ] | ( 시작, 끝나는 숫자 + 1, 스텝) |



### 11. 프로그램 구성 단위

* 식별자(identifier)
* 리터럴(literal)
* 표현식(expression)
* 문장(statement)
  * 문장이 표현식 포함
* 함수(function) : 특정 명령을 수행하는 함수 묶음 
* 모듈(module) : 함수, 클래스의 모음. 하나의 프로그램을 구성하는 단위(file)
* 패키지(package) : 프로그램과 모듈의 묶음(folder, directory)
* 라이브러리(library) : 패키지의 묶음





## :two: 제어문

### 1. 조건 표현식 작성하기

* 이게 결과야, 이게 조건이면. 아니면 이거야



### 2. for 문

* 시퀀스(string, tuple, range, list)를 포함한 iterable한 객체 요소들을 순회합니다

* 딕셔너리에 for 문을 실행하면 기본적으로 value 값이 나옴

* 딕셔너리에서 for를 활용하는 4가지 방법

  ````python
  # 0. dictionary 순회 (key 활용)
  for key in dict:
      print(key)
      print(dict[key])
  
  
  # 1. `.keys()` 활용
  for key in dict.keys():
      print(key)
      print(dict[key])
  
  
  # 2. `.values()` 활용
  # 이 경우 key는 출력할 수 없음
  for val in dict.values():
      print(val)
  
  
  # 3. `.items()` 활용
  for key, val in dict.items():
      print(key, val)
  ````

### 3. Enumerate

* 인덱스와 객체를 쌍으로 담은 열거형 객체 반환

* index, value형태의 tuple로 구성된 열거 객체를 반환한다.

  ```python
  members = ['민수', '영희', '철수']
  
  for i, mem in enumerate(members, start=1):
      print(i, mem)
  ```

### 4. List/Dict Comprehension

* [expression for 변수 in iterable]

  ```python
  # 1~3의 세제곱 리스트 만들기
  cubic_list = []
  for number in range(1, 4):
      cubic_list.append(number ** 3)
      
  # List Comprehension
  a = [number ** 3 for number in range(1, 4)] 
      
  ```

* {key: value for element in iterable}

  ```python
  # 1~3의 세제곱 딕셔너리 만들기
  cubic = {}
  
  for number in range(1, 4):
      cubic[number] = number**3
  
  # Dictionary Comprehension
  a = {number: number**3 for number in range(1, 4)}
  ```



### 5. 반복제어

* Continue: continue 이후의 코드를 수행하지 않고, 다음 요소부터 계속하여 반복을 수행
* pass: 아무것도 하지 않는다. 들여 쓰기 이후 문장이 필요하지만, 프로그램이 특별이 할 일이 없을 때 자리를 채우는 용도로 사용가능
* else: 끝까지 반복문을 실행한 이후에 실행되며, 반복문이 break 문으로 종료될 때에는 실행되지 않는다.





## :three: 함수

### 1. 함수

* 특정한 기능을 하는 코드들의 묶음

* 함수를 쓰는 이유: 가독성, 재사용성, 유지보수 용이

* 함수의 선언은 def 키워드를 활용

* 함수는 동작 이후 return을 통해 반환

  * 오직 하나의 객채만 반환된다. 함수가 return 되거나 종료되면, 함수를 호출한 곳으로 돌아간다. 

  

### 2. 내장함수(built-in Functions)

* 내장함수 확인할 수 있는 함수: dir(\__builtins__)
* len, int, map, all, any, bool, chr, divmod, format, id, range..
* map:



### 3. 함수의 입력(input)

* 매개변수(parameter): 함수의 입력을 받아서 함수 내부에서 활용할 변수

* 전달인자(argument): 실제로 전달되는 "값"

  * 위치 인자(Positional)

    * (a, b)

  * 기본 인자(Default)

    * 입력된 값이 없을 때, 사용할 값을 정해 놓는 것
    * def function(a, b=0)

  * 키워드 인자

    * 함수를 호출할 때, 키워드 인자를 활용해서 직접 변수의 이름으로 특정 인자를 전달할 수 있다

    * def function(a, b)

      print('{a} 그리고 {b}')

  * 가변 인자 리스트(Arbitrary Argument Lists)

    * 갯수가 정해지지 않은 임의의 인자를 받기 위해서는 *args 활용
    * 가변 인자 리스트는 **tuple 형태**로 처리되며, 매개변수에 *로 표현된다. 
    * 일반적으로 매개변수 목록의 마지막에 온다.
    * def function(a, b, *args)

  * 가변 키워드 인자(Arbitrary Keyword)

    * 정해지지 않은 키워드 인자들은 함수를 정의할 때 **kwargs 활용

    * 가변 키워드 인자는 **dict 형태**로 처리되며, 매개변수에 **로 표현

    * 식별자는 숫자만으로는 이루어질 수 없다

    * Key가 숫자인 딕셔너리를 만들고 싶다면, 

      * dict([(1, 1), (2, 2)]) ===> {1: 1, 2: 2}

      

### 4. 함수와 스코프

```python
# 전역 스코프(global scope)
a = 10 # 전역 변수(global)

def func(b):
    # 지역 스코프(local scope)
    c = 20 # 지역 변수(local variable)
    print(a)
    print(b)

func(a)
```

* global scope:

  * 코드 어디에서든 참조할 수 있느 ㄴ공간

* local scope

  * 함수가 만든 스코프로, 함수 내부에서만 참조할 수 있느 ㄴ공간

* 이름 검색 규칙

  * 파이썬에서 사용되는 이름들은 이름공간에 저장되어 있다.
  * LEGB(Local, Enclosed, Global, Built-in)

  

### 5. 재귀함수

* 함수 내부에서 자기 자신을 호출하는 함수

* base case(종료되는 상황)가 반드시 존재해야 함

  * base case: 점점 범위가 줄어들어 반복되지 않는 최종적으로 도달하는 곳을 의미
  * 팩토리얼 계산에서의 base case는, n = 1일 때, 함수가 아닌 정수를 반환하는 것
  * base case에 도달할 때까지 함수를 호출하며
  * 메모리 스택이 넘치게 되면 프로그램이 멈춘다
  * 파이썬에서는 최대 재귀 깊이가 1000번으로, 호출 횟수가 이를 넘어가면 Recursion Error 발생

* 피보나치 수열

  * 만약 현재 단계가 2단계보다 작으면 그냥 현재 단계를 반환합니다

  * 그렇지 않다면, 전단계의 재귀함수  + 전전단계의 재귀함수의 결과를 반환

    ```python
    def fib(n):
        if n < 2:
            return n
        else:
            return fib(n-1) + fib(n-2)
    ```

* 반복문과 재귀함수의 차이

  * 알고리즘 자체가 재귀적인 표현이 자연스러운 경우
  * 재귀 호출은 변수 사용을 줄여줄 수 있다
  * 입력값이 커질수록 속도가 오래 걸린다.



### 6. 함수 응용

* map(function, iterable)
  * iterable의 모든 요소에 function을 적용한 후 그 결과를 돌려주는 것
  * return은 map_object형태
* fliter(function, iterable)
  * iterable에서 function의 반환된 결과가 True인 것들만 구성해서 반환
  * filter object를 반환
* zip(*iterables)
  * 복수의 iterable을 모아 zip()줍니다
  * 튜플의 모음으로 구성된 zip object를 반환
* lambda 
  * 표현식을 계산한 결과 값을 반환하는 함수로, 이름이 없는 함수여서 익명함수라고도 불린다.
  * return 문을 가질 수 없고, 간단한 조건문 외의 구성이 어렵다
  * 함수의 정의해서 사용하는 것보다 간결하게 사용이 가능하다.



## :four: 모듈

### 1. 모듈 

* 특정 기능을 하는 코드를 담고 있는 파일
* 활용
  * import 문을 통해 내장 모듈을 이름공간(namespace)으로 가져와야 한다
  * import문이 사용된 코드의 위치에 따라 namespace가 결정

### 2. 패키지

* 하나의 디렉토리에 모듈이 모여있는 형태
* 패키지.모듈
*  모든 폴더에는 \_\_init\_\_.py를 만들어 패키지로 인식(python 3.3 부터는 파일이 없어도 되지만, 하위 버전 호환 및 프레임워크 등에서의 동작을 위해 파일 생성을권장한다. )

### 3. 가상환경

* virtual environment: venv
* 복수의 프로젝트를 하는 경우, 버전이 상이할 수 있으므로 가상환경을 만들어서 프로젝트별로 독립적인 패키지를 관리할 수 있다.

### 4. 라이브러리 > 패키지 > 모듈 > 함수



## :five: 메서드

### 1. 순서가 있는 데이터 구조

* String
  * s.find(x): x의 첫 번째 위치를 반환, 없으면 -1을 반환
  * s.index(x): x의 첫번째 위치를 반환, 없으면 오류
  * s.isalpha: 알파벳 문자 여부
  * s.split: 공백이나 특정 문자를 기준으로 분리
* List
  * l.append(x): 리스트 마지막 항목에 x를 추가
  * l.extend(x): 리스트 마지막 항목에 x의 iterable을 추가
  * l.inster(i, x):리스트 인덱스 i에 항목 x를 삽입
  * l.remove(x): 리스트 가장 왼쪽에 있는 항목 x를 제거
  * l.pop(x): 리스트 가장 오른쪽에 있는 항목을 반환 후 제거
  * l.sort(...): 리스트 정렬
  * l.count(x): 리스트에서 항목 x 가 몇 개 존재하는지 갯수를 반환
* Tuple
  * 변경할 수 없기 때문에, 값에 영향 미치지 않는 메소드만을 지원한다

### 2. 순서가 없는 데이터 구조

* Dictionary
  * d.keys(): dict의 모든 키를 담은 뷰 반환
  * d.values(): dict의 모든 값을 담은 뷰 반환
  * d.items(): dict의 모든 키-값 쌍을 담은 뷰 반환
  * d.get(k): k 키 값을 반환
  * d.pop(k): 키 k의 값을 반환하고, 키 k 항목을 딕셔너리에서 삭제
* Set
  * s.add(x): 항목x가 set에 없다면 추가
  * s.pop(): set에서 랜덤하게 항목을 반환하고, 해당 항목을 제거
  * s.update(*others): 여러 값을 추가

### 3. 할당

*  같은 메모리 주소를 각자 다른 리스트가 가리키게 한 것
* 메모리 효율적

### 4. 얕은 복사

* 같은 원소를 가진 리스트를 다른 주소에다 복사
* 다른 주소가 같은 리스트를 바라보는 것

### 5. 깊은 복사

* 원래의 리스트에 다시 접근하고 싶을 경우를 대비하여, 오리지널을 남겨 놓는 것
* 메모리를 새롭게 할당해서 copy list가 새로운 메모리를 바라보게 하는 것
* 용량 많이 잡아먹음



## :six: 에러 & 예외처리

### 1. 에러

* NameError: 어느 곳에서도 정의되지 않은 변수를 호출한 경우 발생

* TypeError

  * 자료형이 올바르지 못한 경우
  * 필수 매개변수가 누락된 경우
  * 매개변수 갯수가 초과한 경우

* ValueError

  * 자료형은 올바르나 값이 적절하지 않은 경우
  * 존재하지 않는 값을 찾고자 할 경우

* ImportError

  * 모듈은 찾았으나, 존재하지 않는 클래스/함수를 가져오는 경우

  

### 2. 예외 처리

* try
  * 예외가 발생되지 않으면 except없이 실행 종료
* except
  * 예외 발생되면 남은 부분 실행하지 않고 except 실행
* else
  * 모든 except절 뒤에 와야 함
  * 에러가 발생하지 않는 경우 사용
  * try절이 예외를 일으키지 않을 때 실행되어야만 하는 코드
* finally
  * 반드시 수행해야 하는 문장
  * 모든 상황에 실행되어야 하는 코드
  * 예외의 발생여부에 관계 없이, try문을 떠날 때 항상 실행
* as
  * 에러 메시지 보여줄 때 

### 3. 예외 발생 시키기

* raise
  * 예외를 강제로 발생시키기



## :seven: OOP

### 1. 객체 지향 프로그래밍

* 객체
  * 모든 객체는 Type, Attribute, Method를 가진다
* 객체지향 프로그래밍
  * 컴퓨터 프로그램을 여러 개의 독립된 단위, 즉 객체들의 모임으로 파악하고자 하는 것
  * 코드의 직관성, 활용의 용이성, 변경의 유연성

### 2. OOP 기초

* class
  * 공통된 속성(attribute)과 조작법(method)을 가진 객체들의 분류
* instance
  * 특정 클래스의 실제 데이터 예시 
  * 파이썬에서 모든 것은 객체이고 모든 객체는 특정 클래스의 인스턴스
* attribute
  * 특정 데이터 타입 또는 클래스의 객체들이 가지게 될 상태/데이터 
* method
  * 특정 객체가 할 수 있는 행위(behavior)

### 3. 인스턴스

* 인스턴스 변수

  * 인스턴스의 속성/고유한 데이터

* 인스턴스 메소드

  * 인스턴스가 사용할 메서드
  * 메서드 호출시, 첫번째 인자로 인스턴스 자기자신에 해당하는 self가 전달됨

* self

  * 인스턴스 메서드는 호출 시 첫번째 인자로 인스턴스 자신이 전달되게 설계

* 생성자 & 소멸자

* 매직메서드

  

### 4. 클래스

* 클래스 생성
* 클래스 변수
* 클래스 메서드
* 스태틱메서드
  * 호출시 어떠한 인자도 전달받지 않음
* :star: namespace
  * 클래스르 정의하면, 클래스와 해당하는 이름공간이 생성된다
  * 인스턴스를 만들면, 인스턴스 객체가 생성되고 이름 공간이 생성된다
  * 인스턴스에서 특정 속성에 접근하면, 인스턴스 -> 클리스 순으로 탐색한다.



### 5. OOP의 핵심 개념

* 추상화(Abstraction)
  * 세부적인 내용 외에 필수적인 부분만 표현하는 것
* 상속(Inheritance)
  * 코드 재사용성 높아짐
  * 상속받은 메서드를 재정의 - 메서드 오버라이딩
* 다형성(Polymorphism)
  * 동일한 메서드가 클래스에 따라 다르게 행동할 수 있음
  * 서로 다른 클래스에 속해있는 객체들이 동일한 메시지에 대해 각기 다른 방식으로 응답될 수 있음
* 캡슐화(Encapsulation)
  * 객체의 일부 구현 내용에 대해 외부로부터의 직접적인 액세스를 차단하는 것
  * 암묵적으로는 존재하지만, 언어적으로는 존재하지 않음
  * 접근제어자
    * public Access Modifier 아무것도 없음
    * protected 언더바 하나
    * private 언더바 둘
* getter
  * @property
  * 변수의 값을 읽는 메서드
* setter
  * @변수.setter
  * 변수의 값을 설정하는 메서드
* 다중상속
  * 두 개 이상의 클래스를 상속받는 경우
  * 중복된 속성이나 메서드가 있는 경우, 상속 순서에 의해 결정된다. 
* 상속 관계에서의 이름공간과 Method Resolution Order(MRO)
  * 인스턴스 -> 자식클래스 -> 부모클래스
  * 해당 인스턴스의 클래스가 어떤 부모클래스를 가지는지 확인하는 속성 또는 메서드.





## TIP(30문제)

* 지엽적인 문제 안나온다. 큰 틀에서 보기
* 1. 각 자료형의 특징(mutable, immutable..)
* 2. 부울형(boolean) - 자동형변환에 대해서 알면됨([], '')
*  List, set의 메서드(append 등 자주 쓰는 메서드), enumerate같은거
* 반복문, 조건문은 index 문제 :star: 
  * 끝이 포함되는지 안되는지
  * 어디까지 도는지
* 자주 쓰는 내장함수, len, int, map같은거: 어떤 함수인지 알면됨
* 재귀함수가 어떻게 풀리는가?
  * 언제 다시 자기를 부르는지
  * 인자가 n이었다면, 밑의 인자에는 뭘 넘겨주고 어떻게 변하는가?
  * return할 때 뭘 return해주는가?
  * n = 0, n =1 다 넣어보기
* OOP
  * global 과 local의 차이(namespace 범위)
  * class 문제
    * 상속 받았을 때 이 변수는 어떻게 변하는지 등