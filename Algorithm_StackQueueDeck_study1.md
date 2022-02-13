# Algorithm Stack, Que, Deck



## :zero: Overview

### 1. Stack, Que, Deck이 필요한 이유

- 프로그래밍에서는 그래프, 트리 등의 **자료구조** 안에서 **탐색** 하는 문제를 자주 다룸
- 대표적인 탐색 알고리즘으로 DFS, BFS가 있음
- DFS, BFS를 이해하려면 스택과 큐에 대한 이해가 전제되어야 함

### 2. 자료구조

* 데이터를 표현하고 관리하고 처리하기 위한 구조
* 삽입(push), 삭제(pop) 주로 이 두 함수로 구성됨
* overflow, underflow...는 나중에 알아보자



## :one: 스택 Stack

### 1. 개념

* Stacking - 즉, 박스 쌓기
  * 박스는 아래에서부터 위로 차곡차곡 쌓고, 들어낼 때는 마지막에 올린 것부터 내린다.
* 즉, 선입 후출 (First In Last Out)
* append 시 제일 뒤에(오른쪽) 추가되고, pop 시에도 제일 뒤의 것(오른쪽)이 사라짐 

### 2. 예시





## :two: 큐 Queue

### 1. 개념

* Queuing - 즉, 대기줄

  * 나중에 온 사람일수록 나중에 들어가므로 '공정한' 자료구조

* 즉, 선입 선출(First In First Out)

* append시 앞으로(왼쪽) 추가되고, pop 시에는 뒤의 것(오른쪽)이 사라짐

  

### 2. 예시

* Append & Pop
  * `append, appendleft, pop, popleft`를 사용할 수 있다 
  * `append`, `pop`은 무조건 오른쪽, 왼쪽에 추가 혹은 삭제 원한다면 `appendleft`, `popleft`

* Insert

  * `insert(index, element)`의 경우, 덱 중간에 요소 삽입이 가능하다 

    ```python
    d = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    
    d.insert(5, 10)
    prnit(d) #[0, 1, 2, 3, 10, 4, 5, 6, 7, 8, 9]
    # 5번째 인덱스에 10이 들어가는 것을 알 수 있다
    ```

* Extend

  * `extend`, `extendleft` 를 사용해서 양옆에 iterable한 객체를 통째로 append 시킬 수도 있다

    ```python
    d = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    
    d.extend([a, a, a])
    print(d) #[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, a, a, a]
    
    d.extendleft([b, b, b])
    print(d) #[b, b, b, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, a, a, a]
    ```



## :three: 덱 Deque

### 1. 개념

* Double Ended Queue의 약자

* Stack과 Queue 연산을 모두 지원하는 자료구조

* 양 끝에서 모두 삽입과 삭제가 가능한 Queue

  * 속도가 리스트 이용시보다 효율적이고, queue 라이브러리 이용하는것보다 간단

    ```python
    from collections import deque
    ```

* 함수는 queue 이용할때와 동일!



### 2. 예



