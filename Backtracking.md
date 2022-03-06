# :bulb: Backtracking



## :one: 개념

백트래킹(Backtracking)이란, 솔루션을 찾는 과정에서 유망(promising)하지 않은 후보해에 대해 대해 빠르게 포기하고 이전 단계로 되돌아(back track)가 다른 후보해를 찾는 알고리즘 기법

\- 따라서 운이 좋으면 시행착오를 덜 거치고 목적지에 도착할 수 있지만, 

\- **최악의 경우**에는 모든 경우를 다 거친 다음에 도착할 수 있다. 이 점에서 **브루트포싱과 유사**하지만 가능성이 없다면 배제한다는 점에서 브루트포싱보다는 나은 알고리즘에 해당한다.



## :two: 언제 쓰이는가?

백트래킹은 **제약 충족 문제(CSP, Constraint Satisfaction Problems)**를 풀이하는 데 필수적이다.

제약 충족 문제는 수많은 제약 조건을 충족하는 상태를 찾는 수학 문제다. 대표적으로 스도쿠(sudoku)처럼 1에서 9까지 숫자를 한 번만 넣는(조건) 정답(상태)을 찾는 모든 문제 유형이 있다. 이외 십자말 풀이, 배낭 문제, 문자열 파싱 등이 모두 해당된다.



## :three: DFS vs Backtracking

DFS와 Back-tracking 둘다 재귀 호출 형태로 자주 구현이 되기 때문에 헷갈린다.

두 알고리즘은 사용 목적에 차이가 있다.

- DFS : 깊이 우선 탐색하여 **모든 노드를 방문하는 것을 목표**로 한다.
- Backtracking : 불필요한 탐색을 하지 않기 위해, **유망하지 않은 경우의 수를 줄이는 것을 목표**로 한다.





## :four: 예시: N * M (1)

출처: https://blog.encrypted.gg/732

![image-20220307193909874](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220307193909874.png)



![image-20220307193943800](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220307193943800.png)



![image-20220307193957202](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220307193957202.png)



![image-20220307194010756](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220307194010756.png)



![image-20220307194022919](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220307194022919.png)



![image-20220307194033110](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220307194033110.png)



![image-20220307194048984](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220307194048984.png)



![image-20220307194058088](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220307194058088.png)



![image-20220307194115198](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220307194115198.png)



![image-20220307194135503](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220307194135503.png)

