# Python Function

## 함수 기초

### 함수의 정의

* :star: 사용자 함수(Custom Function) 구현되어 있는 함수가 없는 경우, 사용자가 직접 함수 작성

  ```python
  def function_name(parameter):
  	# code block
  	return returning value
  ```

  

### 함수를 사용해야 하는 이유

* 코드 중복 방지
* 재사용 용이



### 함수 기본 구조

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220119092024266.png" alt="image-20220119092024266" style="zoom: 50%;" />

1) 선언과 호출(define & call)

   * **def 함수명()**

   * parameter가 있는 경우, 함수명(값1, 값2, ...)로 호출

   * 예시

     ```python
     def add(x, y):
     	return x + y
     	
     add(2, 3)
     print(add)
     ```

     <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220119093121886.png" alt="image-20220119093121886" style="zoom:50%;" />

2) 입력(input)

3) 문서화(doc-string)

   * docstring 호출 시: help ..

4) 범위(scope)

5) 결과값(output)



### 실습)

1. 입력 받은 수를 세제곱하여 반환하는 함수 cube를 작성하시오
2. 함수 cube를 활용하여 2의 세제곱, 100의 세제곱을 구하시오

```python
# 숫자를 받아서(input)
# 세제곱 결과를 반환(output)

def cube(number):	#cube:함수이름, number:input이름
	return number ** 3 #**3: 로직

print(cube(2), cube(100))
```











## 함수의 결과값(Output)

### 1. Void function

* 명시적인 return 값이 없는 경우, none을 반환하고 종료

  ```python
  a = print('hello python')
  ```

  hello python

* 예시

  ```python
  
  ```

  ```
  ```

  

### 2. Value returning function

* 함수 실행 후, return문을 통해 값을 반환

* return을 하게 되면, 값 반환 후 함수가 바로 종료

  ```python
  b = float('3.14')
  ```

  3.14

* Out(이건 출력된 게 아니라 마지막에 반환된거야!)

  ```python
  a = print('hello')
  b = float('3.5')
  
  print(a, b)
  ```

  hello

  None 3.5

* return 과 print 구분 중요!

  * return은 함수 안에서만 사용
  * print는 출력을 위해 사용
  * REPL(ex. Jupyter Notebook)환경에선 마지막으로 작성된 코드의 리턴 값을 보여줌

* 두 개 이상의 값 반환

  * 아래 코드의 문제점은 무엇일까?

    ```python
    def minus_and_product(x, y):
    	return x - y 
    	return x * y
    ```

    ```python
    y = minus_and_product(4, 5)
    y
    ```

    -1

    

    * 위에서 아래로 내려오기 때문에 return을 만나는 순간 종료가 된다. 

  * 값을 두개 다 print하고 싶으면?

    ```python
    def m(x, y):
    	return x - y, x * y
    
    print(m(1, 2))
    ```

    (-1, 20)

    * return문은 항상 하나만 반환하지만, 튜플 형식으로 반환한다.  :question: why?

* 함수 실습 문제: 사각형 넓이 구하기

  * 너비와 높이를 입력 받아 사각형의 넓이와 둘레를 튜플로 반환하는 함수 rectangle을 작성하시오.

  * 함수 rectangle을 활용하여 아래 사각형의 넓이를 구하시오(가로: 30, 세로: 20)

    ```python
    def rectangle(width, height):
    	pass width * height, (width + height) * 2
    
    print(rectangle(30, 20))
    # => (600, 100) 하나의 튜플이다!
    ```

    



## 함수의 입력(Input)

### Parameter(매개변수, 인수)

* 함수 내부에서 사용되는 식별자(매개변수이자 인수)
* 정의할 때

### Argument(전달인자, 인자)

* 함수를 호출할 때 함수의 parameter를 통해 전달되는 값

```python
def function(ham): # parameter: ham (이름)
	return ham
	
function('spam')	# argument: 'spam' (값)
```



#### 1. Argument

* 함수 호출 시 함수의 parameter를 통해 전달되는 값

* 소괄호 안에 할당 func_name(argument)

  * 필수 Argument: 반드시 전달되어야 하는 argument
  * 선택 Argument: 값을 전달하지 않아도 되는 경우는 기본 값이 전달

  

#### 2. Positional Arguments

* 기본적으로 함수 호출 시 Argument는 위치에 따라 함수 내에 전달됨

  ```python
  def add(x, y)
  # x = 2; y = 3 =======> Positional Arguments
  	return x + y
  	
  print(add(2, 3)) # Positional Arguments - 내부에서 바인딩 x = 1; y = 2
  ```

  

#### 3. Keyword Arguments(호출)

* 직접 변수의 이름으로 특정 Argument를 전달할 수 있음

* **Keyword Argument 다음에 Positional Argument를 사용할 수 없음**

  ```python
  print(add(y=2, x=1)) # Keyword Arguments - 직접 x와 y값을 각각 지정
  print(add(x=1, 2)) # SyntaxError : positional argument follows keyword argument 키워드로 지정하는 순간 위치가 이미 의미가 없어짐
  print(add(1, y=2)) # 위치 지정.. 키워드 두번째는.. 괜찮음
  ```



#### 4. Default Arguments Values(정의)

* 기본값을 지정하여 함수 호출 시 argument 값을 설정하지 않도록 한다

* 정의된 것보다 더 적은 갯수의 argument들로 호출될 수 있음

  ```python
  def add(x, y=0)
  	return x + y
  	
  add(2)
  
  def add(x, y=0):
  	x = 2
  	return x + y
  ```

  

#### 5. :question: 정해지지 않은 여러 개의 Arguments 처리

##### Positional Arguments Packing/Unpacking 

* Positional Arguments Packing/Unpacking 연산자(*)
  * 여러 개의 Positional Argument를 하나의  필수 parameter로 받아서 사용. **튜플**
* 예제

```python
print("func1")
func(a)
```

1

2

3

```python
def func2(*x)
	print(x)
	for i in x:
		print(i)
print("func2")
func2(a)
```

func2

:question: ([1, 2, 3],)

[1, 2, 3]

```python
def func3(name, *args, number):
	print(name)
	print(args)
	print(number)
	
func3("aiden", 1, 2, 3)
---------------------------------------------
TypeError: fun3() missing 1 required keyword-only arguemnt: 'number'
        
def func3(name, *args, number=100):
	print(name)
	print(args)
	print(number)
	
func3("aiden", 1, 2, 3)        
```

aiden

(1, 2, 3)

100



##### Keyword Arguments Packing/Unpacking

* Keyword Arguments Packing/Unpacking 연산자(**)

  * 함수가 임의의 개수 Argument를 Keyword Argument로 호출될 수 있도록 지정

  * Argument들은 **딕셔너리**로 묶여 처리되며, parameter에 **를 붙여 표현

    ```python
    def family(**kwargs):
    	for key, value in kwargs:
    		print(key, ":", value)
            
    family(father='john', mother'jane', me='john jr.')
    ```

    :question: error!!

    ```python
    def family(**kwargs):
    	for key, value in kwargs.items():
    		print(key, ":", value)
            
    family(father='john', mother'jane', me='john jr.')
    ```

    :question: 왜 father는 'father'이 아닐까? 왜냐면 father은 variable의 형태를 가지므로

6. 정해지지 않은 여러 개의 Arguments 처리

   ```python
   print('hi', 'hello', '안녕', 'guten morgen', 'bon jour')
   
   def add(*args):
       print(args, type(args))
   
   print(add(1, 2, 3))
   print(add(1))
   ```

   

   

   

##### 함수 <u>정의</u> 주의사항

```python
def greeting(name='john doe', age):
```

SyntaxError: non-default argument follows default argument

* 기본 argument값을 가지는 argument 값 다음에 기본 값이 없는 argument로 정의할 수 없음



##### 함수 <u>호출</u> 주의사항

```python
add(x=3, 5)
```

SyntaxError: positional argument follows keyword argument

* keyword arguemtn다음에 positional argument를 활용할 수는 없음



##### 실습 문제

* *args와 **kwargs를 각각 활용
* python 표준 라이브러리, 외부 라이브러리 소스코드나 문서 등을 살펴보기!





## 함수의 범위(Scope)

* 함수는 코드 내부에 local scope을 생성, 그 외의 공간인 global scope으로 구분
  * scope
    * global: 코드 어디에서든 참조할 수 있는 공간
    * local: 함수가 만든 scope, 함수 내부에서만 참조 가능
  * variable
    * global: global scope에 정의된 변수
    * local: local scope에 정의된 변수



* 변수 수명주기(알고만 있기)
  * built-in scope
    * 파이썬 실행된 이후부터 영원히 유지
  * gloabl scope
    * 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날때까지 유지
      * 모듈: 파이썬 파일 자체(.py파일)
  * local scope
    * 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지

* 예시

  ```python
  def func():
  	a = 20
  	print('local', a)
  	
  func()
  print('global', a)
  --------------------------------------------------------------------
  NameError: name 'a' is not defined
      
  # 함수는 가장 기본: local scope!
  # 블랙박스의 결과를 받아보고 싶으면 반환 값을 변수에 저장해서 사용
  # 블랙박스 밖으로 결과를 주고 싶을 수 있음 => return 해야함
  ```



#### 이름 검색 규칙(Name Resolution)

* 파이썬에서 사용되는 이름(식별자)들은 이름공간(namespace)에 저장되어 있음

* 아래와 같은 순서로 이름을 찾으며, **LEGB Rule**이라고 부른다

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220119134322445.png" alt="image-20220119134322445" style="zoom:50%;" />

  1. Local scope
  2. Enclosed scope
  3. Global scope
  4. Built-in scope

  

### global 문

* 예시

  ```python
  # 함수 내부에서 글로벌 변수 변경하기
  a = 10
  def func1():
  	global a 		#이 부분이 없으면 바깥에 있는 a = 10이랑은 상관없음
  	a = 3
  print(a)
  func1()
  print(a)
  ```

  10

  3

  * local scope에서 global 변수 값의 변경. global 키워드를 사용하지 않으면, local scope에 a 변수가 생성됨.

* global 관련 에러

  ```python
  # global 주의 사항
  a = 10
  def func1():
  	print a
  	global a 
  	a = 3
  	
  print(a)
  func1()
  print(a)
  ------------------------
  SyntaxError: name 'a' is used prior to global declaration
  ```

  ```python
  # global 주의 사항
  a = 10
  def func1():
  	print a
  	global a 
  	a = 3
  	
  print(a)
  func1()
  print(a)
  ------------------
  StyntaxError: name 'a' is parameter and global
  ```

  



### Decomposition



### Abstraction function







## 함수의 문서화(Doc-string)

### Docstring(Document String)

* 함수나 클래스의 설명
* Jupyter notebook: 함수에 커서를 놓고 shift + tab

### Naming Convention

* 상수 이름은 영문 전체를 대문자

  * 상수: 변하지 않을 값
  * student_num(x) => STUDENT_NUM(o)

* 클래스 및 예외의이름은 각 단어의 첫 글자만 영문 대문자(파스칼케이스)

  * ex - ClassStudent

* 이외 나머지는 소문자 또는 밑줄로 구분한 소문자 사용 -> 함수+변수 모두

  * student_number

* 표기법

  * pascal case: PascalCase

  * camel case: camelCase (낙타는 머리가 작다)
  * snake case: snake_case

* 스스로를 설명
  * 함수의 이름만으로 어떤 역할을 하는지 파악 가능해야 한다
  * 이름이 길어도 괜찮다!
  * 어떤 기능을 수행하는지, 결과 값으로 무엇을 반환하는지
  * 보편적 사용 약어 외의 약어 사용 지양





## 함수 응용

### 내장 함수(Built-in Functions)

#### 1. :star: map

* **map(function, iterable)**

  * function: 각 요소에 적용하고 싶은 함수 이름
  * iterable: 

* 순회 가능한 데이터구조(iterable)의 모든 요소에 함수(function)를 적용하고, 그 결과를 map object로 반환

* 알고리즘 문제 풀이시 input 값들을 숫자로 바로 활용하고 싶을 때

  ```python
  numbers = [1, 2, 3]
  result = map(str, numbers)	#str 기능을 numbers 각각에 할당해줘
  print(result, type(result)) #그 결과를 map object로 반환(그래서 <map object at.. 어쩌구저쩌구로 반환)
  ```

  \<map object at 0x10e2ca100><class 'map'>

  ```python
  list(result)	#list 형변환을 통해 결과를 직접 확인
  ```

  (1, 2, 3)

  

* 예제 :star:  **n, m = map(int, input().split())**

```python
n, m = input().split()	
#split(): '2 3'에 split 적용하면 스페이스바 기준으로 하나씩 하나씩 떼준다
# n = '2', m = '3'
n = int(n)
m = int(m)	# 이렇게 다 적용을 일일히 시켜야 됨 

n, m = map(int, input().split())	# 이럴 때 map 사용하면 일일히 안시켜도 됨
```



```python
input_value = input()
```

20 20

```python
input_value
```

'20 20'

```python
#20 20 으로 들어온 것을 n, m으로 나눠서 저장
input_value.split()
print(numbers)
```

['20', '20']

```python
# 숫자로 바꾸어주고 싶을 때
# int(input_value.split()) ====> 안됩니다. 왜냐면 split된 결과는 list라서 각각 해야된다. 따라서 for 문 돌립시다

result = []
for number in numbers:
    result.append(int(number))
print(result)
```

[20, 20]

```python
n, m = result
print(n,m)
```

20, 20

* **map을 적용시**

  ```python
  a = input(), split()
  ```

  10 10

  ```python
  map(int, a)
  ```

  map at 0x1973694c310

  ```python
  list(map(int, a))
  ```

  [10, 10]

  ```python
  # 최종 코드
  n, m = map(int, input().split())
  print(n, m, type(n), type(m))
  ```

  20 20 

  20 20 <class 'int'> <class 'int'>

  

#### 2. filter

* **filter(function, iterable)**

* 순회 가능한 데이터구조(iterable)의 모든 요소에 함수를 적용하고(여기까진 map이랑 똑같음), 그 결과가 True인 것들을 filter object로 반환

  ```python
  def odd(n):
  	return n % 2
  numbers = [1, 2, 3]
  result = filter(odd, numbers) 
  #numbers를 모두 odd에 한번씩 넣어주고, True 나온 애들만 다 result에 넣어줌
  print(result, type(result))
  ```

  \<filter object at 0x10e4dfc10><class 'filter'>

  ```python
  list(result)	#리스트 형변환을 통해 결과 직접 확인
  ```

  [1, 3]

  

#### 3. zip

* **zip(*iterables)**

* 복수의 iterable을 모아 튜플을 원소로 하는 zip object를 반환

  ```python
  girls = ['jane', 'ashley']
  boys = ['justin', 'eric']
  pair = zip(girls, boys)
  print(pair, type(pair))
  ```

  \<zip object at 0x10e500c80><class 'zip'>

  ```python
  list(pair)
  ```

  [('jane', 'justin'), ('ashley, eric')]

* 예시

  ```python
  numbers = [1, 2, 3, 4]		#짝이 지어지는 애들만 pair 맺어줌
  letters = ['a', 'b', 'c']	# 따라서 4는 사라짐. 솔로지옥.
  students = ['aiden', 'haley', 'jun'] # pairing할 항목이 많아질수록 진가
  
  for pair in zip(numbers, letters):
  	print(pair)
  ```

  (1, 'a', 'aiden')

  (2, 'b', 'haley')

  (3, 'c', 'jun')

* 응용

  ```python
  #1
  lst = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
  for i in lst:
  	print(i)	# 여기서 list[0][2]는? ===> 3
  -----------------------------------------------------
  [1, 2, 3]
  [4, 5, 6]
  [7, 8, 9]
  
  #2
  lst2 = zip(*lst) # transpose / 전치
  for i in lst2:
      print(i)
  -------------------------------------------------------
  (1, 4, 7)
  (2, 5, 8)
  (3, 6, 9)
  
  #3
  lst3 = list(zip(*lst))[::-1] # 90도 회전 시계 반대 방향
  for i in lst3:
      print(i)
  ------------------------------------------------------
  (3, 6, 9)
  (2, 5, 8)
  (1, 4, 7)
  
  #4
  lst4 = zip(*lst[::-1]) # 90도 회전 시계 방향
  for i in lst4
  	print(i)
  ----------------------------------------------------------
  (7, 4, 1)
  (8, 5, 2)
  (9, 6, 3)
      
  ```

  



#### 4. lambda

* **lambda [parameter] : 표현식**

* 표현식을 계산한 결과값을 반환하는 함수, 이름이 없는 함수라 익명함수라고도 불림

* 어떤 함수를 잠시만 쓰고 싶을 때 쓰인다

* return문을 가질 수 없음

* 간편 조건문 외 조건문이나 반복문을 가질 수 없음

* 함수를 정의해서 사용하는 것보다 간결하고 저장용량이 작음

  ```python
  #def로 정의시
  def 함수이름(매개변수):
  	return 결과
  
  #lambda로 정의시
  lambda 매개변수 : 결과	# 함수이름이 없다
  ```

* 예시:question: 람다 왜 써야됨? 어떤 방식으로 많이 쓰임? :question:

  ```python
  lambda x : x + 1	# x를 받아서 x+1을 리턴하는 함수
  print((lambda x : x + 1)(10))	#10을 받아서 11을 리턴함
  
  func = lambda x : x + 1		#
  func(1)
  
  #def 함수 사용
  
  def sum(x)
  	return x + 1
  
  ```

  

* def를 사용할 수 없는 곳에서도 사용가능

  * def를 사용할 수 없는 곳

  ```python
  #삼각형의 넓이를 구하는 공식 = def
  def traingle_area(b, h):
  	return 0.5 * b * h
  triange_area(5, 6)
  ```

  ```python
  # 삼각형의 넓이를 구하는 공식 - 람다
  triangle_area = lambda b, h : 0.5 * b * h
  triangle_area(5, 6)
  ```

* filter과 함께 응용 가능

  ```python
  # def 사용시
  def odd(n):
  	return n % 2
  
  print(list(filter(odd, range(5))))     
  ```

  [1, 3]

  ```python
  # 람다 사용
  print(list(filter(lambda n: n % 2, range(5))))
  
  # filter: range 통에 함수를 하나하나 적용 - 홀수 인지 아닌지 판별. 그 중에서 Ture인 것, 즉 홀수인 결과들을 묶어주는 것
  
  #list: filter가 묶어 준 걸 조금 더 편하게 볼 수 있도록 도와줌
  ```

  ```python
  lst = [1, 2, 3, 4, 5]
  filter(lambda n : n % 2, lst)
  ```

  

#### 5. 재귀 함수(recursive function)

* 자기 자신을 호출하는 함수

* 따라서 언젠가 리턴을 하는 종료조건이 꼭 필요하다

* 1개 이상의 base case(종료되는 상황)가 존재하고, 수렴하도록 작성

* 예시

  ```python
  def foo():
  	foo()
  ```

  ```python
  # factorial n! = n*(n-1)!
  
  
  ```

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220119144223704.png" alt="image-20220119144223704" style="zoom:50%;" />

  ```python
  def factorial(n):
  	if n == 0 or n == 1:
          return 1
      else:
          return n * factorial(n-1)
  factorial(4)
  ```

  24

  ```python
  return 4 * f(3)
  	return 3 * f(2)
  		return 2 * f(1)
  			return 1
  
  # return 1에서 return 4* f(3) 까지 역방향으로 돌아감
  ```

* 재귀 함수 주의 사항

  * 재귀 함수는 base case에 도달할 때까지 함수를 호출함
  * 메모리 스택이 넘치게 되면(stack overflow) 프로그램이 멈춤
  * 파이썬에서는 최대 재귀 깊이(maximum recursion depth)가 1,000번으로, 호출 횟수가 이를 넘어가게 되면 Recursion Error 발생

* 반복문으로 표현

  ```python
  def factorial(n):
  	result = 1
  	while n > 1:
  		result *= n
  		n -= 1
  	return result
  ```

* 반복문 vs 재귀함수

  * 알고리즘 자체가 재귀적인 표현이 자연스러운 경우 재귀함수를 사용함
    * :question: 재귀적인 표현이 자연스러운 경우
  * 재귀 호출은 변수 사용을 줄여줄 수 있음
  * nㅁ재귀 호출은 입력값이 커질수록 연산 속도가 오래 걸림

