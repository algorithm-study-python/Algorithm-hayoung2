## 다익스트라 알고리즘

- 최단 경로 알고리즘에 사용(하나의 정점에서 다른 모든 정점간의 각각 가장 짧은 거리 구하기)
- 가중치 그래프에서 간선의 가중치 합이 최소가 되도록 하는 경로를 찾는 것
  1. 출발점으로 최단거리 저장할 배열을 만들기
  2. 출발노드의 인접 노드 거리 계산
  3. 가장 짧은 거리를 해당 배열에 업데이트
- 최단 경로 문제(우선순위 큐를 사용한 다익스트라 알고리즘) 

```python
import heapq  # 힙구조 사용 
import sys # input은 내장함수고 이거는 따로 생성해줘야함 

# 입력 받음  정점, 간선
v,e =map(int,sys.stdin.readline().split())
k=int(sys.stdin.readline())

# 가장 최댓값으로 지정 (결과값 출력하는 변수)
result=[ 200000 for i in range(v+1)]

result[k]=0 # 처음 시작값 0으로 설정
dis=[[] for _ in range(v+1)] # 각 값들 넣는 곳 
for _ in range(e):#간선받아서 그래프에 저장
    start,end,d=map(int,sys.stdin.readline().split())
    # 값 입력
    # 해당 위치에 이동하는 값,이동하는 위치 
    dis[start].append([d,end])

que=[]# 계산 하는 큐 
heapq.heappush(que,[0,k])# 처음 시작값은 0으로 시작 

# que 에 계산
while que:
    # 값을 가져오고 (힙은 알아서 정렬) 
  w,end=heapq.heappop(que)
  for d,x in dis[end]: # 해당하는 값 가져옴
    d+=w # 이동한 값 
    if d<result[x]: # 작을 경우 최종 결과 바꿔줌
      result[x]=d
      heapq.heappush(que,[d,x]) # 다시 큐에 넣음 계산

 #계산 
for i in range(1,v+1):
    # 200000일 경우, 이동할 수 있는 경로 없다는 것
  if result[i]==200000:
    print('INF') # InF출력
  else:
    print(result[i]) # 아니면 경로 있음 출력
```

