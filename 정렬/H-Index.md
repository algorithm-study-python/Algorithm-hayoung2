## H-Index

#### 정렬

1. 첫번째 테스트 코드(3개)만 맞고 다 틀림 ㅎ

```python
def solution(citations):
    answer = 0
    number=[]

    while True :
        tmp=1
        for j in range(0,len(citations)):
            if(citations[0]<= citations[j] and 0!=j):
                tmp +=1
        number.append(tmp)
        break
    answer =max(number)
    return answer
```



2. 두번째 성공
   - 문제 이해를 못해서 질문하기에서 문제 이해 후 다시 

```python
def solution(citations):
    answer = 0
    number=[]# 값 넣어 주는 곳
    # 각 값보다 높은 값 찾으려고 반복문 
    for i in range(0,len(citations)) :
        tmp=1# 자신 값 추가
        # 모든 위치 확인, 본인 위치 제외 
        for j in range(0,len(citations)):
            if(citations[i]<= citations[j] and i!=j):
                tmp +=1 # i위치에 인용된 논문 수보다 많은 경우 추가
        # 인용이 더 적게 된 것을 선택해서 넣어야 함
        if tmp < citations[i] :
            number.append(tmp)
        else :
            number.append(citations[i])
    answer = max(number) # 각 인용 수들에서 가장 큰 값 구하기.
    return answer
# 각 논문에서 인용된 논문의 수가 들어 있는  중 더 작은 값을 넣는 것
```

