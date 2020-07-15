## N으로 표현

#### 동적계획법 

1. 첫번째

   - 예제 다 맞고, 42.9나옴
   - 중간에 0, 1 등 . 이런 거 들어가서 result.append(i*10)웅앵 때문에 틀림

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
               result.append(i*10 +i)
           tmp=result
           
           answer +=1
           if number in result:
               return answer
       return -1
   ```

   2. 두번째
      - 이거는 진짜 모르겠어서 인터넷 봄.. 이해한 거 설명. 

   ```python
   def solution(N, number):
       possible_set = [0,[N]] # 조합으로 나올수 있는 가능한 숫자들, 여기에 계속 추가하고 계산한다함.
       if N == number: #처음부터 숫자랑 찾는 거랑 같으면 1 출력(1개 사용)
           return 1
       
       for i in range(2, 9): # 2(55시작)부터 8(55555555)까지 과정 8 이상이면 return -1 나옴. 
           case_set = [] # 임시로 사용할 케이스 셋, 각 I 별로 셋을 만들어 possible set에 붙인다.
           basic_num = int(str(N)*i) # 같은 숫자 반복되는 거 ex 55, 555 이런 거 str 으로 붙이고 int 형으로 변환시킨 거 넣는 변수.
           # 계산을 위해서 값 넣어줌 
           case_set.append(basic_num)
           for i_half in range(1, i//2+1): # 사용되는 숫자의 횟수를 구해야 하는데, 
           # 절반 이상으로 넘어가면 계속 특정 수로 계산하니까 앞의 경우 결과만 나올 뿐이므로 절반까지만을 사용한다. 
           	#  값과 뒤에 경우의 수 값에 대한 사칙연산을 함
               # ex. [0, [5], [55, 10, 0, 0, 25, 1.0, 1.0], [555, 60, -50, 50, 275, 0.09090909090909091, 11.0, 15, -5, 5, 50, .....]]
               for x in possible_set[i_half]:
                   for y in possible_set[i-i_half]: # x와 y를 더하면 i 가 되도록 만든 수다. 
                       case_set.append(x+y)# 각 사칙연산
                       case_set.append(x-y)
                       case_set.append(y-x)
                       case_set.append(x*y)
                       # 나누는 거 0 아니여야해서 조건식 만듦
                       if y !=0:
                           case_set.append(x/y)
                       if x !=0:
                           case_set.append(y/x)
               # case set에 그 값( 5, 55,555,...) 에 대한 사칙연산 값이 들어감
               # 그 안에 찾는 값이 있을 경우 i(N이 사용된 수) 출력
               if number in case_set:
                   return i
               possible_set.append(case_set) # 최종 결과물 set에 사칙 연산 결과 모두 추가 
       return -1 # number로 만드는 과정이  8이 넘으면  -1을 출력.
   ```

   