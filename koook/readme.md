https://programmers.co.kr/learn/courses/30/lessons/12945
피보나치의 수
'''
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

    
    
    
  '''
