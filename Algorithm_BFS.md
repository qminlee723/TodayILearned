# BFS/백트래킹 템플릿

## :one: 1249. 보급로

### 1. 문제

[1249. 보급로](https://swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AV15QRX6APsCFAYD)

![image-20220404170506514](Algorithm_BFS.assets/image-20220404170506514.png)

### 2. 설계

![image-20220404172411502](Algorithm_BFS.assets/image-20220404172411502.png)

* 중복 방문 허용하되 조건은 이전 결과보다 더 나은 결과



### 3. 코드

```python
def BFS(si, sj, ei, ej):
    # 1. q, visited 생성
    q = []
    visited = [[1000000] * N for _ in range(N)]
    
    # 2. q 초기데이터 삽입, visited 표시
    q = [(si, sj)]
    visited[si][sj] = arr[si][sj] # arr[si][sj] 대신 0 써줘도 됨(문제)
    
    while q:
        ci, cj = q.pop(0)
        
        # 4방향, 8방향, 숫자 차이가 일정값 이하...
        for di, dj in ((-1,0),(1,0),(0,-1),(0,1)):
            ni, nj = ci + di, cj + dj 
            if 0 <= ni < N and 0 <= nj < N and visited[ni][nj] > visited[ci][cj] + arr[ni][nj]:
                q.append((ni, nj))
                visited[ni][nj] = visited[ci][cj] + arr[ni][nj]
    return visited[ei][ej]
    
    
T = int(input())
for tc in range(1, T + 1):
    N = int(input())
    arr = [list(map(int, input())) for _ in range(N)]
    ans = BFS(0, 0, N-1, N-1)
    print(f'#{tc} {ans}')
```



## :two: 2806. N-Queen

### 1. 문제

[2806. N-Queen](https://swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AV7GKs06AU0DFAXB)

![image-20220404173602183](Algorithm_BFS.assets/image-20220404173602183.png)

### 2. 설계

![image-20220404194231682](Algorithm_BFS.assets/image-20220404194231682.png)

### 3. 코드

```python
def check(si, sj):
    #1. 위쪽 방향
    for i in range(si-1, -1, -1):
        # 퀸을 마주친다면 실패
        if visited[i][sj] == 1:
            return 0
    #2. 좌측 대각선 위
    i, j = si-1, sj-1
    while i >= 0 and j >= 0:
        if visited[i][j] == 1:
            return 0
        # 퀸을 마주치지 않았다면 상단으로 이동
        i, j = i-1, j-1
    
    #3. 우상단
    i, j = si-1, sj+1
    while i >= 0 and j < N:
        if visited[i][j] == 1:
            return 0
        i, j = i-1, j+1
        
    # 퀸을 마주치지 않았다면: 성공!
    return 1
        
        
        
def DFS(n):
    global ans
    if n == N:
        ans += 1
        return
    
    for j in range(N):
        if check(n,j):
            # n행 j열에 퀸을 배치
            visited[n][j] = 1
            DFS(n+1)
            visited[n][j] = 0
    
    
T = int(input())
for tc in range(1, T + 1):
    N = int(input())
    visited = [[0] * N for _ in range(N)]
    ans = 0
	DFS(0)
    print(f'#{tc} {ans}')
```



### 4. REFACTORING

* 배열을 만들어서 체크 

  ![image-20220404211353644](Algorithm_BFS.assets/image-20220404211353644.png)

```python
def DFS(n):
    global ans
    if n == N:
        ans += 1
        return
    
    for j in range(N):
        if v1[j] == v2[n+j] == v3[n-j] == 0:
            v1[j] = v2[n+j] = v3[n-j] = 1
            # n행 j열에 퀸을 배치
            DFS(n+1)
            v1[j] = v2[n+j] = v3[n-j] = 0
    
    
T = int(input())
for tc in range(1, T + 1):
    N = int(input())
    ans = 0
    v1, v2, v3 = [0] * 30, [0] * 30, [0] * 30
    DFS(0)
    print(f'#{tc} {ans}')
```



## :three: 2115. 벌꿀채취

### 1. 문제

[2115. 벌꿀채취](https://swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AV5V4A46AdIDFAWu&)

![image-20220404211816318](Algorithm_BFS.assets/image-20220404211816318.png)

### 2. 설계

![image-20220404212041784](Algorithm_BFS.assets/image-20220404212041784.png)

### 3. 코드

```python
# 부분집합의 합

def DFS(n, cnt, ssum, lst):
    global sol
    if cnt > C: # 가지치기
        return
    
    # n이 모든 배열, 부분집합의 합들을 다 썼다면,
    if n == M:
        if cnt <= C and sol < ssum:
            sol = ssum
        return
    
    # 포함시키지 않는 경우
    DFS(n+1, cnt, ssum, lst)
    # 포함시키는 경우
    DFS(n+1, cnt+lst[n], ssum+lst[n]**2, lst)
    
T = int(input())
for tc in range(1, T + 1):
    # N = 벌통 크기, M = 벌통 갯수,  C = 꿀 최대 양
    N, M, C = map(int, input().split())
    arr = [list(map(int, input().split())) for _ in range(N)]
    visited = [0 * N for _ in range(N)]
    ans = 0
    
    # 일꾼 1(i1)
    for i1 in range(N):
        for j1 in range(N-M+1):
            sol = 0
            # 0번째 인덱스부터 시작, 카운트, 최대수익, 선택했으면 M개만큼을 보낸다
            # sol 최댓값을 구해놓고
            DFS(0, 0, 0, arr[i1][j1:j1+M])
            # 최댓값을 t1에 저장
            t1 = sol
            
            # 일꾼 2(i2)
            for i2 in range(i1, N):
                sj = 0
                if i1 == i2:
                    sj = j1 + M
                for j2 in range(sj, N-M+1):
                    sol = 0
                    DFS(0, 0, 0, arr[i2][j2:j2+M])
                    ans = max(ans, t1+sol)

    print(f'#{tc} {ans}')
```

### 4. REFACTORING

```python
# Memoization 

def DFS(n, cnt, ssum, lst):
    global sol
    if cnt > C: # 가지치기
        return
    
    # n이 모든 배열, 부분집합의 합들을 다 썼다면,
    if n == M:
        if cnt <= C and sol < ssum:
            sol = ssum
        return
    
    # 포함시키지 않는 경우
    DFS(n+1, cnt, ssum, lst)
    # 포함시키는 경우
    DFS(n+1, cnt+lst[n], ssum+lst[n]**2, lst)
    
T = int(input())
for tc in range(1, T + 1):
    # N = 벌통 크기, M = 벌통 갯수,  C = 꿀 최대 양
    N, M, C = map(int, input().split())
    arr = [list(map(int, input().split())) for _ in range(N)]
    ans = 0
    
    ###### MEMOIZATION ######
    mem = [[0] * N for _ in range(N)]
    for i in range(N):
        for j in range(N-M+1):
            sol = 0
            DFS(0, 0, 0, arr[i][j:j+M])
            mem[i][j] = sol
    
    # 일꾼 1(i1)
    for i1 in range(N):
        for j1 in range(N-M+1):
            # 일꾼2
            for i2 in range(i1, N):
                sj = 0
                if i1 == i2:
                    sj = j1 + M
                for j2 in range(sj, N-M+1):
                    ans = max(ans, mem[i1][j1] + mem[i2][j2])


    print(f'#{tc} {ans}')
```





## :four: 5648. 원자 소멸 시뮬레이션

### 1. 문제

![image-20220404211845217](Algorithm_BFS.assets/image-20220404211845217.png)

### 2. 설계

![image-20220404213456703](Algorithm_BFS.assets/image-20220404213456703.png)

### 3. 코드

```python
T = int(input())
di, dj = (1, -1, 0, 0), (0, 0, -1, 1)
for tc in range(1, T + 1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    
    for i in range(len(arr)):
        arr[i][0] *= 2
        arr[i][1] *= 2
    
    ans = 0
    # 끝에서 끝: -2000 ~ 2000
    for _ in range(4002):  
        # 1. 좌표이동
        for i in range(len(arr)):
            arr[i][0] += dj[arr[i][2]]
            arr[i][1] += di[arr[i][2]]
            
        # 2. 중복되면 삭제
        # 지울 리스트 set으로 생성
        ddel, v = set(), set
        for i in range(len(arr)):
            cj, ci = arr[i][0], arr[i][1]
            if (cj, ci) in v:
                ddel.add((cj, ci))
            v.add((cj,ci))
            
        # 3. 삭제리스트에 있으면 삭제
        for i in range(len(arr)-1, -1, -1):
            if (arr[i][0], arr[i][1]) in ddel:
                ans += arr[i][3]
                arr.pop(i)
                
   
    print(f'#{tc} {ans}')
```



### 4. REFACTORING

```python
T = int(input())
di, dj = (1, -1, 0, 0), (0, 0, -1, 1)
for tc in range(1, T + 1):
    N = int(input())
    arr = [list(map(int, input().split())) for _ in range(N)]
    
    for i in range(len(arr)):
        arr[i][0] *= 2
        arr[i][1] *= 2
    
    ans = 0
    # 끝에서 끝: -2000 ~ 2000
    for _ in range(4002):  
        # 1. 좌표이동
        for i in range(len(arr)):
            arr[i][0] += dj[arr[i][2]]
            arr[i][1] += di[arr[i][2]]
            
        # 2. 중복되면 삭제
        # 지울 리스트 set으로 생성
        ddel, v = set(), set
        for i in range(len(arr)):
            cj, ci = arr[i][0], arr[i][1]
            if (cj, ci) in v:
                ddel.add((cj, ci))
            v.add((cj,ci))
            
        # 3. 삭제리스트에 있으면 삭제
        for i in range(len(arr)-1, -1, -1):
            if (arr[i][0], arr[i][1]) in ddel:
                ans += arr[i][3]
                arr.pop(i)
        
        if len(arr) < 2:
            break
   
    print(f'#{tc} {ans}')
```

