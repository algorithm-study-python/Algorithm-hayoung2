## BFS와 DFS

#### BFS/DFS

1. 첫번째

```python
def dfs(start,mat,prints):
    prints +=[start]
    for i in range(len(mat[start])):
        if mat[start][i] and i not in prints:
            prints=dfs(i,mat,prints)
    return prints
    
def bfs(mat,start):
    que=[start]
    prints=[start]
    while que :
        node=que.pop(0)
        for i in range(len(mat[node])):
            if mat[node][i] and i not in prints:
                que.append(i)
                prints.append(i)
    return prints

N, M, V = map(int, input().split())
mat=[[0] * (N + 1) for i in range(N + 1)]
for i in range(M):
    a,b=map(int,input().split())
    mat[a][b]=1
    mat[b][a]=1
    
print(dfs(mat,V,[]))
print(bfs(mat,V))
# ㅊ음에 리스트로 해서 틀림
    
```

2. 성공

```python
def dfs(start,mat,prints):
    # 맨 처음 들어감, 그리고 다음 이동하면 추가
    prints +=[start]
    for i in range(len(mat[start])):
         # 연결되어 있는 경우, 출력되지않았을경우,
        if mat[start][i] and i not in prints:
            prints=dfs(i,mat,prints)# 반복
    return prints
    
def bfs(mat,start):
    que=[start]
    prints=[start]
    while que :
        # 값 빼서 확인
        node=que.pop(0)
        for i in range(len(mat[node])):
            # 연결되어 있는 경우, 출력되지않았을경우,
            if mat[node][i] and i not in prints:
                que.append(i) # 큐에 다음 값 넣기 
                prints.append(i)# 출력 값에 넣기
    return prints

# 입력하고, 2차원 배열로 연결되었다는 걸 쉽게 풀도록 만든 코드 
N, M, V = map(int, input().split())
mat=[[0] * (N + 1) for i in range(N + 1)]
# 서로 연결되어 있는 것들 1로 입력. 
for i in range(M):
    a,b=map(int,input().split())
    mat[a][b]=1
    mat[b][a]=1
    
# 출력하는 코드
# V는 시작하는 위치. 
for i in dfs(V,mat,[]) :
    print(i, end = ' ')
print()
for i in bfs(mat,V) :
    print(i, end = ' ')
```

