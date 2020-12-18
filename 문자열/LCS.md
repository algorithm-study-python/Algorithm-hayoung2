## LCS

1. 코드

```python
import sys
# 입력
S1 = sys.stdin.readline().strip().upper() 
S2 = sys.stdin.readline().strip().upper() 

len1 = len(S1) 
len2 = len(S2) 
# 각 문자를 분리해서 넣음. 각 문자들이 같아질 수 있는지 체크 함 
matrix = [[0] * (len2 + 1) for _ in range(len1 + 1)] 

for i in range(1, len1 + 1): 
    for j in range(1, len2 + 1): # 같을 경우, 1 추가 
        if S1[i - 1] == S2[j - 1]: 
            matrix[i][j] = matrix[i - 1][j - 1] + 1 
        else: # 같지않을경우, 선택된 값
            matrix[i][j] = max(matrix[i - 1][j], matrix[i][j - 1]) 
print(matrix[-1][-1]) # 마지막 값 출력


```

