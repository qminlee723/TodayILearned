# Algorithm Queue

## :zero: OVERVIEW



## :one: Queue

### 1. 개념

* 큐의 뒤에서는 삽입만, 큐의 앞에서는 삭제만
* FIFO: First In First Out
* 

### 2. 큐의 주요 연산

* 주요 연산

![image-20220225094705650](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220225094705650.png)

* **isFull()** and **isEmpty()**

  ![image-20220225125000056](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220225125000056.png)



### 3. 큐의 연산 과정



### 4. 큐의 구현

![image-20220225124611192](C:\Users\Gyumin\ssafy7\todayilearned\images\image-20220225124611192.png)



### 5. :white_check_mark: 예제 

* 큐를 구현하여 다음 동작을 확인해 봅시다.

  * 세 개의 데이터 1, 2, 3 을 차례로 큐에 삽입하고
  * 큐에서 세 개의 데이터를 차례로 꺼내서 출력한다.
  * 출력 #1, 2, 3

  ```python
  import queue
  
  # Queue 생성
  my_Q = queue.Queue(3)
  
  # 원소 삽입
  my_Q.put(1)
  my_Q.put(2)
  my_Q.put(3)
  
  # get
  elem = my_Q.get()
  
  print(my_Q.qsize())
  print(elem)
  # index로의 접근은 불가능하다
  print(my_Q[1])
  ```

  



## :two: 원형 큐



##