# Python OOP

## OVERVIEW

**객체지향프로그래밍**

- oop기초
- 인스턴스
- 클래스
- 메소드

**객체지향의 핵심개념**

- 추상화
- 상속
- 다형성
- 캡슐화



---

## 객체 지향 프로그래밍(OOP)

- 객체(object)는 특정 타입의 인스턴스

  - 123, 900, 5는 모두 int의 인스턴스
  - 'hello', 'bye'는 모두 string의 인스턴스
  - [232, 89, 1], []은 모두 list의 인스턴스
  - 인스턴스: 만들어진 객체
    - 객체: 개념
    - 클래스로 객체가 만들어지면(==메모리에 추가되면) 인스턴스라고 함
    - 클래스는 붕어빵 틀이고, 인스턴스는 붕어빵

- 객체의 특징

  - 타입(type) 

    - 어떤 연산자(operator)와 조작(method)이 가능한가?
    - 데이터의 타입이 클래스!
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
    dir(a)
    dir(b)
    ```

    

    ```python
    123.__class__
    ```

    

    * a=integer
      * 속성과 메소드가 정의되어 있는 것들을 한꺼번에 다 볼 수 있다.
    * b =string
      * istitle, isupper, islower, join.... etc
      * 어떠한 class 안에 정의되어 있는 메소드를 호출

  - 속성(attribute) : 어떤 상태(데이터)를 가지는가?

  - 조작법(method) : 어떤 행위(함수)를 할 수 있는가?

  - 객체(object) = 속성(attribute) + 기능(Method)

  - .method() 에서 '.'도 dot 연산자

    - len()같은 경우, 파이썬 안에서 정의가 되어 있음
    - 꺼내 쓰면 됩니다.

  

- 객체지향프로그래밍

  - 프로그램을 여러 개의 독립된 객체들과 그 객체들 간의 상호작용으로 파악하는 프로그래밍 방법
  - <-> 절차지향프로그래밍

- 예시

  ```python
  # 절차지향프로그래밍
  
  a = [1, 2, 3]
  
  a = sorted(a)
  
  a = reversed(a)
  
  def append(list, value):
      return 1 + [value]
  
  a = append(a, 4)
  ```

  ```python
  # 객체지향프로그래밍
  
  a = [1 ,2, 3]
  
  a. sort()
  
  a.reverse()
  
  a.append(4)	# 얘는 스스로 a를 호출해서 사용가능
  
  ```

- 객체지향 프로그래밍이 필요한 이유

  - 현실 세계를 프로그램 설계에 반영(추상화)

    ```python
    # 객체 X
    
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
    # 객체지향
    
    class Person:	#class 이름은 Pascal 케이스로!!
        
        def __init__(self, name, gender):
            self.name = name
            self.gender = gender
            
        def greeting(self):
            print(f'안녕하세요, {self.name}입니다.')
    
    jimin = Person('지민', '남')
    jimin.greeting()
    
    jieun = Person('아이유', '여')
    jieun.greeting()       
    
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

    * jimin, jieun 등은 인스턴스

- 예시: 사각형 넓이 구하기

  - 절차지향

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220126093358327.png" alt="image-20220126093358327" style="zoom:50%;" />

    

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

    20000

    100

    ```python
    # 함수
    def area(x, y):
        return x * y
    
    print(area(x_01, y_01))
    print(area(x_02, y_02))
    ```

    20000

    100

    

  - 객체지향프로그래밍

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220126093246206.png" alt="image-20220126093246206" style="zoom:50%;" />

    ```python
    # 객체
    class Rectangle:
        
        def area(self):
            return self.x * self.y
        
    r1 = Rectangle()
    r1.x = 100
    r1.y = 200
    r1.area()
    ```

    20000

    ```python
    r2 = Rectangle()
    r2.x = 10
    r2.y = 10
    r2.area()
    ```

    100

    * 사각형 - class
    * 각 사각형(R1, R2) - instance
    * 사각형의 정보 - attribute(속성)
      * 가로 길이, 세로 길이
    * 사각형의 행동 -  method
      * 넓이를 구한다, 높이를 구한다

* 객체지향의 장점
  * 프로그램을 유연하고 변경이 용이하게 만들기 때문에 대규모 소프트웨어개발에 사용
  * 소프트웨어 개발과 보수를 간편하게 하며, 보다 직관적인 코드 분석을 가능하게 함
* 

### OOP 기초

* 기본 문법

  ```python
  class MyClass:				# 클래스 정의
  
  my_instance = MyClass		# 인스턴스 생성
  my_instance.my_method()		# 메소드 호출
  my_instance.my_attribute	# 속성
  ```

  

* 클래스와 인스턴스

  * 클래스: 객체들의 분류

    ```python
    class Person:
        name = 'aiden'		#attribute
        
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

    

  * 인스턴스: 하나하나의 실체(예)

  

* 속성

  * 특정 데이터 타입/클래스의 객체들이 가지게 될 상태/데이터를 의미

    

* 메소드

  * 특정 데이터 타입/클래스의 객체에 공통적으로 적용 가능한 행위(함수)

    ```python
    class Person
    
    	def talk(self):			# 메소드 = 클래스 내부에 정의된 함수
            print('안녕')
            
        def eat(self, food):	# def eat(self, *args):
            print(f'{food}를 냠냠')
        
    ```

    

* 객체 비교하기

  * ==
    * 동등한(equal)
    * 변수가 참조하는 객체가 동등한 경우 True
    * 두 객체가 같아 보이지만, 실제로 동일한 대상을 가리키고 있다고 확인해 준 것은 아님
  * is
    * 동일한(identical)
    * 두 변수가 동일한 객체를 가리키는 경우 True

### 인스턴스

* 인스턴스 변수

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

* 인스턴스 메소드

  * 인스턴스 변수를 사용하거나, 인스턴스 변수에 값을 설정하는 메소드
  * 클래스 내부에 정의되는 메소드의 기본
  * 호출 시, 첫번째 인자로 **인스턴스 자기자신(self)**이 전달됨

* self

  * 인스턴스 자기자신

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
    
    # p1.test()
    # TypeError: test() takes 0 positional arguments but 1 was given
        
    # <__main__.Person object at 0x00000228B53D4F70>
    s = p1.test()
    print(s, p1)
    ```

    

* 생성자(constructor) 메소드

  * 인스턴스 객체가 생성될 때 자동으로 호출되는 메소드

  * 인스턴스 변수들의 초기값을 설정

    * 인스턴스 생성

    * **\__init__(self)**메소드 자동호출

      * 클래스가 생성될 때 자동적으로 불러와지는 함수.

        ```python
        class Person:
            cnt = 0
            # 클래스가 인스턴스를 만들어줄때는 __init__이 호출됨
            
            def __init__(self):
                Person.cnt +=1
                # 같은 이름으로 함수를 정의하면. 
                # 마지막에 함수를 정의한 것들만 출력/반환된다. 
            
            def __init__(self, name):	
                # instance를 생성하는 녀석
                # instance 변수는 각각의 class에서 독립적이니까 각각 나옴
                self.name = name
                
                # class cnt가 아니라, instance의 독립적인 cnt 만드는 것
                # class와는 상관없게 된다. (Python은 작은 것 부터 찾음)
                Person.cnt += 1
                
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

      

* 소멸자(destructor) 메소드

  * 인스턴스 객체가 소멸(파괴)되기 직전에 

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

    

* 매직 메소드

  * Double underscore(__)가 있는 메소드는 특수한 동작을 위해 만들어진 메소드로, 스페셜 메소드 또는 매직 메소드라고 불린다.

  * 특정 상황에 자동으로 불리는 메소드

  * 매직 메소드 예시

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220126103640656.png" alt="image-20220126103640656" style="zoom:67%;" />

    1. \__str__ : 해당 객체의 출력 형태를 지정

       - 프린트 함수를 호출할 때, 자동으로 호출
       - 어떤 인스턴스를 출력하면 \__str__의 return값이 출력

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

       

    2. \__gt__: 부등호 연산자(>, greater than)

    3. \__eq__: 등호 연산자(=, equal)

    4. \__doc__: docstring

       ```
       'abc'.__doc__
       ```

       

    

### 클래스

* 클래스 변수

  * 한 클래스의 모든 인스턴스라도 똑같은 값을 가지고 있는 속성 :question:

  * 클래스 속성(attribute)

    * 한 클래스의 모든 인스턴스라도 똑같은 값을 가지고 있는 속성

  * 클래스 선언 내부에서의 정의

    ```python
    <classname>.<name>으로 접근 및 할당
    
    class Circle:
        pi = 3.14
        
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

  

* 클래스 메소드

  * 클래스가 사용할 메소드

  * @classmethod 데코레이터를 사용하여 정의

    * 데코레이터: 함수를 어떤 함수로 꾸며서 새로운 기능을 부여

  * 호출 시, 첫번째 인자로 클래스가 전달됨

    ```python
    class MyClass:				#class 이름은 Camel Case
        var = 'Class 변수'
        
        #클래스 메서드: 클래스를 조작하고 싶어
        # 함수 내붸 클래스를 던져주도록 설계
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

    

* 스태틱 메소드

  * 클래스가 사용할 메소드

  * @staticmetion 데코레이터를 사용하여 정의

  * 호출 시, 어떠한 인자도 전달되지 않음(클래스 정보에 접근/수정 불가)

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

    

* 인스턴스와 클래스간의 이름공간(namespace)

  * 클래스 정의시, 클래스와 해당하는 이름공간 생성
  * 인스턴스 만들면, 인스턴스 객체가 생성되고 이름 공간 생성
  * 인스턴스에서 특정 '속성'에 접근하면, 인스턴스-클래스 순서로 탐색

### 메소드

![image-20220126094750348](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220126094750348.png)

* 인스턴스 메소드
  * 예시
* 클래스 메소드
  * 예시
* 스태틱 메소드
  * 예시



## 객체지향의 핵심개념

### 추상화

* 
* 예시

### 상속

* 

* 상속 관련 함수와 메소드

  1. isinstance(object, classinfo)
  2. issubclass(class, classinfo)
  3. super()

* 정리

* 다중 상속

* 상속 관련 함수와 메소드

  * mro 메소드(Method Resolution Order)

* 예시

  ```python
  class Person:
      
      def __init__(self, name, age):
          self.name( = name)
          self.age ( = age)
  def talk(self):
      print('반갑습니다, {ls}')
  ```

  

### 다형성(Polymorphism)

* 
* 메소드 오버라이딩
* 



### 캡슐화

* 

* 접근제어자 종류

  * Public Access Modifier
  * Protected Access Modifier
  * Private Access Modifier
    * 언더바 2개로 시작하는 메소드나 속성
    * 본 클래스 내부에서만 사용이 가능
    * 하위 클래스 상속 및 호출이 불가능

* getter메소드와 setter 메소드

  * getter

    * 데코레이터 사용

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

      

  * setter

