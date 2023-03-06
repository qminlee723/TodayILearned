# Python OOP

## :ballot_box_with_check: Table of Contents

**객체지향프로그래밍**

- Overview

  1. 객체
  2. 객체지향프로그래밍 
  3. 절차지향 프로그래밍
  4. 객체지향 프로그래밍이 필요한 이유
  5. 예시

- oop기초

  1. 기본문법

  2. 클래스
  3. 인스턴스
  4. 속성
  5. 메소드
  6. 객체 비교하기

- 인스턴스

  1. 인스턴스 변수
  2. 인스턴스 메소드
  3. self
  4. 생성자 메소드
  5. 소멸자 메소드
  6. 매직 메소드

- 클래스

  1. 클래스 변수
  2. 클래스 메소드
  3. 스태틱 메소드
  4. 인스턴스와 클래스 간의 이름공간(namespace)
  5. 정리

- 메소드정리

  1. 인스턴스 
  2. 클래스
  3. 스태틱
  4. 예시

**객체지향의 핵심개념**

- 추상화
  1. 개념
  2. 예시
- 상속
  1. 개념
  2. 상속 관련 함수와 메소드
  3. 다중 상속
- 다형성
  1. 개념
  2. 메소드 오버라이딩
- 캡슐화
  1. 개념
  2. 접근제어자 종류
  3. getter
  4. setter

---

---



## :ballot_box_with_check: 객체 지향 프로그래밍(OOP)

### :one: OVERVIEW

#### 1. 개념

* **객체(object)란?**

  * 객체: thing, concept

  * 특정 타입의 인스턴스

  * 속성(Attribute) + 기능(Method)

    

- **인스턴스(instance)란? **

  - 객체: 만들어진 객체

  - 클래스로 객체가 만들어지면(==메모리에 추가되면) 인스턴스라고 함

  - 클래스는 붕어빵 틀이고, 인스턴스는 붕어빵

    * 123, 900, 5는 모두 int의 인스턴스
    * 'hello', 'bye'는 모두 string의 인스턴스
    * [232, 89, 1], []은 모두 list의 인스턴스

    

#### 2. 객체의 특징

- 객체(object) = 속성(attribute) + 기능(Method)

- **타입(type)** 

  - 어떤 연산자(operator)와 조작(method)이 가능한가?
  - 데이터의 타입이 **클래스**!
  - 즉 클래스를 만든다는 것은, 새로운 데이터 타입을 만드는 것과 같다 . 

  ```python
  a = 123
  b = 'hello world'
  
  print(type(a))
  print(type(b))
  -------------------------------------
  <class 'int'>	#123은 int라는 "class" 이다! 결국 다 객체임
  <class 'str'>
  ```

  ```python
  dir(a)	# 해당 클래스에서 사용할 수 있는 method를 다 보여주는 명령어
  dir(b)
  ```

  ```python
  123.__class__
  ```

  

- **속성(attribute)** 

  - 어떤 상태(데이터)를 가지는가?

  

- **조작법(method)** 

  - 어떤 행위(함수)를 할 수 있는가?
  - .method() 에서 '.'도 dot 연산자
  
  - len()같은 경우, 파이썬 안에서 정의가 되어 있음



#### 3. **객체지향프로그래밍**

- 프로그램을 여러 개의 독립된 객체들과 그 객체들 간의 상호작용으로 파악하는 프로그래밍 방법

  * 예시: 콘서트 안에 가수, 감독, 관객 등 각각의 객체 존재

- 절차지향프로그래밍과의 비교

  - 하나하나 변수에 담아서 처리해야 하는 절차지향프로그래밍과 다름

  ```python
  # 절차지향프로그래밍
  # 데이터와 함수로 인한 변화
  
  a = [1, 2, 3]
  
  a = sorted(a)
  
  a = reversed(a)
  
  def append(list, value):
      return 1 + [value]
  
  a = append(a, 4)
  ```

  ```python
  # 객체지향프로그래밍
  # 데이터와 기능(method)분리, 추상화된 구조(interface)
  
  a = [1 ,2, 3]
  
  a.sort()
  
  a.reverse()
  
  a.append(4)	# 얘는 스스로 a를 호출해서 사용가능
  
  ```

- 객체지향 프로그래밍이 필요한 이유

  - 현실 세계를 프로그램 설계에 반영(추상화)

    ```python
    # 절차지향프로그래밍
    
    name = '아이유'
    age = 20
    
    person01 = {
        'name': '아이유'
        'age' : 20
    }
    
    person02 = {
        'name': '홍길동'
        'age' : 999
    }
    
    def greeting(person):
        #person : dictionary
        print('안녕하세요' + person["name"])
        
    greeting(person_01)
    ```

    ```python
    # 객체지향프로그래밍
    
    class Person:	#class 이름은 Pascal 케이스로!!
        
        def __init__(self, name, gender):
            self.name = name
            self.gender = gender
            
        def greeting(self):
            print(f'안녕하세요, {self.name}입니다.')
    
    jimin = Person('지민', '남')
    jimin.greeting()
    #출력: 안녕하세요, 지민입니다.
    
    jieun = Person('아이유', '여')
    jieun.greeting()       
    # 출력: 안녕하세요, 아이유입니다.
    ```

    ```python
    class Person
    	def greeting(self):
            print('안녕하세요' + self.name + '입니다.')
            
    jimin = Person()
    jimin.name = '지민'
    jimin.phone = '01012341234'
    jimin.greeting()
    ```

    * jimin, jieun 등은 Person(클래스)의 인스턴스

    

- **예시**: 사각형 넓이 구하기

  - 절차지향

    ```python
    # 단순 변수
    x_01 = 100 # 너비
    y_01 = 200 # 높이
    
    area_01 = x_01 * y_01
    area_01
    
    x_02 = 10 # 너비
    y_02 = 10 # 높이
    
    area_02 = x_02 * y_02
    print(area_02)
    ```

    ```python
    # 함수
    def area(x, y):
        return x * y
    
    print(area(x_01, y_01))
    print(area(x_02, y_02))
    ```
    
    
    
  - 객체지향프로그래밍
  
    ```python
    # 객체
    class Rectangle:		# 클래스(class)
            
        def area(self):		# 메소드(method)
            return self.x * self.y
        
    r1 = Rectangle()	# 인스턴스(instance): 객체를 저장해놓는 변수
    					# rectangle이라는 class를 불러오기 위한 instance
    r1.x = 100
    r1.y = 200
    r1.area()
    
    r2 = Rectangle()		# 인스턴스(instance)
    r2.x = 10
    r2.y = 10
    r2.area()
    ```
    
    ```python
    class Rectangle:
        
        def __init__(self, x, y):
            self.x = x			# self란 class에 귀속된 변수
            self.y = y			# 클래스를 호출하지 않으면 사용불가능
            
        def area(self):
            return self.x * self.y
        
    r1 = Rectangle(100, 200)
    print(r1.x)
    r1.area()
    
    r2 = Rectangle(300, 500)
    r2.area()
    
    # 같은 Rectangle이라는 클래스를 다른 인스턴스(r1, r2)안에 넣어서 재사용
    # Rectangle이라는 분류 아래에 r1, r2와 같은 분류 내의 다른 존재
    # Class는 인간이고, r1, r2는 나랑 창환이... 그런 느낌..
    ```
    
    
  

* 객체지향의 장점
  * 프로그램을 **유연하고 변경이 용이**하게 만들기 때문에 **대규모 소프트웨어개발**에 사용
  * 소프트웨어 **개발과 보수**를 간편하게 하며, 보다 **직관적**인 코드 분석을 가능하게 함
  
  

### :two: OOP 기초

#### 1. 기본 문법

<img src="images\image-20220127133635816.png" alt="image-20220127133635816" style="zoom: 67%;" />

```python
class MyClass:				# 클래스 정의(파스칼)

my_instance = MyClass		# 인스턴스 생성
my_instance.my_method()		# 메소드 호출
my_instance.my_attribute	# 속성
```



#### 2. 클래스(class)

* 객체들의 분류(class)
* 파스칼형태로 쓴다 

```python
class Person:
    name = 'aiden'		# attribute
    
    def run():			# class안쪽에 정의된 함수, 즉 run은 메소드
        print('헥헥')
    
person_1 = Person()

print(type(person_1))
print( isinstance(person_1, Person) )
# person_1 이라는 instance가 Person이라는 클래스니?
```

```python
class Person:
    cnt = 0						#클래스 변수
    
    def __int__(self):
        self.name = 'aiden'		# 인스턴스 변수

# 클래스 변수와 인스턴스 변수의 가장 큰 차이점은, 이 클래스 내의 인스턴스 변수가 이 클래스 변수를 가지고 있다. 

person_1 = Person()
person_2 = Person()

# self.name은 저 person_1이 각각 가지고 있고,
# cnt는 person_1, person_2 둘 다 가지고 있다. 
```



#### 3. 인스턴스(instance)

* 하나하나의 실체(예)



#### 4. 속성(attribute)

* 특정 데이터 타입/클래스의 객체들이 가지게 될 상태/데이터를 의미



#### 5. 메소드(method)

* 특정 데이터 타입/클래스의 객체에 공통적으로 적용 가능한 행위(함수)

  ```python
       
  class Person:
  
      def talk(self):					# 메소드 = 클래스 내부에 정의된 함수
          print('안녕')
          
      def eat(self, food):			# def eat(self, *args):
          print(f'{food}를 냠냠')	# self = Person이라는 class에 귀속되는 애들
          
  
  hello = Person()
  hello.talk()
  hello.eat('hamburger')
  
  saram = Person()
  saram.talk()
  saram.eat('pizza')
  
  # 같은 Person이라는 클래스를 다른 인스턴스안에 넣어서 재사용이 가능!
  # hello 와 saram이 인스턴스
      
  ```

  * method에 필요한 것들을 받아오는 애들 = arguments '=. parameter

  

  #### 6. 객체 비교하기

  * ==
    
    * 동등한(equal)
    * 변수가 참조하는 객체가 동등한 경우 True
    * 두 객체가 같아 보이지만, 실제로 동일한 대상을 가리키고 있다고 확인해 준 것은 아님
    
  * is
    * 동일한(identical)
    * 두 변수가 동일한 객체를 가리키는 경우 True
    
    

### :three: 인스턴스(instance)

#### 1. 인스턴스 변수

* 인스턴스 변수란?

  * 인스턴스가 개인적으로 가지고 있는 속성(attribute)
  * 각 인스턴스들의 고유한 변수

* 생성자 메소드에서 self.<name>으로 정의

* 인스턴스가 생성된 이후 <instance>.<name>으로 접근 및 할당

* 리터럴(literal) : 인스턴스를 만드는 방식

  ```python
  # 리터럴로 인스턴스를 만들어 보자
  a = 123		#int라는 클래스로 인스턴스가 만들어진 것
  b = True	#bool이라는 클래스로 인스턴스가 만들어진 것
  ```



#### 2. 인스턴스 메소드

* 인스턴스 변수를 사용하거나, 인스턴스 변수에 값을 설정하는 메소드
* 클래스 내부에 정의되는 메소드의 기본
* 호출 시, 첫번째 인자로 **인스턴스 자기자신(self)**이 전달됨



#### 3. self

* 인스턴스 자기자신

  *  인스턴스 각각을 조작하고 싶을 때 class에서 인스턴스를 정의 
  * 따라서 method를 정의할 때 self를 쓰지 않으면, argument가 없다고 에러남
  * 모든 메서드는 self를 첫번째 파라미터로 가져야 한다. 

* 파이썬에서 인스턴스 메소드는 호출 시 첫번째 인자로 인스턴스 자신이 전달되게 설계

  * 매개변수 이름으로 self가 첫번째로 호출된다
  * 다른 단어로 써도 작동하기는 하지만, 안 쓰는게 파이썬의 암묵적인 규칙

  ```python
  Class Person:
      # 인스턴스 메서드 : 인스턴스를 조작하고 싶어
      # 함수 내부에 인스턴스를 던져주도록 설계
      # 메서드를 정의할 때 self로 받도록
      # Python 내부적으로 Person.test(p1)
      def test():
          return 'test'
  # 인스턴스 생성(p1)
  p1 = Person()
  
  # <__main__.Person object at 0x00000228B53D4F70>
  s = p1.test()
  print(s, p1)
  ```
  
  

#### 4. 생성자(constructor) 메소드

* 인스턴스 객체가 생성될 때 자동으로 호출되는 메소드

* 인스턴스 변수들의 초기값을 설정

  * 인스턴스 생성

  * **\__init__(self)**메소드 자동호출

    * 클래스가 생성될 때 자동적으로 불러와지는 함수.

      ```python
      class Person:
          cnt = 0	# 클래스 변수
          # 클래스가 인스턴스를 만들어줄때 자동으로 __init__이 호출됨
          
          def __init__(self):
              Person.cnt +=1
              # 같은 이름으로 함수를 정의하면. 
              # 마지막에 함수를 정의한 것들만 출력/반환된다. 
          
          def __init__(self, name):	
              # instance를 생성하는 녀석
              # instance 변수는 각각의 class에서 독립적이니까 각각 나옴
              
              self.name = name # 인스턴스변수
              
              # class cnt가 아니라, instance의 독립적인 cnt 만드는 것
              # class와는 상관없게 된다. (Python은 작은 것 부터 찾음)
              Person.cnt += 1 	# 인스턴스변수
              
              # 클래스 변수는 모든 인스턴스 변수에 공통적으로 적용되지만,
              # 인스턴스 변수는 개별적
              
      person_1 = Person('aiden')
      print(person_1.cnt)
      
      person_2 = Person('haley')
      print(person_2.cnt)
      ```

      aiden 
      
      haley
      
      ```python
      aiden.cnt = 3
      
      print(aiden.cnt)
      print(haley.cnt)	
      
      # 파이썬은 인스턴스로부터 새로운 인스턴스 변수를 생성할 수 있다.
      # self.name = name
      ```
      
      3
      
      2
      
      ```python
      class Person:
          def __init__(self, name):
              self.name = name 
              
      aiden_1 = Person('aiden')
      aiden_2 = Person('aiden')
      
      print(aiden_1 == aiden2)	# 주소값이 다르다
      #클래스값 비교는 우리가 직접 구현해 주어야 한다. by ".__eq__"
      # 설사 한개라고 하더라도, 비교할 때는 
      print(aiden_1 is aiden2)	# 주소값이 같다
      ```
      
      False
      
      False
      
      

    ```python
    hyoeun = Person('효은', 999)
    print(hyoeun.name, hyoeun.age)
    ```
    
    효은 999
    
    

#### 5. 소멸자(destructor) 메소드

* 인스턴스 객체가 소멸(파괴)되기 직전에 호출되는 메소드

  ```python
  class Person:
      def __init__(self):
          print('응애')
          
      def __del__(self):
          print('으억...')
  ```

  ```python
  p1 = Person()
  ```

  응애

  ```python
  del p1
  ```

  으억...

  

#### 6. 매직 메소드

* Double underscore(__)가 있는 메소드는 특수한 동작을 위해 만들어진 메소드로, 스페셜 메소드 또는 매직 메소드라고 불린다.

* 특정 상황에 자동으로 불리는 메소드

* 매직 메소드 종류

  <img src="images\image-20220126103640656.png" alt="image-20220126103640656" style="zoom:67%;" />

  1. **\__str__** : 해당 객체의 출력 형태를 지정

     - 프린트 함수를 호출할 때, 자동으로 호출
     - 어떤 인스턴스를 출력하면 \__str__의 return값이 출력**\__gt__**: 부등호 연산자(>, greater than)

  3. **\__eq__**: 등호 연산자(=, equal)
  
  4. **\__doc__**: docstring
  
     ```python
     'abc'.__doc__
     ```
  
* 매직 메소드 예시

  * 예시 1(from professor)

    ```python
    class Person:
        
        def __init__(self, name, age, height):
            self.name = name
            self.age = age
            self.height = height
        
        def __lt__(self):				#less than
            return self.age > other.age
        
        def __gt__(self, other):		#greater than
            print(f'{self.name}: {self.age} / {other.name}: {other.age}살')
            return self.age > other.age
        
        def __len__(self):
        	return f'{self.height}cm'
    ```

    ```python
    p1 = Person('재영', 100, 190)
    p2 = Person('지선', 10, 185)
    
    p1 > p2
    
    len(p1)
    
    len(p2)
    ```

    ```python
    a = map(int, '1, 2, 3'.split())
    ```

  * 예시 2 (from powerpoint)

    ```python
    class Circle:
        
        def __init__(self, r):
            self.r = r
        
        def area(self):
            return 3.14 * self.r * self.r
        
        def __str__(self):
            return f'{원} radius: {self.r}'
        
        def __gt__(self, other):
            return self.r > other.r
    ```

    ```python
    c1 = Circle(10)
    c2 = Circle(1)
    ```

    ```python
    print(c1)
    print(c2)
    ```

    [원] radius: 10

    [원] radius: 1

    ```python
    c1 > c2
    c1 < c2
    ```

    True

    False



### :four: 클래스

#### 1. 클래스 변수

* 한 클래스의 모든 인스턴스가 가지고 있는, 똑같은 값을 가지고 있는 속성

* 클래스 속성(attribute)

  * 한 클래스의 모든 인스턴스라도 똑같은 값을 가지고 있는 속성

* 클래스 선언 내부에서의 정의

  ```python
  <classname>.<name>으로 접근 및 할당
  
  class Circle:
      pi = 3.14		# 클래스 변수 정의
      
      def __init__(self, r):
          self.r = r
      
      def area(self):
          return Circle.pi *
  ```

  ```python
  Circle.pi
  ```

  3.14

  ```python
  c1 = Circle(2)
  c1.area()		
  ```

  12.56



#### **2. 클래스 메소드**

* 클래스가 사용할 메소드

  * 클래스 변수를 조작하기 위한 것 

* @classmethod 데코레이터를 사용하여 정의

  * 데코레이터: 함수를 어떤 함수로 꾸며서 새로운 기능을 부여

* 호출 시, 첫번째 인자로 클래스(**cls**)가 전달됨

  ```python
  # 임우재 교수님 예시
  
  class Person:
      cnt = 0
      
      def __init__(self, name):
          self.name = name
          self.run = False
          Person.cnt += 1
      
      def run(self):
          print('뛰어!')
          self.run = True
      
      
      @classmethod 		# instance를 생성하지 않아도 호출이 가능
      def plus(cls): 		#
          cls.cnt += 1
          
  print(Person.cnt)		# 0
  Person.plus()			# class
  print(Person.cnt)		# 1
  ```

  

  ```python
  class MyClass:				#class 이름은 Pascal Case
      var = 'Class 변수'
      
      #클래스 메서드: 클래스를 조작하고 싶어
      # 함수 내부에 클래스를 던져주도록 설계
      # 메서드를 정의할 때 cls로 받도록
      
      @classmethod
      def class_method(cls):	#함수, 변수 이름은 Snake Case
          print(cls.var)
          return cls
  ```

  ```python
  MyClass.class_method()
  ```

  Class 변수

  \__main__.MyClass

  ```python
  MyClass
  ```

  \__main__.MyClass

  

* 데코레이터 

  * 함수

  * 여러번 중복되는 함수에 같은 걸 씌우고 싶을 때 사용

    ```python
    def time_dsplay_decorater(origin_func):
        #매개변수로 함수를 받는다(origin_func)(함수를 꾸며주는 함수)
       
    	#하나의 함수를 만들고
    	def decorated():
            # 내가 사용할 로직을 쓰고
            print(dt.now())
            origin_func()
            print('---')
            
        # 만든 함수를 리턴해준다
        return decorated
    
    
    @time_display_decorator
    def test_a():
        print('test_a')
    
    @time_display_decorator
    def test_b():
        print('test_b')
        
        
    test_a() # time_display_decorator(test_a)()
    
    		# time_display_decorator() => 내부적인 함수콜
        	# original_func를 매개변수로 갖음
            # 그래서 test_a를 매개변수로 넣어주는
            # 마지막 () 이 실행해라 라는 거.... 임...(???)
    test_b()
    
    
    # 이렇게 정의를 하면 얘가 이제 데코레이터가 됩니다.(????)
    
    ```
    

* 예시

  ```python
  #데코레이터 안쓰면 
  
  from datetime import datetime as dt 
  #datetime이라는 모듈에서 datemtime을 가져와라. 이걸 dt라고 한다
  
  def test_a():
      print(dt.now())
      print('test_a')
      print('----')
   
  def test_b():
      def test_b():
      print(dt.now())
      print('test_b')
      print('----')
  
  ```

* 심화

  ```python
  def time_dsplay_decorater(origin_func):
  	def decorated():
          print(dt.now())
          origin_func()
          print('---')
      return decorated
  
  
  class TimeDisplay:
      def __init__(self, origin_func):
          self.origin_func = origin_func
          
      def __call__(self):
          print(dt.now())
          self.origin_func()
          print('----')
  
  @time_display_decorator # 함수로 정의되어있는 데코레이터(snake)
  def test_a():
      print('test_a')
  
  @TimeDisplay # 클래스 형태로 정의되어있는 데코레이터(Paskal)
  def test_b():
      print('test_b')
  
  #### @time_display_decorator나 @TimeDisplay 둘 다 같은 결과를 반환
  #### decorated 대신 wrapper 등으로도 쓰인다. 
      
  test_a() 
  test_b()
  ```




#### 3. 스태틱 메소드(Static Method)

* 인스턴스 변수, 클래스 변수를 전혀 다루지 않는 메소드

* 속성을 다루지 않고, 단지 기능(행동)만을 하는 메소드를 정의할 때 사용한다

* @staticmethod 데코레이터를 사용하여 정의

* 호출 시, 어떠한 인자도 전달되지 않음(클래스 정보에 접근/수정 불가)

  * 

  ```python
  class MyClass:
      
      # 스태틱 메서드: 클래스나 인스턴스를 조작할 생각은 없는데, 함수를 쓸거
      @staticmethod
      def static_method(static):
          return static
  -------------------------------------------
  TypeError: static_method() missing 1 required positional argument: 'static'
  ```

  ```python
  class MyClass:
      
      @staticmethod
      def static_method():
          return 'static'
  ```

  ```python
  class Person():
      population = 0
      
      @classmethod
      
      @staticmethod
      def static_method():
          return '사람들임'
  ```

  

#### 4. 인스턴스와 클래스간의 이름공간(namespace)

* 클래스 정의시, 클래스와 해당하는 이름공간 생성

* 인스턴스 만들면, 인스턴스 객체가 생성되고 이름 공간 생성

* 인스턴스에서 특정 '속성'에 접근하면, 인스턴스 -> 클래스 순서로 탐색

  ![image-20220202130312602](images\image-20220202130312602.png)

  ```python
  class Person:
      name = 'unknown'
      
      def talk(self):
          print(self.name)
  ```

  ```python
  #p1: 인스턴스 변수 정의되지 않음 => 클래스 변수가 출력
  p1 = Person()
  p1.talk()
  ```

  ```python
  #p2: 인스턴스 변수 정의됨 ('Kim') => 인스턴스 변수가 출력
  p2 = Person()
  p2.talk()
  p2.name = 'Kim'
  p2.talk()
  ```

  ```python
  print(Person.name)
  print(p1.name)
  print(p2.name)
  # Person 클래스의 값이 Kim으로 변경된 것이 아님
  # p2인스턴스의 이름 공간에 name이 Kim으로 저장된다
  ```



#### 5. 정리

* 클래스 구현
  * 클래스 정의
  * 데이터 속성 정의(객체의 정보는 무엇인지)
  * 메소드 정의(객체를 어떻게 사용할 것인지)
* 클래스 활용
  * 해당 객체 타입의 인스턴스 생성 및 조작







### :five: 메소드

<img src="images\image-20220126094750348.png" alt="image-20220126094750348" style="zoom: 67%;" />

![image-20220202131133134](images\image-20220202131133134.png)



#### 1. 인스턴스 메소드(Instance Method)

* self 매개변수를 통해 동일한 객체에 정의된 속성 및 다른 메소드에 자유롭게 접근이 가능

* 클래스 자체에도 접근 가능 => 인스턴스 메소드가 클래스 상태를 수정할 수도 있음

  ![image-20220202131224352](images\image-20220202131224352.png)

  

#### 2. 클래스 메소드(Class Method)

* 클래스를 가리키는 cls 매개 변수를 받는다

* cls 인자에만 접근할 수 있기 때문에 객체 인스턴스 상태를 수정할 수 없음

* 클래스 자체에서 각 메소드를 호출하는 경우, 인스턴스 메소드는 호출이 불가능하다

  ![image-20220202131314127](images\image-20220202131314127.png)

  

#### 3. 스태틱 메소드

* 임의 개수의 매개변수를 받을 수 있지만, self나 매개변수는 사용하지 않음

* 객체 상태나 클래스 상태를 수정할 수 없음

* 일반 함수처럼 동작하지만, 클래스의 이름공간에 귀속된다.

  * 주로 해당 클래스로 한정하는 용도로 사용

  ![image-20220202131503640](images\image-20220202131503640.png)







## :ballot_box_with_check: 객체지향의 핵심개념 :star::star::star::star::star:

* 추상화, 상속, 다형성, 캡슐화

### :one: 추상화

* 현실 세계를 프로그램 설계에 반영

* 고수준의 것에서 저수준의 것으로 설명하는 것

* 공통적인 속성을 뽑아내서 코드로 만드는 것

* 예시

  ![image-20220202131612816](images\image-20220202131612816.png)



### :two: :star2: 상속 (inheritance)

#### 1. 상속

* 두 클래스 사이 부모=자식 관계를 정립하는 것

  * A라는 클래스와 B라는 클래스가 있을 때, B가 A를 상속받아서 만들어진다면, A클래스에 있는 모든 것들이 B에 그대로 넘어가게된다. 
  * 하위 클래스는 상위 클래스에 정의된 속성, 행동, 관계 및 제약 조건을 모두 상속받는다.
  * 부모 클래스의 속성, 메소드가 자식 클래스에 상속되므로, **코드 재사용성**이 높아진다. 
    * :exclamation: DRY 원칙: Don't Repeat Yourself 

  * 모든 파이썬 클래스는 object를 상속받는다. (여기선 ParentClass에서 받은거)

* 코드의 재사용성이 높아진다

  ![image-20220127104235015](images\image-20220127104235015.png)

  ```python
  class A():				# 세 개 다 같은 것
  class A(object):		# 제일 구버전
  class A:				# 최신버전: (object)를 가지고는 있음.
     						# object 클래스를 상속받은 class A를 정의하겠다
  ```

* 메소드 재사용 예시

  ![image-20220202131905540](images\image-20220202131905540.png)



#### 2. 상속 관련 함수와 메소드

1. **isinstance(object, classinfo)**

   - 이 object가 classinfo로 만들어졌니?

   - classinfo의 instance거나 subclass*인 경우 True

   - object = student이라면,  classinfo = Person으로 만들어졌니?

     ![image-20220202132045570](images\image-20220202132045570.png)

     

2. **issubclass(class, classinfo)**

   * class 가 classinfo의 subclass면 True

   * classinfo는 클래스 객체의 튜플일 수 있음, classinfo의 모든 항목을 검사

     ![image-20220202132120735](images\image-20220202132120735.png)

   

3. **super()**

   * 자식클래스에서 부모클래스를 사용하고 싶은 경우

   * 상위클래스에 있는 것을 직접 접근하고 싶을 때 

     ```python
     class Person:
         def __init(self, name, age, number, email):
             self.name = name
             self.age = age
             self.number = number
             self.email = email
             
     class Student(Person):
         def __init__(self, name, age, number, email, student_id):
             super().__init__(name, age, number, email)
             self.student_id = student_id
             
     # 만약 super()를 쓰지 않으면, 메소드 오버라이딩이 된다.
     # 자식 이기는 부모 없다. 
     # 똑같은 메소드를 쓰면 자식클래스의 메소드가 부모클래스를 덮어쓰게 된다. 
     ```

     ![image-20220202132144654](images\image-20220202132144654.png)

   

#### 3. 상속 정리

* 파이썬의 모든 클래스는 ojbect로부터 상속된다.
* 래스의 모든 요소 
* 상속관계에서의 이름 공간은 인스턴스, 자식클래스, 부모클래스 순으로 탐색을 하게 된다. 



#### 4. 다중 상속

* 두개 이상의 클래스를 상속 받는 경우

* 상속 받은 모든 클래스의 요소를 활용 가능함

* 중복된 속성이나 메서드가 있는 경우 **상속 순서**에 의해 결정된다. 

  ![image-20220202132239857](images\image-20220202132239857.png)
  

![image-20220202132256524](images\image-20220202132256524.png)



#### 5. 상속 관련 함수와 메소드

* mro 메소드(Method Resolution Order)
  * 해당 인스턴스의 클래스가 어떤 부모 클래스를 가지는 확인하는 메소드
  * 기존의 인스턴스 -> 클래스 순으로 이름 공간을 탐색하는 과정
  * 상속 관계에 있으면 인스턴스 -> 자식 클래스 -> 부모 클래스로 확장

* 예시

  ![image-20220202132603756](images\image-20220202132603756.png)

  ```python
  class Person:
      
      def __init__(self, name, age):
          self.name( = name)
          self.age ( = age)
  def talk(self):
      print('반갑습니다, {ls}')
  ```

  

### :three: 다형성(Polymorphism)

#### 1. 다형성(Polymorphism)

* 여러 모양을 뜻하는 그리스어
* 동일한 메소드가 클래스에 따라 다르게 행동할 수 있음을 의미
* 즉, 서로 다른 클래스에 속해 있는객체들이 동일한 메시지에 대해 다른 방식으로 응답될 수 있음



#### 2. 메소드 오버라이딩

* 상속 받은 메소드를 재정의

  * 클래스 상속 시, 부모 클래스에서 정의한 메소드를 자식 클래스에서 변경
  * 부모 클래스의 메소드 이름과 기본 기능은 그대로 사용하지만, 특정 기능을 바꾸고 싶을 때 사용
  * 상속 받은 클래스에서 같은 이름의 메소드로 덮어씀
  * 부모 클래스의 메소드를 실행시키고 싶은 경우 :question: super를 활용

* 예시

  ![image-20220202132909392](images\image-20220202132909392.png)



### :four: 캡슐화(Encapsulation)

#### 1. 캡슐화

* 객체의 일부 구현 내용에 대해 외부로부터의 직접적인 액세스를 차단
  * 주민등록번호
* 비슷한 기능을 하는 속성과 메서드를 묶는 작업 + 은닉성(접근권한)
* 응집도(cohesion), 결합도/의존성(coupling/dependency)

  * 모듈 내 응집도가 높고, 모듈 간 결합도가 낮은것이 좋다!

#### 2. 접근제어자 종류 

* **Public Access Modifier**: 다 가능

  * 언더바 없이 시작하는 메소드나 속성

  * 어디서나 호출이 가능, 하위 클래스 override 허용

  * 일반적으로 작성되는 메소드와 속성의 대다수를 차지 

    ```python
    class Person:
        def __init__(self, name, age):
            self.name = name
            self._age = age
            
    # Person 클래스의 인스턴스인 p1은 이름(name)과 나이(age) 모두 접근이 가능
    p1 = Person('김싸피', 30)
    print(p1.name)
    print(p1.age)
    ```
    
    

* **Protected Access Modifier**: 나랑 내 자식(안에서)만 가능

  * 언더바 1개로 시작하는 메소드나 속성

  * 암묵적 규칙에 의해 부모 클래스 내부와 자식 클래스에서만 호출 가능

  * 하위 클래스 override 허용

    ```python
    class Person:
        def __init__(self, name, age):
            self.name = name
            self._age = age
            
        def get_age(self):
            return self._age
        
    # 인스턴스를 만들고, get_age 메서드를 활용하여 호출이 가능
    p1 = Person('김싸피', 30)
    p1.get_age
    
    # _age에 직접 접근해도 호출 가능
    # 파이썬에서 암묵적으로 활용됨
    
    p1._age
    ```
    
    

* **Private Access Modifier**: 나만 가능

  * 언더바 2개로 시작하는 메소드나 속성

  * 본 클래스 내부에서만 사용이 가능

  * 하위 클래스 상속 및 호출이 불가능(오류)

  * 외부 호출 불가능(오류)

  * \_\_{class_name}\_\_attribute : name mangling(파이썬이 private접근을 막는다.. 원래 \__age__를 찾고자 했던거임)

    ```python
    class Person:
        def __init__(self, age)
        	self.__age = age	# private(언더바 두 개 )
            
        def get_age(self):		# public method
            return self.__age	# private value(언더바 두 개)
        
        def set_age(self): 		# public method
            self.__age += 1
        
    tony = Person(27)
    print(tony.__age)
    
    ========================================
    AttributeError: 'Person' object has no attribute '__age'
        
    =============================================
    
    print(tony.get_age())
    
    # 직접 접근하지말고, 메서드를 이용해 접근하세요 
    
    tony.set_age()
    print(tony.get_age())
    ```




#### 3. getter메소드와 setter 메소드

* getter 메소드

  * 변수의 값을 읽는 메소드

  * @property 데코레이터 사용setter 메소드

* setter 메소드

  * 변수의 값을 설정하는 성격의 메소드
  * @변수.setter 사용

  

* 예시1

  ```python
  class Person:
      def __init__(self, age):
          self._age = age
          
      @property
      def age(self):
          return self._age - 10
      
      @age.setter
      def age(self):
          return self._age - 10
  ```

  ```python
  p1 = Person(10)
  ---------------------------
  #TypeError: 'int' obejct is not callable
  ```

  ```python
  p1.age() #  매서드를 정의헀는데, 속성처럼 쓰도록 한다.
  ```

  ```python
  p1 = Person(40)
  ```

  ```
  p1.age()
  ```

* 예시2

  ```python
  class Person:
      def __init__(self, age):
          self._age = age
          
      def get_age(self):			 #getter method
          return self.__age 		#private value
      
      def set_age(self, new_age): # setter method
          self.__age = new_age # private method
  
      def get_age(self):			 #getter method
          return self.__age		 #private value
      
      def set_age(self, new_name): # setter method
          self.__age = new_name # private method
      
      
  aiden = Person()
  aiden.set_age(24)
  ```

  * 가져와야 할 메소드가 많아진다면, 데코레이터를 이용해서 반복을 줄인다. 

    ```python
    class Person:
        def __init__(self, age):
            self._age = age
            
        def get_age(self):				#getter method
            return self.__age 			#private value
        
        def set_age(self, new_age): 	# setter method
            self.__age = new_age 		# private method
    
        @property # 게터
        def name(self):			 		# getter method
            return self.__age		 	#private value
        
        @name.setter # 세터
        def name(self, new_name):		# setter 
            self.__name = new name 		# private method
        
        @name.getter 
        #상속 받아서 name의 getter를 오버라이딩 해야 할 때만 쓰임. 
        
    aiden = Person()
    aiden.set_age(24)
    
    aiden.set_name('aiden')
    aiden.name = 'aiden'
    print(aiden.name) # ====> getter가 자동으로 호출됨.
    			      # method를 마치 속성처럼 사용할 수 있따. 
        
    ```

* 예시 3

  ![image-20220202134234000](images\image-20220202134234000.png)

  ![image-20220202134250996](images\image-20220202134250996.png)