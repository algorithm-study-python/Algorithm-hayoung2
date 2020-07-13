## N으로 표현

#### 동적계획법 

1. 첫번째

   - 예제 다 맞고, 42.9나옴
   - 어디가 틀린 지 알겠는데 자꾸 안된다네..저거 주석해 놓은 곳..일단 보류

   ```python
   def solution(N, number):
       answer = 0
       tmp=[N]
       
       while answer<9 :
           result =[]
           for i in tmp :
               result.append(i-N)
               result.append(i+N)
               result.append(i/N)
               result.append(i*N)
               # temp=str(i)+str(N)
               # result.append(int(temp))
           tmp=result
           
           answer +=1
           if number in result:
               return answer
       return -1
   ```

   