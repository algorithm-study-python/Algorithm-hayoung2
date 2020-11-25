## ATM

1. 성공

```python
n=int(input())
time= list(map(int, input().split()))
time=sorted(time) # 정렬
result=0
answer=0
for i in time : 
  result +=i # 시간 추가
  answer +=result # 기다린 시간 추가 
print(answer)
```

