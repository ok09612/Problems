
'''
https://programmers.co.kr/learn/courses/30/lessons/12945
피보나치의 수

python



def solution(n):
    answer = 0
    enum = 0
    fibo_t0 = 0
    fibo_t1 = 1
    fibo_t2= 0
    temp = 0
    while enum < n-1:
        enum +=1
        fibo_t2 = fibo_t1 + fibo_t0
        fibo_t0 = fibo_t1
        fibo_t1 = fibo_t2
    answer = fibo_t2%1234567
    return answer



    
    
    
  https://programmers.co.kr/learn/courses/30/lessons/12941
    최소값 만들기

    python
    
    def solution(A,B):
    answer = 0
    #최소값을 구하려면 A의 최소값들 * B의 최대값순
    A.sort()
    B.sort(reverse = True)
    
    #간단하게 각 원소들 뽑아서 곱해주면 끝
    #이게 왜 Level2?
    for i, j in zip(A,B):
        answer += i*j

    return answer
    
    
    '''

    
  '''
