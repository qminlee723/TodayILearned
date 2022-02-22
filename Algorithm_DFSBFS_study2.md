# DFS vs BFS



## :one: DFS

* stack

* 백트래킹 - 모든 경우의 수를 탐색

* 그래프 탐색인거 같을 때 DFS 사용

  



## :two: BFS

* queue
* 탐색시 최단거리 보장, 최단시간 보장시 BFS 사용





## :three: 문제

```python
# node의 길이가 주어졌을 때, 최단 거리 탐색
1 2 10

cost = [[0]*(V+1) for _ in range(V+1)]

```

```python
# 몇 번의 노드를 거쳐왔는지? 어떤 노드를 거쳐왔는지 탐색
# parent를 만들어서 탐색 가능함!
#D

def bfs(graph, start, visited):
    queue = deque([start])
    visited[start] = True
    
    while queue:
        v = queue.popleft()
        
        for i in graph[v]:
            if not visited[i]:
                queue.append(i)
                visited[i] = True
                parent[i] = v

N = int(input())
M = int(input())
graph = [[] for _ in range(N+1)]
visitied = [False] * (N+1)
parent = [-1] * (N+1)
parent[1] = 1

for _ in range(M):
    a, b = map(int, input().split())
    graph[a].append(b)
    graph[b].append(a)
    
bfs(graph, 1, visited)

print(visited.count(Ture)-1)

while start != parent[start]:
    print(start)
    start = parent[start]
print(start)
```

```python
# dictionary 사용
# 노드를 알파벳으로 주는 경우 있음
# dictionary / ord와 chr을 써서 문자를 숫자로 바꾸는 방법

adj = dict('A': [], 'B': [])
adj['A'].append('B')
```

```python
# 무방향 그래프일 경우(Undirected graph)
def bfs(graph, start, visited):
    queue = deque([start])
    visited[start] = True
    
    while queue:
        v = queue.popleft()
        
        for i in graph[v]:
            if not visited[i]:
                queue.append(i)
                visited[i] = True
                parent[i] = v

N = int(input())
M = int(input())
graph = [[] for _ in range(N+1)]
visitied = [False] * (N+1)
parent = [-1] * (N+1)
parent[1] = 1

for _ in range(M):
    a, b = map(int, input().split())
    graph[a].append(b)
#    graph[b].append(a) 방향그래프일때, a->b로 간다고 치면 이 부분을 삭제해준다
    
bfs(graph, 1, visited)

print(visited.count(Ture)-1)

while start != parent[start]:
    print(start)
    start = parent[start]
print(start)
```

