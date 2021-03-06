# Algorithm

# :ballot_box_with_check: OVERVIEW

1. 알고리즘
2. 배열
3. 버블 정렬 (Bubble Sort)
4. 카운팅 정렬 (Counting sort)
5. 완전검색
6. 그리디(Greedy Algorithm)



:heavy_plus_sign: 이산수학

파이썬에서는 100만개 정도의 배열 가짐(실제로 저장할 수 있는 크기)





알고리즘  주간 

* 코드 효율성 검토가 가능한지를 보는 것

* 그 능력을 검증하는 것이 알고리즘

* 

  월수는 라이브 보고 연습문제 1문제

  화요일 목요일은 4문제씩 주고 조짜서 문제

  금요일도 4문제

  매일매일 hw



## :zero: 알고리즘

### 1. 알고리즘이란?

* 개념

  * 유한한 단계를 통해 문제를 해결하기 위한 절차나 방법
  * 컴퓨터가 어떤 일을 수행하기 위한 단계적 방법
  * 어떠한 문제를 해결하기 위한 절차

* 알고리즘 표현법

  * 의사코드(Pseudocode)

    <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220210090807111.png" alt="image-20220210090807111" style="zoom:50%;" />

  * 순서도

### 2. 알고리즘의 성능은 무엇으로 측정하는가? (5:정작메단최)

* 무엇이 좋은 알고리즘인가?

  * 정확성: 얼마나 정확하게 동작하는가
  * 작업량: 적은 연산으로 원하는 결과를 얻어내는가
  * 메모리사용량: 적은 메모리를 사용하는가
  * 단순성: 얼마나 단순한가
  * 최적성: 개선불가능한 최적

  

* 시간복잡도(Time Complexity)

  * 실제 걸리는 시간 측정

    * (가장 빠름) O(logN) > O(N) > O(NlogN) > O(N^2) > O(N^3) > O(2^N) (가장 느림)
      * O(n^2): 웬만큼 커도 돌아가겠다(효율적이진 않음)
      * O(n^3) : 좀 느리겠네
      * O(2^n) : 입력이 매우 작아야 함.. 코딩 하지 말고 다른 길을 찾아 떠나라
      * O(n!): 다른 길을 찾아 떠나라!

  * 실행되는 명령문의 개수(연산의 횟수) 계산

    * 계수(coefficient)은 생략하고 표시

  * 최악의 경우를 상정하고 계산

  * 시간 효율성 vs 공간 효율성 

    * 시간 효율성 > 공간 효율성(지금은 메모리 가격이 쌈)

    

* 표기법

  * 빅-오 표기법(Big-Oh Notation)

    <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220210091321762.png" alt="image-20220210091321762" style="zoom:50%;" />

  * 시간 복잡도 함수 중에서 가장 큰 영향력을 주는 n에 대한 항만을 표시

  * 계수(coefficient)는 생략하여 표시

  * 예시

    <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220210091420299.png" alt="image-20220210091420299" style="zoom:50%;" />

    * n개의 데이터를 입력 받아 저장한 후 각 데이터에 1 씩 증가시킨 후 각 데이터를 화면에 출력하는 알고리즘의 시간복잡도는 어떻게 될까?
      * O(n)
    * 가장 큰 차수만 따서 표현
      * ex) O(n + n^2) == O(n^2)

### 3. 다양한 시간 복잡도(Time Complexity)의 비교

* 요소 수가 증가함에 따라 각기 다른 시간복잡도의 알고리즘은 아래와 같은 연산 수를 보임

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220210092035134.png" alt="image-20220210092035134" style="zoom:50%;" />



## :one: :star: 배열

### 1. 개념

* 일정한 **자료형**의 **변수**들을 **하나의 이름**으로 **열거**하여 사용하는 자료구조
* 파이썬에서는 리스트



### 2. 필요성

* 프로그램 내에서 여러 개의 변수가 필요할 때, 일일이 다른 변수명을 이용하는 것은 비효율적
* 배열 사용시 하나의 선언을 통해 둘 이상의 변수를 선언하는 효과 가짐
* 다수의 변수로는 하기 힘든 작업을 배열을 활용해 쉽게 할 수 있다



### 3. 1차원 배열

* 1차원 배열의 선언

  * 별도의 선언 방법이 없으면, 변수에 처음 값을 할당할 때 생성

  * 이름: 프로그램에서 사용할 배열의 이름

    ``Arr = list()``, `Arr=[]`, `Arr=[1,2,3]`, `Arr=[]*10`

    * 크기를 정해놓은 배열을 사용하는게 속도가 빠르다

* 1차원 배열의 접근

  * Arr[0]=10;
    * 배열 Arr의 0번 원소에 10을 저장
  * Arr[idx]=20;
    * 배열 ARr의 idx번 원소에 20을 저장

* :white_check_mark: 예제: Gravity

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220220235301631.png" alt="image-20220220235301631" style="zoom:67%;" />

  ![image-20220221000058697](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220221000058697.png)

  

### 4. 정렬

* 2개 이상의 자료를 특정 기준에 의해 작은 값부터 큰 값(오름차순:ascending), 혹은 그 반대의 순서대로(내림차순:descending) 재배열하는것
* 키
  * 자료를 정렬하는 기준이 되는 특정 값
* 종류
  * 버블(Bubble)
  * 카운팅(Counting)
  * 선택(Selection)
  * 퀵(Quick)
  * 삽입(Insertion)
  * 병합(Merge)





## :two: 버블 정렬(Bubble Sort)

### 1. :star: 개념

* 인접한 두 개의 원소를 비교하며 자리를 계속 교환하는 방식
* 선택 정렬과 헷갈리지 말자(비교해서 면접질문 많이 나옴..?)

### 2. 과정

* 첫 번째 원소부터 인접한 원소끼리 계속 자리를 교환하면서 맨 마지막 자리까지 이동한다

* 한 단계가 끝나면 가장 큰 원소가 마지막 자리로 정렬된다

* 시간복잡도

  * O(n^2)

* 예제

  * 입력

    ```python
    N = int(input())
    arr = list(map(int, input().split())
    ```

  * 첫 번째 패스: 가장 큰 수를 맨 뒤로

    ```python
    # 나에게 주어진 범위 파악
    # 비교기준위치: j = 0~3 (N-1)개 ==> 비교원소의 왼쪽 인덱스)
    
    for j:0 -> 3
        if arr[j] > arr[j+1]:
            arr[j] <-> arr[j+1]
    ```

  * 두 번째 패스:

    ```python
    # 2번째 구간에 대해서 최대값을 찾는다 
    # 구간이 1만큼 줄어듦 == (n-2)
    # 구간의 끝이 안쪽으로 들어오는 것. 구간의 끝을 i라고 하자
    
    #구간 결정:
    	for i: N - 1 -> 1 
            # 0까지 가도 괜찮지만, 보통 두 개 남기는 최소한의 구간의 길이는 1(인덱스)
            
    ```

  * 세 번째 패스:

    ```python
    # 3번째 구간에 대해서 최대값을 찾는다
    # 범위가 1만큼 줄어듦 == (n-1)
    
    #PseudoCode
    for j: 0 -> i-1
        if arr[j] > arr[j+1]
        	arr[j] <-> arr[j+1]
            
    #Python
    def BubbleSort(a, N) : 			# 정렬할 List, N 원소 수
        for i in range(N-1, 0, -1): # 정렬 구간의 끝 
            for j in range(i):		# 비교할 왼쪽 원소
                if a[j] > a[j+1]:
                    a[j], a[j+1] = a[j+1], a[j]
        return
                    
                    
    T = int(input())
    for tc in range(1, T+1):
        N = int(input())
        arr = list(map(int, input().split()))
        bubble_sort(arr, N)
        
        # print(f'#{tc}, end='')
        # for x in arr:
        #      print(x, end='')
        # print()
        # print(*arr)
    ```

    

  

### 3. 알고리즘





## :three: 카운팅 정렬(Counting Sort)

### 1. 개념

* 항목들의 순서를 결정하기 위해 집합에 각 항목이 몇 개씩 있는지 세는 작업을 하여, 선형 시간에 정렬하는 효율적인 알고리즘
* 제한 사항
  * 정수나 정수로 표현할 수 있는 자료에 대해서만 적용 가능: **각 항목의 발생 횟수**를 기록하기 위해, 정수 항목으로 인덱스 되는 카운트들의 배열을 사용하기 때문 (누적 합)
  * 맨 뒤에서부터 정렬 
  * 카운트들을 위한 충분한 공간을 할당하려면 집합 내의 가장 큰 정수를 알아야 한다.
* 시간 복잡도
  * O(n+k): n은 리스트 길이, k는 정수의 최대값
  * 차수 낮아져서 좀 빠를 것을 알 수 있음

### 2. 과정

* 별도의 저장공간을 만들어서 정렬하는 것 

  * 숫자의 범위
  * 숫자의 갯수


* 1단계

  ![image-20220221053035673](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220221053035673.png)

  ![image-20220221053053254](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220221053053254.png)

  ![image-20220221053108102](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220221053108102.png)

  ![image-20220221053120933](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220221053120933.png)

  .

  .

  .

  ![image-20220221053208525](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220221053208525.png)



* count = [0]*(N+1)

  * 0을 찾으면 그 카운트를 하나씩 올려줘(기록해줘)

    ```python
    A[0, 4, 1, 3, 1, 2, 4, 1]
    
    counts=[0]*(N+1)			#빈 count를 만들어줌
    for j:0 -> N-1
        counts[A[i]] += 1
    ```

* 누적된 갯수를 찾을 것

  *  

    ```python
    for j -> N-1 -> 0
    	count[data[i]] -= 1
        TEMP[counts[datap[i]]] = DATA[i]
    ```

    

* 

1. Data에서 각 항목들의 발생 횟수를 세고, 정수 항목들로 직접 인덱스 되는 카운트 배열 counts에 저장한다.

2. 정렬된 집합에서 각 항목의 앞에 위치할 항목의 개수를 반영하기 위해 counts의 원소를 조정한다

3. 

4. counts[1]을 감소시키고 Temp에 1을 삽입

   ```pyhon
   for j -> N-1 -> 0
   	count[data[i]] -= 1
       TEMP[counts[datap[i]]] = DATA[i]
   ```

   

5. counts[4]를 감소시키고 temp에 4를 삽입

   ```python
   for j -> N-1 -> 0
   	count[data[i]] -= 1
       TEMP[counts[datap[i]]] = DATA[i]
   ```

   

6. counts[2]를 감소시키고 temp에 2를 삽입

   ```python
   for j -> N-1 -> 0
   	count[data[j]] -= 1
       TEMP[counts[datap[j]]] = DATA[j]
   ```

   

7. counts[1]을 감소시키고 temp에 1을 삽입

8. counts[3]을 감소시키고 temp에 3을 삽입

9. counts[1]을 감소시키고 temp에 1을 삽입

10. counts[4]을 감소시키고 temp에 4을 삽입

11. counts[0]을 감소시키고 temp에 0을 삽입

### 3. 알고리즘

* Pseudo

  ```
  

* Python

  ```python
  def Counting_Sort(A, B, k)
  # A [] -- 입력 배열(1 to k) ==== DATA
  # B [] -- 정렬된 배열 ===== TEMP
  # C [] -- 카운트 배열 ===== COUNTS
  
  for i in range (0, len(A)):
      C[A[i]] += 1
      
  for i in range (1, len(C)):
      C[i] += C[i-1]
      
  for i in range (len(B)-1, -1, -1):
      C[A[i]] -= 1
      B[C[A[i]]] = A[i]
  ```

  

### 4. 



## :four: 완전 검색(Exaustive Search)

### 0. Baby-gin Game 

* 0~9 사이의 숫자 카드에서 임의의 카드 6장을 뽑았을 때, 3장의 카드가 연속적인 번호를 갖는 경우는 run이라고 하고, 3장의 카드가 동일한 번호를 갖는 경우를 triplet이라고 한다.

* 그리고 6장의 카드가 run과 triplet으로만 구성된 경우 baby-gin

* 6자리의 숫자를 입력 받아 baby-gin 여부를 판단하는 프로그램을 작성하라

  

  ![image-20220209140340274](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220209140340274.png)



### 1.개념

* 문제의 해법으로 생각할 수 있는 **모든 경우의 수**를 나열해보고 확인하는 기법이다.
* **Brute-force** 혹은 generate-and-test 기법이라고도 불리운다.
* 모든 경우의 수를 테스트한 후, 최종 해법을 도출한다
* 일반적으로 경우의 수가 상대적으로 작을 때 유용( 일반적으로 틀린다 )
* 수행 속도는 느리지만, 해답은 웬만큼 찾아낸다
* 자격검정평가 등에서 문제를 풀 때, 먼저 완전 검색으로 접근해서 해답을 도출한 후에 성능 개선을 위해 다른 알고리즘을 사용하고 해답을 확인하는 것이 바람직하다. 



### 2. 완전 검색을 활용한 Baby-gin 접근

* 고려할 수 있는 모든 경우의 수 생성하기

* 해답 테스트하기

  

### 3. 순열(permutation)

* 서로 다른 것들 중 몇 개를 뽑아서 한 줄로 나열하는 것

  * nPr: 서로 다른 n개 중 r개를 택하는 순열은 아래와 같이 표현

    <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220209140927272.png" alt="image-20220209140927272" style="zoom: 33%;" />

    ```
    nPr = n!/(n-r)!
    ```

  * 순열의 경우의 수

  * 대략 계산량을 생각해보고 싶을 때 - 너무 많아지면 방식에 대해서 다시 생각해볼 수 있음

* 예시: {1, 2, 3}을 포함하는 모든 순열을 생성하는 함수

  동일한 숫자가 포함되지 않았을 때, 각 자리 수 별로 loop을 이용해 아래와 같이 구현 가능

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220209141135135.png" alt="image-20220209141135135" style="zoom:50%;" />

  * i1과 겹치는지 확인하고, 다르면 i2를 결정하자
  * i1과 i2와 겹치는지 확인한 후에 i3를 결정하자
  * 사람 3명이 있는데, 사람(1, 2, 3)이 물건(A, B, C)을 하나씩 잡으려고한다. 이렇게 물건을 골고루 배정해야하는 상황을 생각

  

  



## :five: 그리디(Greedy Algorithm)

### 1. 개념

* 최적해를 구하는데 사용되는 근시안적인 방법
  * 가장 적은 비용, 가장 적은 횟수
* 여러 경우 중 하나를 결정해야 할 때마다 **그 순간에 최적**이라고 생각되는 것을 선택해 나가는 방식으로 진행하여 최종적인 해답에 도달 ( 다 해보지 말고! )
* 각 선택의 시점에서 이루어지는 결정은 지역적으로는 최적이지만, 그 선택들을 계속 수집하여 최종적인 해답을 만들었다고 하여, 그것이 최적이라는 보장은 없다.
* 일반적으로, 머릿속에 떠오르는 생각을 검증 없이 바로 구현하면 Greedy 접근



### 2. 과정

1. 해 선택

   - 현재 상태에서 부분 문제의 최적 해를 구한 뒤, 이를 부분해집합(Solution Set)에 추가

2. 실행 가능성 검사

   - 새로운 부분해 집합이 실행 가능한지를 확인한다.
     - 즉, 제약 조건을 위반하지 않는지

3. 해 검사

   - 새로운 부분해 집합이 문제의 해가 되는지 확인
   - 아직 전체 문제의 해가 완성되지 않았다면, 1)의 해 선택부터 다시 시작한다.

   

### 3. 예시

* **거스름돈 줄이기**: 손님에게 거스름돈으로 주는 지폐와 동전의 개수를 최소한으로 줄일 수 있을까?

  1. 해 선택: 단위가 큰 동전으로만 거스름돈을 만들어 추가해본다

  2. 실행 가능성 검사: 거스름돈이 손님에게 내드려야 할 액수를 초과하는지 확인

     2-1. 초과한다면 마지막에 추가한 동전을 거스름돈에서 뺀다

     2-2. 1로 다시 돌아간다

  3. 해 검사: 거스름돈이 손님에게 내드려야 하는 액수와 일치한다.

     3-1. 거스름돈을 확인해서 액수에 모자라면, 다시 1로 돌아간다.

     

* **Babygin**

  1. 6개의 숫자는 6자리의 정수 값으로 입력된다.

     * counts 같은 경우 10개 (0~9)

     ```python
     for i: 0 -> 5
         counts[arr[i]] += 1
     ```

  2. count 배열의 각 원소를 체크하여 run과 triplet 및 baby-gin 여부를 판단한다.

     ```python
     ##PSEUDOCODE
     # run 조사 후 run 데이터 완전 삭제
     for i: 0 -> 9
         if counts[i] [i+1] [i+2]:
     
     # triplet 조사 후 triplet 데이터 완전 삭제
     for i: 0 -> 9
         counts[i] >= 3
     ```

     연속되는 세 숫자가 1보다 크거나 같다?

     - arr[i],[i+1],[i+2]

  3. babygin의 구현

     ```python
     num = 456789		# baby gin 확인할 6자리 수
     counts = [0] * 12 	# 6자리 수로부터 각 자리의 수를 추출하여 개수를 누적할 리스트
     					
         
     ### 왜 12개짜리 리스트를 만드는걸까요?
     # 인덱스를 run과 triplet을 검사할 때 같은 인덱스에 공유하려면.. 하나가지고 할 수 있으니까...????/???????
     # 아 run인 경우 7에서 그만드고, triplet인 ㅕㄱㅇ우 9에서 그만두니까 인덱스를 통일시키지 않으면 if문으로 따로 지정을 해줘야되니까 번거로움이 있다
     
     for i in range(6):
         c[num % 10] += 1	# 맨 오른쪽에 있는 애를 먼저 떼 낸다
         num //= 10
         
     # 자리수를 모를 때 자리수를 자르는 방법 ( 오른쪽부터 떼서 넣어주는 것 )
     while num > 0:
         c[num % 10] += 1	
         num //= 10
      
     ```

     ```python
     i = 0
     tri = run = 0
     while i < 10 :
         if c[i] >= 3:
             c[i] -= 3		# triplet 조사 후 데이터 삭제
             tri += 1
             continue
             
         # triplet검사와 run검사는 개별적인 검사이므로, if-if 구조를 가진다
         # (if-else, if-elif 아님)    
         if c[i] >= 1 and c[i+1] >= and c[i+2] >= 1:
             c[i] -= 1
             c[i+1] -= 1		# run 조사 후 데이터 삭제
             c[i+2] -= 1
             run += 1
             continue
         i += 1
         
     if run + tri == 2: print("Baby Gin")
     else: print("Lose")
     ```



### 4. 자주 실수하는 오답

* 입력받은 숫자를 정렬한 후, 앞뒤 3자리씩 끊어서 run 및 triplet을 확인하는 방법

* 해답을 찾아내지 못하는 경우도 있음

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220209152717044.png" alt="image-20220209152717044" style="zoom:50%;" />

  



```python
# 대상: 모든 원소
# n개의 자연수, 10억 이하
# Test Case: 1

arr = [2, 7, 3, 5, 4, 7]

maxV = arr[0]	# 가장 큰 값으로 가정
for i: 1 -> N-1
    if maxV < arr[i]
    	maxV = arr[i]
       
```

```python
arr = [2, 7, 3, 5, 4, 7]

maxV = 0
for i: 0 -> N-1
    if maxV < arr[i]
    	maxV = arr[i]
    
    
    # 0으로 놔도 별 문제가 없는 이유, 10억 이하의 자연수
    # if 절대값 10억 이하인 N개의 정수인 경우 0을 넣으면 안된다
    # float('-inf') 넣으면 시간 초과 
```





```python
# 최대값의 위치는?
arr = [2, 7, 3, 5, 4, 7]
maxIdx=0
for i: I -> N-1
    if arr[maxIdx] < arr[i]
    	maxIdx <- i 
        
print(maxInx[i])
```



```python
# 최대값이 여러개 일 경우?
# 문제에서 마지막 애나, 첫번째 애나 고를 애를 정해줄 것임

if arr[maxIdx] <= arr[i]	#같은 값이면 더 나중에 나온 애를 고르자

```

