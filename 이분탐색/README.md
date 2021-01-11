## binary search(이분탐색)

:  정열되어 있는 배열에서 탐색 범위를 절반씩 줄여나가며 특정 값을 찾는 알고리즘. 

- 시간복잡도 : log n 
- 정렬된 리스트에서만 사용 가능하며, 선형탐색(n)과 비교하여 탐색 시간이 빠름

```python
arr=[1,5,2,34,53,27,9,3]
def binarySearch(arr,targetNum,start,end):
    mid=(start+end)//2
    if arr[mid]==targetNum:
        return mid
    while start<=end:
        if arr[mid] >targetNum:
            end=mid
        else:
            start=mid
        
arr.sort()
print(binarySearch(arr,9,0,len(arr)))
```

