# 위상 정렬

- 어떤 일을 하는 순설르 찾는 알고리즘
- 사이클이 없는 방향 그래프에 존재하는 각 정점들의 선행 순서를 위배하지 않으면서 모든 정점을 나열하는 알고리즘

​	![img](https://gmlwjd9405.github.io/images/algorithm-topological-sort/topological-sort.png)



## 진입차수와 진출차수

- 진입차수

  - 특정한 노드로 들어오는 간선의 개수

- 진출차수

  - 특정한 노드에서 나가는 간선의 개수

  ![img2](README.assets/image.png)



## 위상 정렬 알고리즘

1. 정점의 진입차수(indegree)를 담는 배열을 선언하고 0으로 초기화함

2. 그래프 정보를 바탕으로 진입차수를 더해나감

3. 큐를 만들고, 진입차수가 0인 정점들을 넣음

4. 큐의 앞에서부터 원소를 `pop` 하고, 그 원소를 선행 정점으로 가지는 정점들의 진입차수를 1씩 낮춤

5. 진입차수가 0인 정점들을 큐에 추가하고 끝날 때 까지 반복

   ```python
   #백준 2252번
   from collections import deque
   import sys
   input = sys.stdin.readline
   
   N, M = map(int, input().split())
   array = [[] for _ in range(N+1)]
   indegree = [0] * (N+1)
   
   q = deque([])
   
   for _ in range(M):
       a, b = map(int, input().split())
       array[a].append(b)
       indegree[b] += 1
   
   for idx, value in enumerate(indegree):
       if idx == 0: continue
       if value == 0:
           q.append(idx)
   
   while q:
       tmp = q.popleft()
       print(tmp, end=" ")
       for item in array[tmp]:
           indegree[item] -= 1
           if indegree[item] == 0:
               q.append(item)
   ```

## 위상 정렬 특징

- 위상 정렬은 사이클이 없는 방향 그래프에 대해서만 수행 가능
- 여러 가지의 답이 존재할 수 있음
- 모든 정점을 방문하기 전에 큐가 비게 되면, 사이클이 존재한다고 판단 가능
  - 사이클을 이루는 정점은 큐에 들어가지 못하기 때문

- 시간 복잡도는 O(V+E)
  - 모든 정점을 순회하면서 (O(V)), 간선을 끊어야하므로 (O(E)) -> O(V+E)

## 관련문제

[백준 2252번](https://www.acmicpc.net/problem/2252)