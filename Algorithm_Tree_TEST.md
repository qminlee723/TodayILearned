# Algorithm_Tree_TEST



\* 트리 계산기 부터 쭉 보기



* 트리

  * 원소들 간 1:n 관계를 가지는 자료구조
  * 원소들 간에 계층 관계를 가지는 계층형 자료구조
  * 상위 원소에서 하위 원소로 내려가면서 확장되는 트리 모양의 구조

* 이진트리

  * 모든 노드들이 2개의 서브트리를 갖는 특별한 형태의 트리
  * 각 노드가 자식 노드를 2개까지만 가질 수 있는 트리
  * 높이가 h인 이진트리가 가질 수 있는 노드의 최소 갯수는 (h+1)개, 최대 갯수는 2 ^ (h+1) -1 개
  * 

* 완전이진트리

  * 높이가 h이고 노드 수가 n개 일 때, 포화 이진 트리의 노드 번호 1번부터 n개까지 빈자리가 없는 이진트리

* 포화이진트리

  * 모든 레벨에 노드가 포화상태로 차 있는 이진트리
  * 이진 트리의 최대 노드 갯수를 가진 이진 트리

* 이진트리를 리스트로 표현하면 어떻게 될까?

  * 부모 자식
  * 간선은 부모 정점 번호가 작은 것부터 나열
  * 부모 정점이 동일하다면 자식 정점 번호가 작은 것부터 나열

* 삭제 삽입 어떻게 하는가?

  * 삽입

    ![image-20220403190010890](C:/Users/Gyumin/AppData/Roaming/Typora/typora-user-images/image-20220403190010890.png)

    1. 먼저 탐색 연산 수행
    2. 같은 원소가 트리에 있는지 탐색
    3. 탐색 실패가 결정되는 위치가 삽입 위치
    4. 탐색 실패한 위치에 삽입

  * 삭제

    1. 탐색 연산 수행
    2. 트리에 있으면 삭제 
       1. 만약 리프 노드이면 그냥 삭제
       2. 삭제할 노드의 차수가 1이면 바로 위 조상 노드에 손자 노드 연결
       3. 삭제할 노드의 차수가 2 이상이면, 삭제하고 -> 후보 찾고 -> 이동

* HEAP이란?

  * 완전 이진 트리에 있는 노드 중에서 키 값이 가장 큰 노드나, 키 값이 가장 작은 노드를 찾기 위해 만든 자료구조

* 최대힙(max heap)

  * 키 값이 가장 큰 노드를 찾기 위한 완전 이진 트리
  * 부모 노드의 키 값 > 자식 노드의 키 값
  * 루트 노드: 키 값이 가장 큼

* 최소힙(min heap)

  * 키 값이 가장 작은 노드를 찾기 위한 완전 이진 트리
  * 부모 노드의 키 값 < 자식 노드의 키 값
  * 루트 노드: 키 값이 가장 작음

* 이진트리의 예 - 왜 힙이 아닌지?

  ![image-20220403190410162](C:/Users/Gyumin/AppData/Roaming/Typora/typora-user-images/image-20220403190410162.png)

  * 트리 1
    * 힙은 완전 이진 트리의 한 가지로, 일단 완전 이진 트리의 조건을 만족시켜야 한다. 그러나 트리 1의 경우 완전 이진트리가 아니다 
    * 완전 이진트리란 포화 이진트리에서 오른쪽 리프부터 제거해 나간 트리를 말하는데, 8의 자식 노드인 5, 그리고 그 자식노드인 1이 왼쪽이 아닌 오른쪽에 위치해 있으므로 완전 이진트리라고 볼 수 없다.
  * 트리 2
    * 일단 루트 자체가 최소값도 최대값도 아니므로 어떠한 힙도 될 수 없음
    * 또한, 11의 키 값을 갖는 노드의 자식이 부모 노드와 같은 키 값을 가지고 있으므로 힙이라고 할 수 없음(최대 힙인 경우, 부모가 자식보다 큰 값을, 최소 힙인 경우 부모가 자식보다 작은 값을 가져야 함)

* 삽입하면 어떻게 되는지

  ![image-20220403191921871](C:/Users/Gyumin/AppData/Roaming/Typora/typora-user-images/image-20220403191921871.png)

  1. 새로 값을 삽입할 노드 확장
  2. 확장한 자리에 새로운 값을 임시 저장
  3. 현재 위치에서 부모 노드와 크기 비교 후 자리 확정

* 삭제는 어떻게 이루어지는지

  <img src="C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220316153933152.png" alt="image-20220316153933152" style="zoom:50%;" />

  * 삭제는 루트의 원소만을 삭제할 수 있다
    1. 루트 노드 안의 원소 보관
    2. 마지막 노드 삭제 후 루트로 옮김
    3. 마지막 노드 인덱스 감소 
    4. 최대힙이 되도록 자리 바꾸기
    5. 자리 확정

