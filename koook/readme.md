완주하지 못 한 선수
https://programmers.co.kr/learn/courses/30/lessons/42576

'''
python


def solution(participant, completion):
    answer = ''
    participant.sort()
    completion.sort()
    flag = 0
    for i in range(len(completion)):
        if(participant[i] == completion[i]):
            pass
        else:
            answer = participant[i]
            flag = 1
            break
            
    if(flag != 1):
        answer = participant[-1]
    return answer
'''
