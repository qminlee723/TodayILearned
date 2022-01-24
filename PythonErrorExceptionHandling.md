# Python Error/Exception Handling

## 디버깅

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
  * 뇌컴파일, 눈디버깅(???)

* 에러 메시지가 발생하는 경우

  * 해당하는 위치를 찾아 메시지를 해결

* 로직 에러가 발생하는 경우

  * 명시적인 에러 메시지 없이 예상과 다른 결과가 나온 경우
    * 정상적으로 동작하였던 코드 이후 작성된 코드를 생각해봄
    * 전체 코드를 살펴봄
    * 휴직을 가져봄
    * 누군가에게 설명해봄



## 에러와 예외

### 문법 에러(Syntax Error)

1. Invalid syntax

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

2. NameError: namespace상에 이름이 없는 경우, 오타 등

3. TypeError:

   1. Type 불일치

      ```python
      1 + '1'
      ```

   2. Argument 누락

      ```python
      divmod()
      ```

      

   3. Argument 개수 초과

      ```python
      
      ```

      

   4. Argument type 불일치

      ```python
      ```

      

4. ValueError: 타입은 올바르나 값이 적절하지 않거나 없는 경우

   ```python
   ```

   

5. IndexError: 인덱스가 존재하지 않거나 범위를 벗어나는 경우

   ```python
   ```

   

6. KeyError: 키가 존재하지 않는 경우

7. ModuleNotFoundError: 존재하지 않는 모듈을 import하는경우

8. ImportError: Module은 있으나 존재하지 않는 클래스/함수를 가져오는 경우

9. KeyboardInterrupt: 임의로 프로그램을 종료하였을 때

10. IndentationError: indentation이 적절하지 않는 경우

### 파이썬 내장 예외

* 파이썬 내장 예외의 클래스 계층 구조

  ![image-20220124151824153](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124151824153.png)



## 예외 처리

### 예외 처리

* try 문(statement)

  * 오류가 발생할 가능성이 있는 코드를 실행
  * 예외가 발생되지 않으면, except 실행 없이 실행

* except 절(clause)

  * 예외가 발생하면 except절이 실행
  * 예외 상황을 처리하는 코드를 받아서 적절한 조치를 취함

  

### 작성 방법

```python
try: 
	try 명령문
except: 예외그룹-1 as 변수-1:
        예외처리 명령문 1
except: 예외그룹-2 as 변수-2:
        예외처리 명령문 2
finally:
    finally 명령문
```



### :question: 예외 처리 예시

```python
try:
    num = input('숫자입력 :')
    print(int(num))
except ValueError as e :
    print(f'{e}, 숫자가 입력되지 않았습니다.')
```

숫자입력: abc

'숫자가 입력되지 않았습니다. '

### 처리 순서

![image-20220124151844261](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124151844261.png)

### 복수의 예외 처리 실습

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

   

### :question: 예외 처리 종합

* try
* except
* else
* finally (cleanup): 파일을 열고 읽는 코드를 작성하느 경우
  * 파일 열기 시도
  * 파일 없는 경우 ==> 해당 파일이 없습니다 

### 예외 처리 종합 예시

![image-20220124155844393](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124155844393.png)

* 

### 에러 메시지 처리(as)

![image-20220124155906083](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124155906083.png)









## 예외 발생 시키기

### raise statement

```python
raise <표현식> (메시지)

#표현식 <== 예외 타입 지정. (주어지지 않을 경우 현재 스코프에서 활성화된 마지막 예외를 다시 일으킴)
```



### assert statement

```python
assert len([1, 2]) == 1, '길이가 1이 아닙니다'   #디버깅 의도로 많이 쓰임
```



### raise vs assert

* raise: 실제 프로덕션 코드에서 활용
* assert: 특정 조건이 거짓이면 발생. 디버깅 및 테스트에서 활용