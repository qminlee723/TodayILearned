

# Python Control Statement

* 파이썬은 기본적으로 위에서부터 아래로 순차적으로 명령을 수행
* 특정 상황에 따라 코드를 선택적으로 실행(분기/조건)하거나 계속하여 실행(반복)하는 제어 필요
* 제어문은 순서도(flow chart로 표현이 가능)



## 조건문(Conditional Statement)

### 1. 기본

* 조건문은 참/거짓을 판단할 수 있는 조건식과 함께 사용한다. 

* expression에는 참/거짓에 대한 조건식

  * 조건이 참인 경우, 이후 들여쓰기 되어있는 코드 블럭을 실행

  * 이외의 경우, else 이후 들여쓰기 되어있는 코드 블럭을 실행

  * else는 선택적

    ```python
    if <expression == True>:
    	#Run this Code block
    else
    	# Run this Code block
    ```

#### 연습문제

1. 아래의 순서도를 코드로 나타내시오

   <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118091132661.png" alt="image-20220118091132661" style="zoom:50%;" />

   ```python
   a = 5
   if a > 5:
       print('5 초과')
   else:
       print('5 이하')
   print(a)
   ```

   5 이하

   5

   

2. 아래의 순서도를 코드로 나타내시오

   <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118091213092.png" alt="image-20220118091213092" style="zoom:50%;" />

   ```python
   a = 6
   if a > 5
   	print('5 초과')
   else a <= 5 
   	print('5 이하')
   print(a)
   ```

   5 초과

   6

   

3. 조건문을 통해 변수 num의 값이 홀수/짝수 여부를 출력하시오

   - 이 때, num은 input을 통해 사용자로부터 입력을 받으시오

   ```python
   num = int(input('숫자를 입력하세요: '))
   if num % 2: # if num % 2 == 1:
       print('홀수입니다.')
   else:
       print('짝수입니다.')
   
   ```



### 2. 복수 조건문

* 복수의 조건식을 활용할 경우, elif를 활용하여 표현함

  ```python
  if <expression>:
  	#Code block
  elif <expression>:
  	#Code block
  elif <expression>:
  	#Code block
  else:
  	#Code bock
  ```



#### :white_check_mark: 연습 문제

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118092058302.png" alt="image-20220118092058302" style="zoom: 67%;" />

```python
dust = 80

if dust > 150:
    print('매우 나쁨')
elif dust > 80:
	print('나쁨')
elif dust > 30:
	print('보통')
else:
    print('좋음')
print('미세먼지 확인 완료!')
```

보통

미세먼지 확인 완료!



### 3. 중첩 조건문

* 조건문은 다른 조건문에 중첩되어 사용될 수 있다. 

  * Indentation 조심!

  ```python
  if <expression>:
  	#Code block
  		if <expression>:
  			#Code block
  else:
  	#Code block
  ```

  

#### :white_check_mark: 연습 문제

1. <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118094432031.png" alt="image-20220118094432031" style="zoom:67%;" />

   ```python
   dust = 500
   
   if dust > 150:
       print('매우 나쁨')
       if dust > 300:
           print('실외 활동을 자제하세요.')
   elif dust > 80:
   	print('나쁨')
   elif dust > 30:
   	print('보통')
   else:
       if dust >= 0
       	print('좋음')
       else: 
           print('값이 잘못 되었습니다.')
   ```

   매우 나쁨

   실외 활동을 자제하세요.

   

	### 4. 조건 표현식(Conditional Expression)

*  조건 표현식은 일반적으로 저건에 따라 값을 정할 때 활용
* 삼항 연산자(Ternary Operator)로 부르기도 함
* 무엇보다 코드 자체가 짧아짐

```python
<true인 경우 값> if <expression> else <false인 경우 값>
```

* **일반: if 는 만약에 이거면, 이걸 주고, 아니면 저걸 준다**
* **:sparkles: 조건 표현식: 이걸 줄거야 만약 이거면. 아니면 저거 줌 :sparkles:**



#### :white_check_mark: 연습 문제

1. **num이 정수 일 때, 아래의 코드는 무엇을 위한 코드일까요?**

   ```python
   value = num if num >=0 else -num
   ```

   답: 절대값을 저장하기 위한 코드 

   

2. **아래의 코드는 무엇을 위한 코드일까요?**

   <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118101607947.png" alt="image-20220118101607947" style="zoom:67%;" />

   답: 절대값 계산기

   

3. **다음의 코드와 동일한 조건 표현식을 작성하시오**

   <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118095753128.png" alt="image-20220118095753128" style="zoom: 67%;" />

   ```python
   result = '홀수입니다.' if num % 2 else '짝수입니다' 
   print(result)
   ```

   

4. **다음의 코드와 동일한 조건문을 작성하시오**

   <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118095825435.png" alt="image-20220118095825435" style="zoom: 80%;" />

   ```python
   num = -5
   if num >= 0:
   	value = num
   else:
   	value = 0
   print(value)
   ```

   



## 반복문(Repetitive Statement)

* 특정 조건을 도달할 때까지, 계속 반복되는 일련의 문장

### 1. While 문

* 종료조건에 해당하는 코드를 통해 반복문을 종료시켜야 한다.

  * 조건이 참인 경우 들여쓰기 되어있는 코드 블록이 실행됨

  * 코드 블록이 모두 실행되고, 다시 조건식을 검사하며 반복적으로 실행됨

  * while문은 무한 루프를 하지 않도록 종료조건이 반드시 필요하다

    ```python
    while <expression>:
    	#Code block
    ```

#### 예시

1.  **아래의 순서도를 코드로 나타내시오**

   <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118104217984.png" alt="image-20220118104217984" style="zoom:50%;" />

   ```python
   a = 0
   while a < 5
   	print('a')
       a += 1
   print('끝')
   ```

   :question: += 뜻

   

2.  **1부터 사용자가 입력한 양의 정수까지의 총합을 구하는 코드를 작성하시오.**

   <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118104311058.png" alt="image-20220118104311058" style="zoom:80%;" />

   ```python
   while n <= user_input:
       total += n
       n += 1
   print(total)
   ```



### 2. For 문

* 반복 가능한 객체를 모두 순회하면 종료된다(종료조건 필요X)

* 시퀀스(string, tuple, list, range)를 포함한 순회가능한 객체(iterable)요소를 모두 순회함

  ```python
  for <변수명> in <iterable>:
  	#Code block
  ```

#### 예시

1. **아래의 순서도를 코드로 나타내시오**

   <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118110945321.png" alt="image-20220118110945321" style="zoom: 67%;" />

   ```python
   for fruit in ['apple', 'mango', 'banana']:
   	print(fruit)
   print('끝')
   ```

   apple

   mango

   banana

   끝



#### 일반 형식

* Iterable

  * 순회할 수 있는 자료형(str, list, dic 등)
  * 순회형 함수(range, enumerate)

  ```python
  for <변수명> in <iterable>:
  	#Code block
  else:				#else는 선택
  	#Code block
  ```





#### :star: 문자열(String) 순회

* 실습

  1. **사용자가 입력한 문자를 한 글자씩 출력하시오.**

     ```python
     chars = input()
     ```

     happy

     ```python
     for char in chars:
     	print(char)
     ```

     h

     a

     p

     p

     y

     

  2.  **사용자가 입력한 문자를 range를 활용하여 한 글자씩 출력하시오.**

     ```python
     chars = input()
     ```

     happy

     ```python
     for idx in range(len(chars)):	# len() 많이 쓰임
     	print(chars[idx])
     ```

     h

     a

     p

     p

     y

     

     <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118112215451.png" alt="image-20220118112215451" style="zoom:80%;" />

     

#### 딕셔너리(Dictionary) 순회

* keys(): Key로 구성된 결과
* values(): value로 구성된 결과
* items(): (Key, value)의 튜플로 구성된 결과

```python
grades = {'john': 80, 'eric': 90}
print(grades.keys())
print(grades.values())
print(grades.items())
```

dict_keys(['john', 'eric'])

dict_values([80, 90])

dict_items([('john', 80), ('eric', 90)])



```python
grades = {'john': 80, 'eric': 90}
for name, score in grades.items():
	print(name, score)
```

john 80

eric 90





#### :star: :star: Enumerate 순회

* **enumerate()**

* **인덱스**와 객체를 쌍으로 담은 열거형 객체 반환

  * (index, value)형태의 tuple로 구성된 열거 객체를 반환

    ```python
    members = ['민수', '영희', '철수']
    ```

    ```python
    for idx, member in enumerate(members):
    	print(idx, member)
    ```

    0 민수

    1 영희

    2 철수

* **공식 문서**(Official Documents)<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118111959698.png" alt="image-20220118111959698" style="zoom:80%;" />

* 예제

  ```python
  enumerate(members)
  ```

  <enumerate at 0x105d3e100>

  ```python
  list(enumerate(members)) 	#숫자와 값의 tuple
  ```

  [(0, '민수'), (1, '영희'), (2, '철수')]

  ```python
  list(enumerate(members, start=1))	
  #기본값 0, start를 지정하면 해당값부터 순차적으로 증가한다.
  ```

  [(1, '민수'), (2, '영희'), (3, '철수')]

  

#### List Comprehension

* 표현식과 제어문을 통해 특정한 값을 가진 리스트를 간결하게 생성하는 방법

  ```python
  [<expression> for <변수> in <iterable>]	# 추천!
  ```

  ```python
  [<expression> for <변수> in <iterable> if <조건식>]
  ```

  

* 실습

  1. 1~3의 세제곱의 결과가 담긴 리스트를 만드시오

     ![image-20220118113029452](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118113029452.png)

     ```python
     [number**3 for number in range(1, 4)]
     ```

     [1, 8, 27]

     

#### :question: Dictionary Comprehension

* 표현식과 제어문을 통해 특정한 값을 가진 딕셔너리를 간결하게 생성하는 방법

  ```python
  {Key: value for <변수> in <iterable>}
  ```

  ```python
  {key:value for <변수> in <iterable> if <조건식>}
  ```

  

* 실습

  1. 1~3의 세제곱의 결과가 담긴 딕셔너리를 만드시오

     <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220118123743621.png" alt="image-20220118123743621" style="zoom:80%;" />

     ```python
     {number:number**3 for number in range(1,4)}
     ```

     {1: 1, 2: 8, 3: 27}

     

  2. 반복문과 조건문만 활용하여 1~30까지 숫자 중에 홀수만 출력하시오

     ```python
     for i in range(1, 31):
     	if i % 2:
     		print(i)
     ```

     1

     3

     5

     7

     ..

     29



### 3. 반복문 제어

* break, continue, for-else

#### break

* break문을 만나면, 반복문은 종료됨

```python
n = 0 
while True:
    if n == 3:
        break
    print(n)
    n += 1
```

0

1

2

```python
for i in range(10):
	if i > 1:
		print('0과 1만 필요해!')
		break
	print(i)
```

0

1

0과 1만 필요해!



#### continue

* continue 이후의 코드 블록은 수행하지 않고, 다음 반복을 수행

```python
for i in range(6):
	if i % 2 == 0:
		continue
	print(i)
# continue를 만나면, 이후 코드인 print(i)가 실행되지 않고 바로 다음 반복을 시행
```

1

3

5



#### pass

* 아무것도 하지 않음

  * 특별히 할 일이 없을 때, SyntaxError를 막기 위해서 씀

  ```python
  for i in range(5):
  	if i == 3:
  		pass
  	print(i)
  ```

  ```python
  for i in range(5):
  	if i == 3:
  		continue
  	print(i)
  ```

  

#### for-else

* 끝까지 반복문을 실행한 이후에 else문 실행
* else 문은 break로 중단되었는지 여부에 따라 실행

```python
for char in 'apple':
	if char == 'b':
		print('b!')
		break
else:
	print('b가 없습니다.')
```

```python
for char in 'banana':
	if char == 'b':
		print('b!')
		break
else:
	print('b가 없습니다.')
```







