# Algorithm Tree

## :zero: Table of Contents

1. [TOC]

   

## :one: 트리

### 1. 트리의 개념

* 비선형구조

* 원소들 간 1:n 관계를 가지는 자료구조

* 원소들 간에 계층 관계를 가지는 계층형 자료구조

* 상위 원소에서 하위 원소로 내려가면서 확장되는 트리(나무)모양의 구조

* 한 개 이상의 노드로 이루어진 유한 집합(1개만 있어도 Tree)

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316092211137.png" alt="image-20220316092211137" style="zoom:80%;" />

  * 노드 중 최상위 노드를 루트(root)라고한다
  * 나머지 노드들은 n개의 분리집합 T1, T2, ... TN으로 분리가능
  * 분리집합들은 각각 하나의 트리가 되며(재귀적 정의), 루트의 부 트리(subtree)라고 한다.



### 2. 용어

* 노드(node)

  * 트리의 원소

* 간선(edge) 

  * 노드를 연결하는 선. 부모 노드와 자식 노드를 연결

* 루트 노드(root node)

  * 트리의 시작 노드

* 형제 노드(sibling node)

  * 같은 부모 노드의 자식 노드

* 조상 노드

  * 간선을 따라 루트 노드까지 이르는 경로에 있는 모든 노드

* 서브 트리(subtree)

  * 부모 노드와 연결된 간선을 끊었을 때 생성되는 트리

    <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316093340899.png" alt="image-20220316093340899" style="zoom: 67%;" />

* 자손 노드

  * 서브 트리에 있는 하위 레벨의 노드들

* 차수(degree)

  * 노드의 차수: 노드에 연결된 자식 노드의 수
  * 트리의 차수: 트리에 있는 노드의 차수 중에서 가장 큰 값
  * 단말 노드(리프 노드): 차수가 0인 노드. 자식 노드가 없는 노드

* 높이

  * 노드의 높이: 루트에서 노드에 이르는 간선의 수. 노드의 레벨
  * 트리의 높이: 트리에 있는 노드의 높이 중에서 가장 큰 값. 최대 레벨



## :two: 이진 트리

### 1. 개념

* 모든 노드들이 2개의 서브트리를 갖는 특별한 형태의 트리

* 각 노드가 자식 노드를 최대한 2개까지만 가질 수 있는 트리

  * 왼쪽 자식 노드(left child node)
  * 오른쪽 자식 노드(right child node)

* 이진 트리의 예

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316092818111.png" alt="image-20220316092818111" style="zoom:50%;" />



### 2. 특성

* 레벨 i에서 노드의 최대 갯수는 2^i개 (레벨이 0에서 시작한다면)

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316093851029.png" alt="image-20220316093851029" style="zoom:50%;" />

* 높이가 h인 이진 트리가 가질 수 있는 노드의 최소 갯수는 (h+1)개가 되며, 최대 갯수는 ( 2^(h+1) - 1 )개



### 3. 종류

* 포화 이진 트리(Full Binary Tree)

  * 모든 레벨에 노드가 포화상태로 차 있는 이진트리
  * 높이가 h일 때, 최대의 노드 갯수의 노드를 가진 이진 트리
  * 루트를 1번으로 하여 정해진 위치에 대한 노드 번호를 가짐. 목차 '특성'에 있는 이진트리가 포화 이진트리

* 완전 이진 트리(Complete Binary Tree) 

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316094244196.png" alt="image-20220316094244196" style="zoom: 50%;" />

  * 높이가 h이고 노드 수가 n개 일 때(단, **h + 1 < n < 2^(h+1) -1**) 포화 이진 트리의 노드 번호 1번부터 n번까지 **빈 자리가 없는** 이진 트리 

* 편향 이진 트리(Skewed Binary Tree)

  * 높이 h에 대한 최소 갯수의 노드를 가지면서 한쪽 방향의 자식 노드만을 가진 이진트리

  * 트리의 장점들이 사라짐(선형 자료구조와 동일하다고 보면 됨)

    * 왼쪽 편향 이진트리

      <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316094515475.png" alt="image-20220316094515475" style="zoom:50%;" />

    * 오른쪽 편향 이진트리

      <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316094527889.png" alt="image-20220316094527889" style="zoom:50%;" />

  

### 4. 순회

* 개념 및 정의

  * 순회(traversal)란 트리의 각 노드를 중복되지 않게 전부 방문(visit)하는 것을 말한다. 그러나 트리는 비선형 구조이기 대문에 선형구조에서와 같이 선후 연결 관계를 알 수 없다.

  * 순회(traversal): 트리의 노드들을 체계적으로 방문하는 것

  * **순회를 시작한 서브트리 내에서만 순환한다! 거슬러 올라가서 돌지 않는다**

  * 3가지의 기본적인 순회방법

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220316130130627.png" alt="image-20220316130130627" style="zoom:67%;" />

    <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316094851949.png" alt="image-20220316094851949" style="zoom: 50%;" />
    
    * 전위순회(preorder traversal): VLR
    * 중위순회(inorder traversal): LVR
    * 후위순회(postorder traversal): LRV



* 전위순회(preorder traversal)

  * 수행방법

    * 현재 노드 n을 방문해서 처리 (V)
    * 현재 노드 n의 왼쪽 서브트리로 이동 (L)
    * 현재 노드 n의 오른쪽 서브트리로 이동(R)

  * 전위 순회 알고리즘(pseudo code)

    ```python
    def preorder_traverse(T):
        if T:
            visit(T)					# 가장 처음
            preorder_traverse(T.left)
            preorder_traverse(T.right)
            
    # return 없어도 자동으로 됨
    ```

  * 예시

    <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316095355974.png" alt="image-20220316095355974" style="zoom: 50%;" />

    ![image-20220316130206075](C:\Users\Gyumin\ssafy7\TodayILearned\image-20220316130206075.png)
    
    

* 중위순회(inorder traversal)

  * 수행방법
    * 현재 노드 n의 왼쪽 서브트리로 이동: L
    * 현재 노드 n을 방문하여 처리: V
    * 현재 노드 n의 오른쪽 서브트리로 이동: R
    
  * 중위 순회 알고리즘(pseudo code)

    ```python
    def inorder_traverse(T):
        if T:
            inorder_traverse(T.left)
            visit(T)						# 부모가 중간
            inorder_traverse(T.right)
    ```

  * 예시

    <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316101835505.png" alt="image-20220316101835505" style="zoom:50%;" />
    
    ![image-20220316125545988](C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316125545988.png)
    
    

* 후위순회(postorder traversal)

  * 수행방법

    * 현재 노드 n
    * 현재 노드 n
    * 현재 노드 n

  * 후위 순회 알고리즘(pseudo code)

    ```python
    def postorder_traverse(T):
        if T:
            postorder_traverse(T.left)
            postorder_traverse(T.right)
            visit(T)						# 부모가 마지막
    ```

  * 예시 

    ![image-20220316101856634](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316101856634.png)
    
    ![image-20220316130339443](C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316130339443.png)







* 연습문제

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316102319144.png" alt="image-20220316102319144" style="zoom:67%;" />

  * 전위순회: **A** B D H I E J C F K G L M
  * 중위순회: H D I J E B **A** K F C L G M
  * 후위순회: H I J D E B K L M F G C **A**



### 5. 이진트리의 표현

#### 1) 배열을 이용한 이진 트리의 표현

<img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316103438761.png" alt="image-20220316103438761" style="zoom:50%;" />

* 기본가정

  * 이진 트리에 각 노드 번호를 위와 같이 부여(완전이진트리)

  * 루트의 번호를 1로 한다

  * 레벨 n에 있는 노드에 대해 왼쪽부터 오른쪽으로 `2^n` 부터 `2^(n+1)-1` 까지 번호를 차례로 부여

  * 1~n번까지의 노드 있으면, N+1개의 원소를 가진 배열을 생성한다(인덱스 0부터 시작이라 14개 만듦)

    * (완전/포화이진트리)정점 번호를 인덱스로 사용하는 것
    * 높이가 h인 이진 트리를 위한 배열의 크기는 `2 ^ (h+1) - 1`

    <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316104028037.png" alt="image-20220316104028037" style="zoom:50%;" />

* 노드 번호의 성질

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316104424557.png" alt="image-20220316104424557" style="zoom:50%;" />

  * 노드 번호가 i인 부모노드 번호

    * ` i / 2`

  * 노드 번호가 i인 노드의 왼쪽 자식 노드 번호

    * `2 * i`

  * 노드 번호가 i인 노드의 오른쪽 자식 노드 번호

    * `2 * i + 1`

  * 레벨 n의 노드 번호 시작 번호 

    * `2ⁿ`

    

* 예시

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316104928864.png" alt="image-20220316104928864" style="zoom:50%;" />

  * 참고: 편향 이진트리의 경우, 이런 식으로 배열을 만들어 하지 않음(할수는 있는데 굳이 그렇게 안 함)



* 배열을 이용한 이진 트리의 표현의 단점
  * 편향 이진 트리의 경우, 사용하지 않는 배열 연소에 대한 메모리 공간 낭비 발생
  * 트리 중간에 새로운 노드를 삽입하거나, 기존의 노드를 삭제할 경우 배열의 크기 변경 어려워 비효율적

* 단점 보완방법
  * 연결리스트를 이용한 트리 표현



#### 2) 연결리스트를 이용한 이진 트리의 표현

* 개념

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316111848368.png" alt="image-20220316111848368" style="zoom:67%;" />

  * 이진 트리의 모든 노드는 최대 2개의 자식 노드를 가지므로, 일정한 구조의 단순 연결리스트 노드를 사용하여 구현

* 완전이진트리의 연결리스트

  <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316145342087.png" alt="image-20220316145342087" style="zoom:50%;" />

  



### 6. 수식트리

* 개념
  * 수식을 표현하는 이진트리
  * 수식 이진 트리(Expression Binary Tree)라고 부르기도 함
  * 연산자는 루트 노드이거나 가지 노드
  * 피연산자는 모두 잎 노드
* 수식 순회의 순회
  * 중위순회
    * `A / B * C * D + E`
  * 후위순회
    * `A B / C * D * E`
  * 전위순회
    * `+ * * / A  B C D E`



### :white_check_mark: [참고] 이진트리의 저장

#### 1. 부모 번호를 인덱스로 자식 번호를 저장

* 간선의 갯수(노드 갯수 - 1)로 부모자식 쌍 알 수 있음

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316105551697.png" alt="image-20220316105551697" style="zoom:50%;" />

* pseudo code

  ```python
  for i: 1 -> N
      read p, c
      if( c1[p] == 0)
      	c1[p] = c
      else:
          c2[p] = c
  ```

  <img src="C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316105928160.png" alt="image-20220316105928160" style="zoom:50%;" />

* python code

  ```python
  E = int(input())	# edge 수
  arr = list(map(int, input().split()))
  V = E + 1 			# vertex/node 수
  
  child1 = [0] * (V + 1)
  child2 = [0] * (V + 1)
  
  # 배열저장
  for i in range(E):
      p, c = arr[i*2], arr[i*2+1]	# 배열에서 인덱스0, 1 / 2, 3 / 4, 5 씩 끊어서 가져와줌
      if child1[p] == 0:	# 아직 자식이 없는 경우
          child1[p] = c
      else:				# 자식이 있는 경우
          child2[p] = c	# 자식2 배열에다 저장
          
  # 전위순회
  def preorder_traversal(v):
      if v:				# 0번 정점이 없으므로, 0번은 자식이 없는 경우를 표시 (이 문제 한정)
          print(v)		# visit(v)
          preorder_traversal(child1[v])
          preorder_traversal(child2[v])
          
  # 중위순회
  def inorder_traversal(v):
      if v:
  		inorder_traversal(child1[v])
          print(v)
          inorder_traversal(child2[v])
          
  # 후위순회
  def postorder_traveresal(v):
      if v:
          postorder_traversal(child1[v])
          postorder_traversal(child2[v])
          print(v)
          
  preorder_traversal(1)
  inorder_traversal(1)
  postorder_traversal(1)
  ```

  * 출력

    * 배열 저장

      ![image-20220316111349855](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316111349855.png)

    * 전위순회

      ![image-20220316112125653](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316112125653.png)

      * 만약 `preorder_traversal(3)` (즉, 3에서부터 순회 시작을 한다면)인 경우, `3, 4, 5`만 하고 끝

        ![image-20220316112531702](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316112531702.png)

    * 중위순회

      ![image-20220316112710423](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316112710423.png)

    * 후위순회

      ![image-20220316112930701](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316112930701.png)

      * `postorder_traversal(3)` 경우 출력

        ![image-20220316112849483](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220316112849483.png)

  * Tree 의 정점 번호 규칙

    * 포화이진트리: 루트는 1번!
    * 그 외: 부모 정점 번호 > 자식 정점 번호 일 수도 있고, 루트가 1번이 아닐 수도 있다.
    * 따라서 다루고 있는 트리가 포화이진트리인지 판별하는 것이 필요.

  

#### 2. 자식 번호를 인덱스로 부모 번호를 저장

* `2 1 2 4 4 3 4 5 `

* pseudo code

  ```python
  for i: 1 -> N
      read p, c
      par[c] = p
  ```

* python code

  ```python
  E = int(input())	# edge 수
  arr = lsit(map(int, input().split()))
  V = E + 1 			# vertex/node 수
  
  
  # 자식 번호를 인덱스로 부모 번호를 저장
  # 배열저장
  parent = [0] * (V+1)
  for i in range(E):
      p, c = arr[i * 2], arr [i * 2 + 1]
      parent[c] = p
  print(*parent)
  ```
  
  * 출력
  
    * 배열저장
  
      <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316142151305.png" alt="image-20220316142151305" style="zoom: 50%;" />



#### 3. 루트 찾기, 조상 찾기

* pseudo code

  ```python
  c = 5
  while(a[c] != 0): # 루트인지 확인
      c = a[c]
      ancestor.append(c) # 조상 목록
  root = c
  ```

* python code

  ```python
  # root 찾기    
  root = 0
  for i in range(1, V + 1):
      if parent[i] == 0:
          root = i
          break
  print(root)
  inorder_traversal(2)
  
  # 조상찾기
  # 노드 c의 조상찾기
  c = 5
  ancestor = []
  while par[c] != 0:
      ancestor.append(par[c])
      c = parent[c]			# 찾은 부모를 새로운 자식으로 할당
  print(*ancestor)
  ```
  
  * 출력
  
    * root 찾기
  
      <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316142546048.png" alt="image-20220316142546048" style="zoom:50%;" />
  
    * 조상찾기
  
      <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316144154608.png" alt="image-20220316144154608" style="zoom: 50%;" />
  
      



## :three: 이진 탐색 트리

### 1. 개념

<img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316150045394.png" alt="image-20220316150045394" style="zoom:50%;" />

* 탐색작업을 효율적으로 하기 위한 자료구조
* 모든 원소는 서로 다른 유일한 키를 가짐
* key(왼쪽 서브트리) < key(루트 노드) < key(오른쪽 서브트리)
* 왼쪽 서브트리와 오른쪽 서브트리도 이진 탐색 트리
* 중위 순회하면 오름차순으로 정렬된 값을 얻을 수 있다.



### 2. 연산

* 탐색연산

  * 루트에서 시작

  * 탐색할 키 값 x를 루트 노드의 키 값과 비교

    * `키 값 x = 루트노드의 키 값`인 경우: 원하는 원소를 찾았으므로 탐색연산 성공
    * `키 값 x < 루트노드의 키 값`인 경우: 루트노드의 **왼쪽** 서브트리에 대해 탐색연산 수행
    * `키 값 x > 루트노드의 키 값`인 경우: 루트노드의 **오른쪽** 서브트리에 대해 탐색연산 수행

  * 예시: 13 탐색

    <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316150328620.png" alt="image-20220316150328620" style="zoom:50%;" />



* 삽입 연산

  * 먼저 탐색 연산을 수행

    * 삽입할 원소와 같은 원소가 트리에 있으면 삽입할 수 없으므로, 같은 원소가 트리에 있는지 확인
    * 탐색에서 탐색 실패가 결정되는 위치가 삽입 위치가 됨

  * 탐색을 실패한 위치에 원소를 삽입

  * 예시: 5를 삽입

    <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316150440840.png" alt="image-20220316150440840" style="zoom:50%;" />

* 삭제 연산

  * 예시: 다음 트리에 대해서 13, 12, 9를 차례로 삭제해 보자

  * :question: 만약 15를 삭제한다면?

    ```python
    ```

    <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316152821958.png" alt="image-20220316152821958" style="zoom:50%;" />

    

    

### 3. 성능

* 탐색(searching), 삽입(insertion), 삭제(deletion) 시간은 트리의 높이 만큼 시간이 걸린다.
  * O(h), h : BST(Binary Search Tree)의 깊이(height)
* 평균의 경우
  * 이진 트리가 균형적으로 생성되어 있는 경우
* 최악의 경우
  * 한쪽으로 치우친 경사 이진트리의 경우
  * O(n)
  * 순차탐색과 시간복잡도기 길다.

* 검색 알고리즘의 비교
  * 배열에서의 순차 검색: O(N)
  * 정렬된 배열에서의 순차 검색: O(N)
  * 정렬된 배열에서의 이진탐색: O(logN)
    * 고정 배열 크기와 삽입, 삭제 시 추가 연산 필요
  * 이진 탐색트리에서의 평균: O(logN)
    * 최악의 경우: O(N)
    * 완전 이진 트리 또는 균형트리로 바꿀 수 있다면 최악의 경우를 없앨 수 있다.
      * 새로운 원소 삽입시 삽입 시간 줄임
      * 평균과 최악의 시간이 같다. O(logn)
    * 해쉬검색: O(1)
      * 추가 저장 공간이 필요





## :four: 힙

### 1. 개념

* 완전 이진 트리에 있는 노드 중 키값이 가장 큰 노드나 키값이 가장 작은 노드를 찾기 위해서 만든 자료구조

* 최대 힙(max heap)

  <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316153203778.png" alt="image-20220316153203778" style="zoom: 50%;" />

  * 키값이 가장 큰 노드를 찾기 위한 완전 이진 트리
  * `{부모노드의 키값 > 자식노드의 키값}`
  * 루트 노드: 키값이 가장 큰 노드

* 최소 힙(min heap)

  <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316153310165.png" alt="image-20220316153310165" style="zoom:50%;" />

  * 키 값이 가장 작은 노드를 찾기 위한 완전 이진 트리
  * `{부모노드의 키값 < 자식노드의 키값}`
  * 루트 노드: 키값이 가장 작은 노드

* 힙이 아닌 이진 트리의 예

  <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316153438515.png" alt="image-20220316153438515" style="zoom:50%;" />

  * 아닌 이유
    * 트리 1: 최소 힙 / 최대 힙 기준을 충족하지 못하고 있음 
    * 트리 2: 완전 이진 트리가 아님

### 2. 삽입

* 예시: 17삽입

  <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316153805911.png" alt="image-20220316153805911" style="zoom:50%;" />

  1. 마지막 정점 번호를 확보한다 (6번)
  2. 마지막 정점 번호를 확장시킨다 (7번)
  3. 해당 정점 번호에 데이터를 삽입한다.
  4. 최대힙/최소힙 조건 만족하는지 확인

  

* 예시: 23 삽입

  <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316153825840.png" alt="image-20220316153825840" style="zoom:50%;" />

  1. 마지막 정점 번호 확보 (6번)
  2. 마지막 정점 번호 확장 (7번)
  3. 해당 정점 번호에 데이터 삽입 (7번에 23 넣음)
  4. 최대합/최소힙 조건 만족하는지
     * `부모키값 < 자식키값` 이므로 최대힙 만족할 때 까지(더 큰 부모를 만날 때 까지) 자리 바꿔준다 

* 예시 3

  * 최대 100개의 정수가 키로 입력됨
  * 최대힙

  ```python
  
  def enq(n): # 우선순위 큐
      global last
      last += 1
      tree[last] = n		# 완전이진트리 유지
      c = last			# 새로 추가된 정점을 자식으로
      p = c//2			# 완전이진트리에서의 부모 정점 번호
      while p >= 1 and tree[p] < tree[c]:			# 자식의 키 값이 부모보다 더 크면,
          tree[p], tree[c] = tree[c], tree[p]		# 부모와 자리 바꿔줌
          c = p
          p = c // 2
          
  # # 포화 이진트리의 정점번호 1 ~ 100까지
  tree = [0] * (101)
  last = 0 	#  마지막 정점번호
  
  # 삽입되었는지 확인
  enq(3)
  enq(2)
  enq(4)
  enq(7)
  enq(5)
  enq(1)
  print(tree[1])
  # 출력: 7
  enq(9)
  print(tree[1])
  # 출력: 9
  ```

  

### 3. 삭제

* 힙에서는 루트 노드의 원소만을 삭제할 수 있다

* 루트 노드의 원소를 삭제하여 반환한다

* 힙의 종류의 따라 최대값 또는 최소값을 구할 수 있다.

* 예시

  <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316153933152.png" alt="image-20220316153933152" style="zoom:50%;" />

  1. 루트 노드안의 원소 보관
  2. 마지막 노드 반환 후 루트로 옮김
  3. 마지막 노드 인덱스 감소
  4. 최대힙이 되도록 자리 바꾸기
  5. 자리 확정(부모보다 더 큰 자식이 없을 때 까지)

  ```python
  def deq():
      global last
      tmp = tree[1] 			# root의 키 값 보관
      tree[1] = tree[last] 	# 마지막 노드의 키를 루트에 복사
      last -= 1				# 마지막 노드 인덱스 감소
      
      #부모>자식 규칙 유지(최대힙 조건)
      p = 1
      c = p * 2			# 왼쪽자식노드 번호
      while c <= last:	# 왼쪽자식이 있으면
          if c + 1 <= last and tree[c] < tree[c+1]:	# 오른쪽 자식노드가 있고, 더 크면
              c += 1				# 오른쪽 자식 선택
          if tree[p] < tree[c]:	# 자식의 키 값이 더 크면 교환
              tree[p], tree[c] = tree[c], tree[p]
          	p = c
              c = p * 2
          else:
              break
      return tmp
  
  print(tree[1])
  while last > 0:
      print(deq())
      print(tree[1])
  ```

  * 출력

    ![image-20220316161852247](C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316161852247.png)



### 4. 힙을 이용한 우선순위 큐

* 들어올 때는 뒤로 들어오고, 나갈 때는 우선순위에 따라 나감

<img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316155034391.png" alt="image-20220316155034391" style="zoom:50%;" />





## :five: 연습

### 1. 완전이진트리에서의 순회

```python
def pre_order(v):
    global last
    if v <= last: # 마지막 정점번호 이내
        print(v)  # visit(v)
        pre_order(v*2) # 왼쪽 자식 정점 방문
        pre_order(v*2+1) # 오른쪽 자식 정점 방문
```



