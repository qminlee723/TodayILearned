# Algorithm Stack

## :zero: OVERVIEW

1. 스택
2. 재귀호출
3. Memoization & DP
4. DFS



## :one: 스택

### 1. 스택의 특성

#### 스택의 특성

* 물건을 쌓아올린 듯 자료를 쌓아 올린 형태의 자료구조
* 스택에 젖아된 자료는 선형 구조를 갖는다
  * 선형 구조: 자료 간의 관계가 1대 1의 관계를 갖는다
  * 비선형 구조: 자료 간의 관계가 1대 N의 관계를 갖는다(예:트리)
* 스택에 자료를 삽입하거나 스택에서 자료를 꺼낼 숭 ㅣㅆ다.
* **마지막에 삽입한 자료를 가장 먼저 꺼낸다. Last-In-First-Out**
* 웹 브라우저의 ''뒤로가기'' 버튼
  * 가장 최근에 방문한 웹페이지부터 불러옴



#### 구현하기 위해서 필요한 자료구조

* 자료구조: 자료를 선형으로 저장할 저장소

  * 배열을 사용할 수 있다
  * 저장소 자체를 스택이라 부르기도 한다
  * 스택에서 마지막 삽입된 원소의 위치를 top이라 부른다.

* 스택의 삽입/삭제 과정

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220221162315997.png" alt="image-20220221162315997" style="zoom: 67%;" />

  

### 2. 함수 콜 스택 

```python
def factorial(n): 
    if n == 1:
        return
    else:
        return n * factorial(n-1)

print(factorial(3))
```

* 정보학의 아버지 Friedrich Ludwig Bauer
* Recursive function calls and the dynamic runtime behavior of computer programs.
* Stack overflow



### 3. 스택의 연산

* CreateStack: 스택을 생성하는 연산, `size`필요
* IsEmpty: 스택이 현재 비어있는지를 확인하는 연산, `True, False` 리턴
* IsFull: 스택이 현재 꽉 차있는지를 확인하는 연산, `True, False` 리턴
* Push: 스택에 새로운 데이터 요소를 삽입하는 연산
* **Pop**: 스택에서 가장 위에 있는 요소를 제거하는 연산, 데이터 반환. 꺼낸 자료는 삽입한 자료의 역순으로 꺼낸다. 
* **Peek**: 스택에서 가장 위(top)에 있는 요소를 반환하는 연산
* :star: Pop과 Peek의 차이점



### 4. 스택의 데이터 구조(Data structure of stack)

* top: 스택의 가장 위에 있는 위치를 저장하고 있는 데이터
* size: 스택의 크기를 저장하고 있는 데이터
* itmes: 스택에 담길 데이터를 저장할 데이터 구조





### 5. 스택의 구현

```python
class Stack:
    def __init__(self, size):
        self.size = size # 스택의 사이즈
        self.top = -1
        self.items = [None] * self.size
```

```python
        class Stack:
    ...
    size = n
    top = -1
    items = [None] * self.size
    
    
    #스택의 연산 구현하기 # 삼항연산자
    def is_empty(self):
        return True if self.top == -1 else False
    
    def is_full(self):
        return True if self.top == self.size else False
    
    def is_full(self):
        return True if self.top == self.size else False
    
    def push(self, item):
        if self.is_full():
            # 에러
            raise Exception("It is full!")
            
        self.top += 1
        self.items[self.top] = item
     
    # stack 가장 마지막의 수를 반환
    def peek(self):
        if self.is_empty():
            raise Exception("It is empty!")
        return self.items[self.top]
        
    def pop(self):
        if self.is_empty():
            raise Exceptoin("It is empty!")
        else:
            value = self.items[self.top]	
            # 가장 위에 있는 데이터르 락져와
            self.itmes[self.top] = None	# 아이템삭제
            self.top -= 1	# top위치 변경
            return value 
            
        return self.pop[self.pop]
    
   
    
```

```python
def __ str__(self):
    result = "\n----"
    for item in self.itmes:
       if item in s
            result = f"\n| + result
        else: 
                result = f'\n| {item}
        
```



```python
my_stack = Stack(size = 5)
my_stack.push(1)
my_stack.push(2)
my_stack.pop()

my_stack.push(2)
my_stack.push(3)

print(my_stack)

stack = [] # stack 생성
stack.append(1)
stack.append(2)
stack.append(3)
stack.pop()
peek = stack[-1] # peek
len(stack) == 0 # is_empty
print(stack)

# python은 스택 자료구조를 리스트에다 녹여놨다,
# 그래서 우리는 리스트 자료구조를 스택처럼 사용이 가능하다
```

* 스택
  * LIFO
  * top 에서만 삽입, 삭제가 가능하다
* 

### 6.  스택의 응용

#### 1) 괄호검사

* 괄호를 조사하는 알고리즘 개요
  * 문자열에 있는 괄호를 차례대로 조사하면서, 왼쪽 괄호(여는괄호)를 만남녀 스택에 삽입하고, 오른쪽 괄호를 만나면 스택에서 top괄호를 삭제한 후 오른쪽 괄호에 짝이 맞는지를 검사한다
  * 이 때,



#### 2) Function call

* 프로그램에서 함수 호출과 복귀에 따른 수행 순서를 처리

  * 가장 마지막에 호출된 함수가 가장 먼저 실행을 완료하고, 복귀하는 후입선출 구조이므로 후입선출 구조의 스택을 이용하여 수행순서를 관리한다. 
  * 함수 호출이 발생하면 호출한 함수 수행에 필요한 지역변수, 매개변수 및 수행 후 복귀할 주소 등의 정보를 슽개 프레임에 저장하여 시스템 스택에 삽입
  * 함수의 실행이 끝나면 시스템 스택의 top원소(스택 프레임)를 삭제(pop)하면서 프레임에 저장되어있는 복귀 주소를 확인하고 복귀
  * 함수 호출과 복귀에 따라 이 과정을 반보갛여 전체 프로그램 수행이 종료되면 시스템 스택은 공백 스택이 된다. 

* 함수 호출과 복귀에 따른 전체 프로그램의 수행 순서

  ![image-20220222094704973](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220222094704973.png)

  









## :two: 재귀호출

### 1. 팩토리얼

```python
```

### 2. 피보나치 수열

* 0, 1, 1, 2, 3, 5, 8, ....

* 재귀함수

  ```python
  def fibo(n):
      if n < 2:
          return n
      else:
          return fibo(n-1) + fibo(n-2)
  ```

* 문제점

  * 연산량이 많다 - 중복 호출이 엄청나다

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220222100441032.png" alt="image-20220222100441032" style="zoom: 67%;" />

  * 이를 해결하기 위해 Memoizatin 기술이 발전

    

## :three: Memoization & DP

### 1. 메모이제이션(Memoization)

#### 개념

* 컴퓨터 프로그램을 실행할 때 이전에 계산한 값을 메모리에 저자해서 매번 다시 계산하지 않도록 하여 전체적인 실행속도를 빠르게 하는 기술이다. 
* 동적 계획법의 핵심이 되는 기술.
* 이를 글자 그대로 해석하면 메모리에 넣기(to put in memory)라는 의미이며, 기억되어야 할 것 이라는 뜻의 라틴어 memorandum에서 파생되었다. 동사형은 memoize.

#### 예제

* 피보나치 수를 구하는 알고리즘에서 fibo(n)을 계산하자마자 저장하면, 실행시간을 세타(n)으로 줄일 수 있다.

* Memoization방법을 적용한 알고리즘

  ```python
  #memo를 위한 배열을 할당하고, 모두 0으로 초기화한다;
  #memo[0]을 0으로 memo[1]은 1로 초기화
  
  def fibo1(n):
      global memo
      if n >= 2 and len(memo) <= n:
          memo.append(fibo1(n-1) + fibo1(n-2))
      return memo[n]
  
  memo = [0, 1]
  ```

  



### 2. 동적 계획(DP: Dynamic Programming)

#### 개념

* 그리디 알고리즘과 같이 최적화 문제를 해결하는 알고리즘

* 먼저 입력 크기가 작은 부분 문제들을 모두 해결한 후에, 그 해들을 이요하여 보다 큰 크기의 부분 문제들을 해결하여, 최종적으로 원래 주어진 입력의 문제를 해결하는 알고리즘.

#### 적용

* 피보나치 수 DP 적용

  1. 문제를 부분 문제로 분할

     - fibo(n)은 fibo(n-1), fibo(n-2)의 합
     - fibo(n-1)은 fibo(n-2), fibo(n-3)의 합
     - fibo(2)는 fibo(1), fibo(0)의 합

  2. 가장 작은 부분 문제부터 해를 구한다

  3. 그 결과를 테이블에 저장하고, 테이블에 저장된 부분 문제의 해를 이용하여 상위 문제의 해를 구한다

  4. 알고리즘

     ```python
     def fibo2(n):
         f = [0, 1]
         
         for i in range(2, n+1):
             f.append(f[i-1] + f[i-2])
             
         return f[n]
     ```

* DP의 구현 방식

  * recursive 방식: fib1()

  * iterative 방식: fib2()

  * memoization을 재귀 적 구조에 사용하는 것보다, 반복적 구조로  DP를 구현한 것이 성능 면에서 효율적

  * 재귀적 구조는 내부에 시스템 호출 스택을 사용하는 오버헤드가 발생

    





## :four: 깊이우선탐색 (DFS: Depth First Search)

### 1. 개념

* 시작 정점의 한 방향으로 갈 수 있는 경로가 있는 곳까지 깊이 탐색해 가다가 더 이상 갈 곳이 없게 되면, 가장 마지막에 만났던 갈림길 간선이 있는 정점으로 되돌아와서 다른 방향의 정점으로 탐색을 계속 반복하여 결국 모든 정점을 방문하는 순회방법
* 가장 마지막에 만났던 갈림길의 정점으로 되돌아가서 다시 깊이 우선 탐색을 반복해야 하므로 후입선출 구조의 스택 사용





### 2. 기본 형태

![image-20220224163246799](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220224163246799.png)