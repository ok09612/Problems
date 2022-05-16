https://programmers.co.kr/learn/courses/30/lessons/42584
주식 가격
'''
python

def solution(prices):
    answer = []
    for i in range(len(prices)):
        flag = 0
        for j in range(i+1,len(prices)):
            if(prices[j] -prices[i])>=0:
                pass
            else:
                answer.append(j-i)
                flag = 1
                break
        if flag == 0:
            answer.append(len(prices)-i-1)
    return answer
'''
