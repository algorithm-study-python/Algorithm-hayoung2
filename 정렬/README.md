## 정렬 알고리즘

- 시간복잡도 O(n2)

  1) 버블 정렬

     : 두 인접한 원소 검사 

  ```python
  def bubbleSort(arr):
    for i in range(len(arr)):
      for j in range(len(arr)-1):
        if arr[j]>arr[j+1]:
          tmp=arr[j]
          arr[j]=arr[j+1]
          arr[j+1]=tmp
  
  if __name__=="__main__":
    arr=[4,3,1,2,0]
    bubbleSort(arr)
      
  # [3, 4, 1, 2, 0]
  # [3, 1, 4, 2, 0]
  # [3, 1, 2, 4, 0]
  # [3, 1, 2, 0, 4]
  ```

  

  2) 선택정렬

     : 최소값 선택해서 정렬

  ```python
  def selectionSort(arr):
    for i in range(len(arr)):
      min=i
      for j in range(i+1,len(arr)):
        if arr[min]>arr[j]:
          min=j
      tmp=arr[i]
      arr[i]=arr[min]
      arr[min]=tmp
      print(arr)
  
  if __name__=="__main__":
    arr=[4,3,1,2,0]
    selectionSort(arr)
  # [0, 3, 1, 2, 4]
  # [0, 1, 3, 2, 4]
  ```

  

  3) 삽입 정렬

    : 자신의 위치를 찾아 삽입하는 정렬 

  ```python
  def insertionSort(arr):
    for i in range(1,len(arr)):
      tmp=arr[i]
      idx=0
      for j in range(i-1,-1,-1):
        if arr[j]>tmp :
          arr[j+1]=arr[j]
        else:
          idx+=1
          break
      
      arr[idx]=tmp
  
  
  if __name__=="__main__":
    arr=[4,3,1,2,0]
    insertionSort(arr)
      
  # [4, 4, 1, 2, 0]
  # [3, 4, 1, 2, 0]
  # [3, 4, 4, 2, 0]
  # [3, 3, 4, 2, 0]
  # [1, 3, 4, 2, 0]
  ```

  