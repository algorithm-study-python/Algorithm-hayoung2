## Greedy (그리디 알고리즘)

: 각 단계에서 최선을 선택하여 결과를 도출하는 알고리즘 

- Ex. 거스름돈
- 조이스틱(프로그래머스)  시간복잡도 : O(n)

```python
def solution(name):
    answer=0
    cnt=0# A 개수 추가 
    for i in range(len(name)):     
        # A일경우 
        if name[i]=='A':
            cnt+=1
        else:
            # A 아닐경우-> 앞에 A가 나왔을 경우 들어감.
            if cnt!=0:
                if i-cnt==0 :#0~i까지 계속 a가 나오는 경우
                    answer+=cnt # -> 이동 추가 
                elif i-(cnt+1)<=cnt:#돌아가는 경우가 빠른경우 
                    answer+=i-(cnt+1)#돌아가는 거리 구하기 
                    # 테스트 'BAAAAAB' 같은 경우, 3이 나와야하는데 이걸 계산 
                else:# 앞부분에 a도 있고 다른 알파벳도 있는 경우, 
                    answer+=cnt
            # ABBABBAAB
            # 아스키 코드로 각자 차이 계산해서 적용
            if ord(name[i])-65>13:
                answer+=90-ord(name[i])+1
            else:
                answer+=ord(name[i])-65 
              
            # 마지막 띄어쓰기 안함 
            if i==len(name)-1:
                answer-=1
            # 다음 글자로 넘어가기
            answer+=1
            cnt=0 # A 개수 초기화(이미 A가 아닌 다른 값이 온거니까)
```

