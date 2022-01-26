# Python Error/Exception Handling

## :star: :star: 디버깅

* 직접 확인

  * branches

    모든 조건을 커버하고 있는지

  * for loops

    반복문 원하는 횟수만큼 실행되는지, 반복문의 값(결과)이 맞는지

  * while loops

    종료조건이 있는지

  * function

    함수 호출시, 함수 파라미터, 함수 결과

* 디버깅

  * print함수 활용
    * 특정 함수 결과, 반복/조건 결과 등 나눠 생각, 코드를 section으로 나눠 생각
  * 개발 환경(text editor, IDE)등에서 제공하는 기능 활용
    * breakpoint, 변수 조회 등
  * Python tutor 활용
  * **뇌컴파일, 눈디버깅(???)**

* 에러 메시지가 발생하는 경우

  * 해당하는 위치를 찾아 메시지를 해결

* 로직 에러가 발생하는 경우

  * 명시적인 에러 메시지 없이 예상과 다른 결과가 나온 경우
    * 정상적으로 동작하였던 코드 이후 작성된 코드를 생각해봄
    * 전체 코드를 살펴봄
    * 휴직을 가져봄
    * **누군가에게 설명해봄**



## 에러와 예외

### 문법 에러(Syntax Error)

1. Invalid syntax

   ```python
   whilem # ':' 빼먹음
   ```

2. assign to literal

   ```python
   5 = 3 # 특정 고유한 값에는 할당할 수 없어
   ```

3. EOL (End of Line)

   ```python
   print('hello	# 문장이 안끝났어
   ```

4. EOF (End of File) 

   ```python
   print(	#파일이 안끝나
   ```

   

### 예외 (Exception)

1. ZerioDivisionError: 0으로 나누고자할 때 발생

   ```python
   10/0 #0으로 나누는거 불가능
   ```

2. NameError: namespace상에 이름이 없는 경우, 오타 등

   ```python
   print(name_error) # name_error라는 변수를 정의되지 않음
   ```

3. TypeError:

   1. Type 불일치

      ```python
      1 + '1' # 정수랑 string은 안됨
      ```

   2. Argument 누락

      ```python
      divmod() #divmod안에 값이 없음
      ```

      ```python
      import random
      random.sample()
      ```

   3. Argument 개수 초과

      ```python
      divmod(1, 2, 3) # 갯수 초과 (2개만)
      ```

   4. Argument type 불일치

      ```python
      ```

      

4. ValueError: 타입은 올바르나 값이 적절하지 않거나 없는 경우

   ```python
   ```

   

5. **IndexError**: 인덱스가 존재하지 않거나 범위를 벗어나는 경우

   ```python
   empty_list = []
   empty_list[2]     #for 문에 인덱스가 잘못되었구나
   ```

   

6. KeyError: 키가 존재하지 않는 경우

7. ModuleNotFoundError: 존재하지 않는 모듈을 import하는경우

8. ImportError: Module은 있으나 존재하지 않는 클래스/함수를 가져오는 경우

9. KeyboardInterrupt: 임의로 프로그램을 종료하였을 때

10. IndentationError: indentation이 적절하지 않는 경우

### 파이썬 내장 예외

* 파이썬 내장 예외의 클래스 계층 구조

  ![image-20220124151824153](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124151824153.png)





---

## :star:예외 처리

### 1. 예외 처리

* try 문(statement)

  * 오류가 발생할 가능성이 있는 코드를 실행
  * 예외가 발생되지 않으면, except 실행 없이 실행

* except 절(clause)

  * 예외가 발생하면 except절이 실행
  * 예외 상황을 처리하는 코드를 받아서 적절한 조치를 취함

  

### 2. 작성 방법

```python
try: 
	try 명령문
except 예외그룹-1 as 변수-1:	# try 명령문에서 에러나면 except 실행, as 별명
        예외처리 명령문 1
except 예외그룹-2 as 변수-2:
        예외처리 명령문 
else:		# try 명령문에서 에러가 나지 않으면 
finally:	# try 명령문이 되든 안되든 finally 밑에 있는건 써주세요(선택)
    finally 명령문
```

```python
# as 는 설명
import random as rd
random.sample(~)	# 이렇게 써야 되는 걸
rd.sample(~)		# 이렇게 쓸 수 있다!
```



### 3. :question: 예외 처리 예시

```python
try:
user_input = int(input('숫자를 입력해 주세요: '))
print(f'입력한 숫자에 10을 곱하면 {user_input*10}이 됩니다.')

# 여기다가 숫자 10을 쓰면 100이 나옴
# 그런데 문자를 쓰면?

except ValueError 
# ValueError인지 어떻게 아냐면 -> 해보고 Error발생시켜보세여
# 만약 except 뒤에 아무것도 안 쓴다면 어떤 Error가 나든지 무조건 출력
# 그런데 이런 경우에는 에러가 나도 어떤 에러가 났는지 구분할 수 없음. 그래서 추천X
	print('너 누구냐 ㅡㅡ?')

except IndexError:
    print('index 넘었잖아 바보야 ㅡㅡ')
   
else:
    print('아이 이뻐라 ^ㅇ^')
    
finally:
    print('종료')
```

```python
try:
user_input = int(input('숫자를 입력해 주세요: '))
print(f'입력한 숫자에 10을 곱하면 {user_input*10}이 됩니다.')

a = [1, 2, 3]
print = a[5]

# 여기다가 숫자 10을 쓰면 100이 나옴
# 그런데 문자를 쓰면?

except Exception: 
    print('에러!!')
    #Exception이 ValueError보다 상위에 있으므로, Exception을 쓴다면 밑에 애들은 반영이 안 됨. 따라서 작은 except들을 exception 먼저 쓰는 것이 좋다. 
    
except ValueError 
	print('너 숫자 아니지?')

except IndexError:
    print('index 넘었잖아 바보야 ㅡㅡ')
   
else:
    print('아이 이뻐라 ^ㅇ^')
    
finally:
    print('종료')
```

```python
try:
    num = input('숫자입력 :')
    print(int(num))
except ValueError as e :
    print(f'{e}, 숫자가 입력되지 않았습니다.')
```

숫자입력: abc

'숫자가 입력되지 않았습니다. '



### 4. 처리 순서

![image-20220124151844261](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124151844261.png)



### 5. 복수의 예외 처리 실습

1. 100을 사용자가 입력한 값으로 나누고 출력하는 코드를 작성해보시오.

   - 먼저, 발생 가능한 에러가 무엇인지 예상해보시오

   ```python
   num = input('100으로 나눌 값을 입력하시오 : ')
   print(100/int(num))
   
   # 100/int('a') ===> ValueError
   # 100/int('0') ===> ZeroDivisionError
   ```

2.  100을 사용자가 입력한 정수로 나누고 출력하는 코드를 작성해보시오.

   ```python
   #1. 발생 가능한 에러를 모두 명시
   try:
       num = input('100으로 나눌 값을 입력하시오: ')
       100/int(num)
   except (ValueError, ZeroDivisionError):
       print('제대로 입력해줘')
   
       
   #2. 에러 별로 별도의 에러처리
   try:
       num = input('값을 입력하시오: ')
       100/int(num)
   except ValueError:
       print('숫자를 넣어주세요.')
   except ZeroDivisionError: 
       print('0으로 나눌 수 없습니다.')
   except:
       print('에러는 모르지만 에러가 발생하였습니다.')
       
   #3. 순차적으로 수행되므로, 가장 작은 범주부터 예외 처리를 해야 함
   try:
       num = input('값을 입력하시오: ')
       100/int(num)
   except Exception: # Exception은 가장 큰 범주
       print('에러는 모르지만 에러가 발생하였습니다.')
   except ValueError:
       print('숫자를 넣어')
       
   #값을 입력하시오: 안녕
   #에러는 모르지만 에러가 발생하였습니다.
   ```

   

### 6. :question: 예외 처리 종합

* try

* except

* else

* finally (cleanup): 파일을 열고 읽는 코드를 작성하느 경우
  * 파일 열기 시도
  * 파일 없는 경우 ==> 해당 파일이 없습니다 
  
  

### 7. 예외 처리 종합 예시

![image-20220124155844393](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124155844393.png)

* 단, 알고리즘 문제는 try except 쓰지 않음 무조건 맞는 문제만 주기 때문임



### 8. 에러 메시지 처리(as)

![image-20220124155906083](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124155906083.png)



---



## 예외 발생 시키기

### raise statement

* 에러를 내가 발생시키는 것. 파이썬이 터지기 전에.

```python
raise <표현식> (메시지)

#표현식 <== 예외 타입 지정. (주어지지 않을 경우 현재 스코프에서 활성화된 마지막 예외를 다시 일으킴)
```

```PYTHON
try:
    user_input = int(input('숫자: '))
    
    lst = [1, 2, 3, 4]
    
    if user_input > 5:
        raise IndexError	
        # index 4 이상이면 IndexError 내버려 
        # raise 써서 내가 정의한 Error도 만들 수 있따
        # GyuminError 써도 가능 -> Error가 정의된 Except 문으로 바로 이동
       
    else:
        print(lst[user_input])

except IndexError:
    print('에러!')
```



### assert statement

* assert는 상태 검증에 사용되며, 표현식이 False인 경우 AssertionError

* 일반적으로 디버깅 용도로 쓴다

  ```python
  assert <표현식>, <메시지>
  ```

  ```python
  try:
  except AssertionError:
      print("~~~")
      
  #위의 try - except 문을 아래처럼 표현가능하다.
  
  lst = [1, 2, 3]
  user_input = int(input(" : "))
  assert user_input <= 2, "index 잘못됨"
  
  print(lst[user_input])
  
  # 입력을 1로 하면 True가 되어서 assert 구문을 무시하고 지나간다
  # 입력이 5가 되면 False가 되어서 AssertionError가 나온다
  # Logic 자체의 검증보다는, 뭔가 오류가 날 것 같이 불안한 부분에 간이역처럼 써 놓는 것
  # __debug__ 라는 것과도 같이 쓰이니까 구글링해보세요 궁금하면
  # 안궁금하면 어떡하져
  # 그래서 그냥 넘어가려고 합니다
  ```

  

```python
assert len([1, 2]) == 1, '길이가 1이 아닙니다'   #디버깅 의도로 많이 쓰임
```



### raise vs assert

* raise: 실제 프로덕션 코드에서 활용
* assert: 특정 조건이 거짓이면 발생. 디버깅 및 테스트에서 활용