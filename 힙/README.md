## 힙

- 완전 이진 트리의 일종. 우선순위 큐를 위해 만들어진 자료구조
- 여러개의 값들 중에서 최댓값이나 최솟갑을 빠르게 찾아내도록 만들어짐(반정렬상태)
- Max Heap: 부모노드가 자식 노드보다 크거나 같은 완전 이진 트리
- Min Heap : 부모노드가 자식 노드보다 작거나 같은 이진 트리 
- 삽입, 삭제 O(log n)

![heapify](https://user-images.githubusercontent.com/39898938/105790948-8b4b5500-5fc8-11eb-9274-64566d28a0e5.jpg) 

- 프로그래머스 더 맵게 문제(힙 사용)

```python
import heapq
def solution(scoville, K):
    answer = 0 # scoville에 가장 작은 값이 k 값을 넘을 때까지 계산
    heapq.heapify(scoville) # 정렬 
    # scoville이 없어질 때까지 
    while len(scoville)>1 :
        # 가장 작은 값이 K보다 작을 경우,
        if scoville[0] < K:
            # 가장 작은 값 + 다음으로 작은 값 더해서 scoville에 다시 넣기
            heapq.heappush(scoville, heapq.heappop(scoville)+(heapq.heappop(scoville)*2))
            # 계산했으니까 ++
            answer += 1
        else :
            # 클 경우, answer 리턴
            return answer
     # 하나 남은게 K보다 클 경우, answer 리턴
    if scoville[0] > K:
        return answer
    # k를 넘지 못했으면 -1 리턴 
    else :
        return -1
```


