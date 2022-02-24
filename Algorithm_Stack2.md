# Algorithm Stack(Calculator/Backtracking)



## :zero: OVERVIEW

1. 계산기
2. 백트래킹
3. 

## :one: 계산기(Calculator)

* 문자열로 된 계산식이 주어질 때, 스택을 이용하여 이 계산식의 값을 계산할 수 있다.

* 문자열 수식 계산의 일반적 방법

  * step1. 중위 표기법의 수식을 후위 표기법으로 변경한다(스택 이용)
  * step2. 후위 표기법의 수식을 스택을 이용하여 계산한다.
    * 중위 표기법(infix notation)
      * 연산자를 피연산자의 가운데 표기하는 방법(A+B)
    * 후위 표기법(postfix notation)
      * 연산자를 피연산자 뒤에 표기하는 방법(AB+)

* **step1.** 중위표기식의 후위표기식 변환 방법1

  * 수식의 각 연산자에 대해 우선순위에 따라 괄호를 사용하여 다시 표현

  * 각 연산자를 그에 대응하는 오른쪽괄호의 뒤로 이동

  * 괄호를 제거한다

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220223094116791.png" alt="image-20220223094116791" style="zoom:50%;" />

* 증위 표기법에서 후위 표기법으로 변환 알고리즘(스택 이용)2

  * 입력 받은 중위 표기식에서 토큰을 읽는다
  * 토큰이 피연산자이면 토큰을 출력한다
  * 토큰이 연산자(괄호포함)일 때, 이 토큰이 스택의 top에 저장되어 있는 연산자보다 우선순위가 높으면 스택에 push하고, 그렇지 않다면 스택 top의 연산자의 우선순위가 토큰의 우선순위보다 작을 때까지 스택에서 pop한 후 토큰의 연산자를 push한다. 만약 top에 연산자가없으면 push 한다
  * 토큰이 오른쪽 괄호 ')'이면 스택 top에 왼쪽 괄호 '('가 올 때까지 스택에 pop 연산을 수행하고, pop한 연산자를 출력한다. 왼쪽 괄호를 만나면 pop만 하고 출력하지는 않는다.
  * 중위 표기식에 더 읽을 것이 없다면 중지하고, 더 읽을 것이 있다면 1부터 다시 반복한다.
  * 스택에 남아 있는 연산자를 모두 pop하여 출력한다.
    * 스택 밖의 왼쪽 괄호는 우선 순위가 가장 높으며, 스택 안의 왼쪽 괄호는 우선 순위가 가장 낮다.

* step2. 후위 표기법의 수식을 스택을 이용하여 계산

  * 피연산자를 만나면 스택에 push
  * 연산자를 만남녀 필요한 만큼의 피연산자를 스택에서 pop하여 연산하고, 연산 결과를 다시 스택에 push
  * 수식이 끝나면, 마지막으로 스택을 pop하여 출력



![image-20220224091523144](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220224091523144.png)

![image-20220224092143761](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220224092143761.png)





## :two: 백트래킹(Backtracking)

### 1. 개념

* 해를 찾는 도중에 '막히면'(즉, 해가 아니면) 되돌아가서 다시 해를 찾아 가는 기법
* 백트래킹 기법은 최적화(optimization) 문제와 결정(decision)문제를 해결할 수 있다.
* 결정 문제: 문제의 조건을 만족하는 해가 존재하는지 여부를 'yes' 또는 'no'가 답하는 문제
  * 미로 찾기
  * n-Queen 문제
  * Map coloring
  * 부분 집합의 합 (Subset Sum)문제 등
* DFS를 하면 모든 경우의 수를 찾게 된다
* 이런 경우, 어떤 경우가 있으면 그만하라고 ..



### 2. 미로 찾기

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220223171246995.png" alt="image-20220223171246995" style="zoom:67%;" />



```python
bit
```

* \



## :six: 부분집합 구하기

### 1. 개념

* 어떤 집합의 공집합과 자기자신을 포함한 모든 부분잡합을 powerset이라고 하며, 구하고자 하는 어떤 집합의 원소 갯수가 n일 경우, 부분집합의 갯수는 2^n 개 이다.



### 2. 백트래킹 기법으로 powerset 구하기

* 일반적인 백트래킹 접근 방법 사용
* n개의 원소가 들어있는 집합의 2^n 개의 부분집합을 만들 때는, true 또는 false값을 가지는 항목들로 구성된 n개의 배열을 만드는 방법을 이용
* 여기서 배열의 i번째 항목은 i번쨰 원소가 부분집합의 값인지 아닌지를 나타내는 값



```python
def backtrack(a, k, input):
    global MAXCANDIDATES
    c = [0] * MAXCANDIDATES
    
    if k == input :
        process_solution(a, k) # 답이면 원하는 작업을 한다.
    else:
        k += 1
        ncandidates = construct_candidates(a, k, input, c)
        for i in range(ncandidates):
            a[k] = c[i]
            backtrack(a, k, input)
            
def construct_candidates(a, k, input, c):
    c[0] = True
    c[1] = False
    return 2

MAXCANDIDATES = 2
NMAX = 4
a = [0] * NMAX
backgrack(a, 0, 3)
```







### 3. 각 원소가 부분집합에 포함되었는지를 loop이용하여 확인하고 부분집합을 생성하는 방법

```python
bit [0, 0, 0, 0]
for i in range(2):
    bit[0] = i						# 0번째 원소
    for j in range(2)	
    	bit[1] = j					# 1번째 원소
        for k in range(2):
            bit[2] = k				# 2번째 원소
            for l in range(2):
                bit[3] = 1			# 3번째 원소
                print(bit)			# 생성된 부분집합 출력
```





### 4. :white_check_mark: 예시: {1, 2, 3}을 포함하는 모든 순열을 생성하는 함수

* 동일한 숫자가 포함되지 않았을 때, 각 자리 수 별로 loop을 이용해 아래와 같이 구현할 수 있다.

  ```python
  def f(i, N):	# i 는 부분집합에 포함될지 결정할 원소의 인덱스, N 전체 원소갯수
      if i == N:  # 1개의 부분집합 완성
          return
      else:
          bit[i] = 1
          f(i+1, N)
          bit[i] = 0
      
  a = [1, 2, 3]
  bit = [0, 0, 0]
  f(0, 3)
  
  
  for i1 in range(1, 4):
      for i2 in range(1, 4):
          if i2 != i1:
              for i3 in range(1, 4):
                  if i3 != i1 and i3 != i2:
                      print(i1, i2, i3)
  ```



### 5. 백트래킹을 이용하여 순열 구하기

```python
def backtrack(a, k, input):
    global MAXCANDIDATES
    c = [0] * MAXCANDIDATES
    
    if k == input:
        for i in range(1, k+1):
            print(a[i], end="")
        print()
    else:
        k += 1
        ncandidates = construct_candidates(a, k, input, c)
        for i in range(ncandidates):
            a[k] = c[i]
            backtrack(a, k, input)
            
def construct_candidates(a, k, input, c):
    in_perm = [False] * NMAX
    
    for i in range(1, k):
        in_perm[a[i]] = True
        
    ncandidates = 0
    for i in range(1, input+1):
        if in_perm[i] == False:
            c[ncandidates] = i
            ncandidates += 1
    return ncandidates
```



![](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220223164729549.png)



vertex의 갯수가 1000개가 넘어가면 인접리스트를 쓰는 것이 좋다



![image-20220223211135890](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220223211135890.png)

