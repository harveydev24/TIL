# Union & Find

- 기본적으로 parent 배열은 인덱스 자기 자신으로 초기화

  ```python
  # [0, 1, 2, ..., n]
  partent = [x for x in range(n+1)]
  ```

## Find

- 부모 노드를 찾음

  ```python
  def findParent(a):
      while a != parent[a]:
          a = parent[a]
      return a
  ```

- 위의 코드는 잘 작동하지만, 시간이 오래걸림

- 따라서 아래와 같이 부모 노드를 찾을 때 마다 parent 배열을 바꿔줘야함

  ```python
  def findParent(a):
      tmp = a
      while a != parent[a]:
          a = parent[a]
      parent[tmp] = a
      return a
  ```

- 좀 더 간단하게 다음과 같이 쓸 수도 있음

  ```python
  def findParent(a):
      if parent[a] != a:
          parent[a] = find(Parent(parent[a]))
      return parent[a]
  ```

  

## Union

- 부모 노드를 찾은 후, 다르다면 한 쪽의 부모를 다른 한 쪽으로 바꿈

  ```python
  def union(a, b):
      a = find(a)
      b = find(b)
      if a != b:
          parent[a] = b
  ```

- 순서가 중요할 경우 다음과 같이 구현할 수도 있음

  ```python
  def union(a, b):
      a = find(a)
      b = find(b)
      if a <= b:
          parent[b] = a
      else:
          parent[a] = b
  ```

  

## 관련문제

[백준 1717번](https://www.acmicpc.net/problem/1717)