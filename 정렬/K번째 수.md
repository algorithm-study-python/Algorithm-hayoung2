## K번째 수

#### 정렬

```python
def solution(array, commands):
    answer = []
    cnt=0
    # commands 에 값이 있을 때까지
    while commands :
        # array에 있는 commadns 첫번째값부터  두번째값까지 배열에 저장.
        #-1은 0부터 시작 안해서 
        tmp =array[commands[cnt][0]-1:commands[cnt][1]]
        tmp.sort()# 정렬
        #오름차순으로 정렬된 배열에 commands에 세번째에 해당하는 값 저장
        answer.append(tmp[commands[cnt][2]-1])
        # 완료된 것 제거
        commands.pop(0)
    return answer
```

