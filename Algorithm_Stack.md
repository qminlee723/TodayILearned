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



## :two: 재귀호출

## :three: Memoization & DP

## :four: DFS

