### stack

- LIFO : 한 쪽 끝에 삽입과 삭제를 할 수 있는 자료구조 
- push 하면 top으로 들어가고, pop 하면 가장 최근에 push한 데이터가 나옴
- 자료가 없을 경우, stack underflow, 스택 크기 이상의 자료는 stack overflow
- 삽입/ 삭제 O(1)

```python
import sys
n=int(sys.stdin.readline())
stack=[] # 스택
answer =[] # 정답
for i in range(n): # 각 명령입력
    c=sys.stdin.readline()
    if "push" in c: 
        tmp=c.split(' ') # 분리해서 idx 1부분입력받음
        stack.append(int(tmp[1]))
        continue
    if "size" in c:
        answer.append(len(stack)) # size 추가
        continue
    if len(stack)==0: # stack 에 값이 없을 경우
        if "empty" in c:
            answer.append(1)
            continue
        answer.append(-1) # empty 제외 다 -1 출력
    else: # stack 에 값이 있을 경우 
        if "pop" in c:
            answer.append(stack.pop(-1))
        elif "top" in c:
            answer.append(stack[-1])
        elif "empty" in c:
            answer.append(0)

for i in answer : # 모두 출력
    print(i)
```

### que

- FIFO : 먼저 삽입된 데이터가 먼저 나오는 자료구조 
- 데이터 삽입 front , 제거 되는 곳 back
- 삽입삭제 O(1)

### DEQUE

- front, back  모두 삽입 삭제 가능.
- 

