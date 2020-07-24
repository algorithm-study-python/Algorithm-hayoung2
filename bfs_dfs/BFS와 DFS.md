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

# 입력하고, 2차원 배열로 연결되었다는 걸 쉽게 풀도록 만든 코드 
N, M, V = map(int, input().split())
mat=[[0] * (N + 1) for i in range(N + 1)]
for i in range(M):
    a,b=map(int,input().split())
    mat[a][b]=1
    mat[b][a]=1
    
# 출력하는 코드
for i in dfs(V,mat,[]) :
    print(i, end = ' ')
print()
for i in bfs(mat,V) :
    print(i, end = ' ')
```

