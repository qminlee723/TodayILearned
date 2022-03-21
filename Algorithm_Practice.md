#  문제풀이

[TOC]



## :one: 넓이 우선 탐색: BFS 알고리즘

### 1. 기본 템플릿

```python
def BFS(G, v, n):
    # 생성
    visited = [0] * (n + 1)
    queue = []
    # 시작
    queue.append(v)
    visited[v] = 1
    
    while queue:
        t = queue.pop(0)
        visit(t)
    # 조건 ( 문제마다 이 조건이 달라지는 것 )
    	for i in G[t]:
            if not visited[i]:
                queue.append(i)
                visited[i] = visited[n] +1
```



### 2. 미로의 거리(5105)

```python
def bfs(si, sj, ei, ej):
    q = []
    visited = [[0] * N for _ in range(N)]
    
    q.append([si, sj])
    visited[si][sj] = 1
    
    while q:
        ci, cj = q.pop(0)
        if ci == ei and cj == ej:
            return visited[ci][cj] - 2
        
        # 조건
        for di, dij in ([-1, 0], [1, 0], [0, -1], [0, 1]):
            ni, nj = ci + di, cj + dj
            if 0 <= ni < N and 0 <= nj < N and visited[ni][nj] == 0 and\
            	MAP[ni][nj] != '1':
                q. append([ni, nj])
                visited[ni][nj] = visited[ci][cj] + 1
	return 0
```

![image-20220318093130321](C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220318093130321.png)



### 2. contact(1238)

![image-20220318094412732](C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220318094412732.png)

```python
```



![image-20220318100008310](C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220318100008310.png)

![image-20220318100657537](C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220318100657537.png)

![image-20220318101136969](C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220318101136969.png)

```python
T = 1

for test_case in range(1, T+1):
    N, S = map(int, input().split())
    lst = list(map(int, input().split()))
    # 리스트 연결값을 인접 행력에 저장
    adj = [[0] * 101 for _ in range(101)]
    
    # 조건
    for i in range(0, len(lst)), 2):
        adj[lst[i]][lst[i+1]]
        
    ans BFS(S)
    print(f'#{test_case} {ans}'')
```

```python
def BFS(s):
    q = []
    v = [0] * 101
    
    q.append(s)
    v[s] = 1
    sol = s
    
    while q:
        c = q.pop(0)
        if v[sol] < v[c] or v[sol] == v[c] and sol < c
            sol = c
        
        for j in range(1, 101):
            if adj[c][j] and v[j] == 0:
                q.append(j)
                v[j] = v[c] + 1
                
    return sol 
```



### 3. 정사각형 방(1861)

![image-20220318105841558](C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220318105841558.png)

![image-20220318111531471](C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220318111531471.png)

```python
T = 1

for test_case in range(1, T+1):
    N = int(input())
    arr = [list(map(int, input().split)) for _ in range(N)]
    v = [[0] * N for _ in range(N)]
    num = N * N 
    cnt = 0
    
    for i in range(N):
        for j in range(N):
            if v[i][j] == 0: # 방문 안 한 곳이라면
                tn, tc = BFS(i, j)
                if cnt < tc or cnt == tc and num > tn:
                    cnt = tc
                    num = tn
    print(f'#{test_case} {num} {cnt})   
```

```python
def BFS(si, sj):
    q = []
    s = []
    
    q.append((si, sj))
    v[si][sj] = 1
    s.append(arr[si][sj])
    
    while q:
        ci, cj = q.pop(0)
        
        # 조건
        for di, dj in ((-1, 0), (1, 0), (0, -1), (0, 1)): # 상 하 좌 우
            ni, nj = ci + di, cj + dj
            if 0 <= ni < N and 0 <= nj < N and v[ni][nj] == 0 and \
            	abs(arr[ci][cj] - arr[ni][nj]) == 1:
                    q.append((ni, nj))
                    v[ni][nj] = 1
                    s.append(arr[ni][nj])
    return min(s), len(s)
```



### 4. 탈주범 검거(1953)

![image-20220318112836360](C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220318112836360.png)

![image-20220318125917400](C:\Users\Gyumin\ssafy7\TodayILearned\images\image-20220318125917400.png)

![image-20220318142131580](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220318142131580.png)



```python

pipe = [[0,0,0,0],[1,1,1,1],[1,1,0,0],[0,0,1,1],[0,1,0,1],[0,1,1,0],[1,0,1,0]]
di, dj = (-1,1,0,0), (0,0,-1,1) # 상하좌우
opp = [1,0,3,2]	# 하상우좌

def BFS(N, M, R, C, L):
    q = []
    v = [0] * M for _ in range(N)	# visited배열을 초기화
    
    q.append((si,sj))	# q에 시작좌표 넣어주기
    v[si][sj] = 1		# visited 표기해주기
    cnt = 1				# 갯수 (start 하나) 
	
    while q:
        ci, cj = q.pop(0)	# 현재 좌표를 꺼내준다
        
        if v[ci][cj] == L:	# 종료조건(찾았다면)
            return cnt 
        
        for k in range(4):	# 방향(상하좌우) 체크
            ni, nj = ci + di[k], cj + dj[k]	# 다음 좌표를 할당해주자
            if 0 <= ni < N and 0 <= nj < M and v[ni][nj] == 0 and \ # 범위 내
            	# 내 파이프가 진행하려는 방향이 1이어야 하고
                # 상대 파이프도 진행되는 방향에 1을 가지고 있어야 진행이 된다.
            	pipe[arr[ci][cj][k] and pipe[ni][nj]][opp[k]]:
                q.append((ni,nj))
                v[ni][nj] = v[ci][cj] + 1
                cnt += 1
    return cnt # 종료조건(못 찾았을 때)
# T = 10
T = int(input())
for test_case in range(1, T + 1):
    N, M, R, C, L = map(int, input().split())
    arr = [list(map(int, input().split())) for _ in range]
    ans = BFS(N, M, R, C, L)
    print(f'#{test_case} {ans}')
```



### BFS로 접근하지 말아야 하는 경우

* 복잡도 N 을 기준으로 확인하자

* 1000 * 1000





## :two: 깊이우선탐색 DFS

* 가능한 모든 경우를 처리해서 답을 찾는 문제(예시: 부분집합의 합)
* 가능한 모든 경우를 표현하는 효율적인 방법: Tree(상태공간 트리 설계)

```python
def DFS(n, ssum):
    global sol
    
    # 가지치기 선택        
    
    # 종료조건(기본적으로 n 관련)
    if n >= N:
        if ssum == K:
            sol += 1
        return
        
        #정답처리
        return
    
    # 하부함수 호출
    DFS(n+1, ...)
    DFS(n+1, ...)
```



### 1. 



```python
def DFS(n):
    global sol
    
    # 가지치기 선택
    if n == N:
        if ssum >= B and ans > ssum - B:
            ans = 
    # 종료조건(기본적으로 n 관련)
    if n >= N:
        
        #정답처리
        return
    
    # 하부함수 호출
    DFS(n+1, ...)
    DFS(n+1, ...)
```

