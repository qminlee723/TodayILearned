# Algorithm 모의A형대비

[TOC]



## :zero: 기본

### 1. BFS vs DFS

* DFS
  *  N이 1~30 정도 되는 수치
* BFS
  * 2차원배열, N이 50~200 수준
  * 최소를 구하라



### 2. 간단 구현

* 리스트에 55, 44, 33, 22, 11, 0 을 for문 이용하여 차례로 집어넣기

  ```python
  lst = []
  for i in range(55, -1, -11):
      lst.append(i)
  print(lst)
  ```

* 제시된 lst 안에 있는 알파벳 중 중복을 제거하고 알파벳 순서대로 넣기

  ```python
  lst = ['A', 'B', 'T', 'A', 'A', 'A', 'B', 'A']
  print(sorted(list(set(lst))))
  ```

* :star: 재귀함수

  ```python
  lst = [10, 9, 8, 7, 6, 6, 7, 8, 9, 10]
  def call(v):
      if v == 5:
          return
      print(v)
      call(v-1)
      print(v)
  call(10)
  ```

  



## :one: BFS

### 1. Flood Fill  

* 2차원 배열에서 쭉 퍼지는 모양의 알고리즘

  ![image-20220405195307272](Algorithm_A%ED%98%95%EB%8C%80%EB%B9%84.assets/image-20220405195307272.png)

* BFS의 80%는 Flood Fill, 20% 는 그래프 탐색



### 2. BFS 기본

* 구현

  ![image-20220405195605820](Algorithm_A%ED%98%95%EB%8C%80%EB%B9%84.assets/image-20220405195605820.png)

  ![image-20220405195904965](C:/Users/Gyumin/AppData/Roaming/Typora/typora-user-images/image-20220405195904965.png)

* 코드

  ```python
  def BFS(v):
      Q = []
      Q.append(v)
      
      while Q:
          w = Q.pop(0)
          
          for r in range(4):
              ni = w[0] + di[r]
              nj = w[1] + dj[r]
          
  
  di = [-1, 1, 0, 0]
  dj = [0, 0, -1, 1]
  arr = [[0]*4 for _ in range(4)]
  v = arr(1, 1)
  ```

  



### 3. BFS 응용

#### 1) 응용 1

* 구현

![image-20220405200130451](Algorithm_A%ED%98%95%EB%8C%80%EB%B9%84.assets/image-20220405200130451.png)

* 코드

  ```python
  ```

  

#### 2) 응용 2

* 구현

  * 섬의 크기를 구하라

  ![image-20220405200217739](Algorithm_A%ED%98%95%EB%8C%80%EB%B9%84.assets/image-20220405200217739.png)

* 코드

  ```python
  ```



### 3) 응용 3

* 구현

  * 바다에 섬이 있다. 섬이 몇개인가?

    ![image-20220405200359142](Algorithm_A%ED%98%95%EB%8C%80%EB%B9%84.assets/image-20220405200359142.png)

* 코드

  ```python
  ```



#### 4) 응용 4

* 구현

  * A에서 B까지 최소 거리 출력

  ![image-20220405200812882](Algorithm_A%ED%98%95%EB%8C%80%EB%B9%84.assets/image-20220405200812882.png)

* 코드

  ```python
  ```

  

#### 5) 응용 5

* 구현

  * A -> B -> C 로 가는 최단거리 구하기

  ![image-20220405200906565](Algorithm_A%ED%98%95%EB%8C%80%EB%B9%84.assets/image-20220405200906565.png)

* 설계

  * 미로찾기 두 번하기

* 코드

  ```python
  ```



#### 6) 응용 6

* 구현

* 설계

* 코드

  ``` python
  ```

  

#### 7) 응용 7

* 구현

* 설계

* 코드

  ``` python
  
  ```



## :two: 문제풀이

### 1.  SWEA 14195 미생물관찰 

* 출력

  * A 개체의 수 
  * B 개체의 수

  * 가장 큰 개체

* 코드

  ```python
  ```

  