# Python_TEST



## :zero: 파이썬 기초



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

![image-20220203004655861](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203004655861.png)



### 8. 식별 연산자

* **is** 연산자

* 파이썬에서 -5부터 256까지의 id는 동일

* 257이후의 id는 각각 다르다

  ![image-20220203005023726](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220203005023726.png)



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





## 제어문

### 1. if 조건문

