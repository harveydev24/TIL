# Parmetric Search

- 최적화 문제를 결정 문제로 바꾼 뒤 이분 탐색을 이요하여 최적해를 찾는 알고리즘
- 최적화 문제
  - 어떤 값의 최대, 최솟값을 구하는 문제
- 결정 문제
  - 답이 Yes or No로 갈리는 문제
- 최적화 문제를 결정 문제로 바꾸었을 때, 결정문제 답의 분포가` False,False,...,False,True,True,...,True`와 같이 두 구간(반대 경우도 가능)으로 나뉘는 경우에만 이분탐색 사용 가능



## 예시

[BOJ 3079](http://boj.kr/3079)

- 이 문제에서는 입국 심사에 걸리는 시간의 ''최솟값''을 찾아야하므로 최적화 문제임
- 이를 파라메트릭 서치로 풀기 위해 결정문제로 바꿔야함
- 'k초 이하의 시간으로 입국 심사를 할 수 있는가?'로 문제를 바꿀 수 있음



## 틀

- 다음과 같이 구현하면, 항상 `check(start)==False`이고, `check(end)==True`임

  ```python
  while start+1 < end:
      mid = (start+end)//2
      if not check(mid): 
          start = mid
      else: 
          end = mid
  '''
  start = 1, end = 9
  f f f t t t t t t
  1 2 3 4 5 6 7 8 9
  
  start = 1, end = 5
  f f f t t 
  1 2 3 4 5
  
  start = 3, end = 5
  f t t 
  3 4 5
  '''
  ```

  - `while`의 조건을 탈출하는 순간, `start+1 >= end`
  - `while` 문 내부에서는 `start+1 < end` 이므로, `start < mid < end` 가 항상 성립
  - 위 두 조건에 의해 `while` 문 탈출 직후는 항상 `start+1 = end` 성립
  - `while` 문 내부의 조건문에 따라서 `start` 는 항상 `False` 이고, `end` 는 항상 `True` 임
  - 즉, `False, False, ..., False, True, ..., True, True`에서 `False`가 `True`가 되는 순간이 `start`와 `end`.



## 세 줄 요약

1. `[start, end]`가 `check(start) != check(end)`가 되도록 구간을 설정
2. `while start+1<end`일 동안, `check(mid) == check(end)`라면 `start = mid`, 아니라면 `end = mid`
3. 구한 경계에서 답이 `start`인지 `end`인지 생각해보고 출력



## 주의점

- start = (정답의 최솟값)-1, end = (정답의 최댓값)+1
  - 이렇게 설정해야 구간이 이분됨
- 최댓값을 구하는 문제의 경우, 그 보다 작은 값까지 조건이 모두 성립해야하므로 start 출력
  - ... T T T T T T T(<-정답) F F F F ...
- 최솟값을 구하는 문제의 경우, 그 보다 큰 값까지 조건이 모두 성립해야하므로 end 출력
  - ... F F F F F F F T(<-정답) T T T T ...



## 참고 링크

[정리글](https://www.acmicpc.net/blog/view/109)

