'''
Python
프로그래머스 
https://programmers.co.kr/learn/courses/30/lessons/67256

스마트폰 전화 키패드의 각 칸에 다음과 같이 숫자들이 적혀 있습니다.

kakao_phone1.png

이 전화 키패드에서 왼손과 오른손의 엄지손가락만을 이용해서 숫자만을 입력하려고 합니다.
맨 처음 왼손 엄지손가락은 * 키패드에 오른손 엄지손가락은 # 키패드 위치에서 시작하며, 엄지손가락을 사용하는 규칙은 다음과 같습니다.

엄지손가락은 상하좌우 4가지 방향으로만 이동할 수 있으며 키패드 이동 한 칸은 거리로 1에 해당합니다.
왼쪽 열의 3개의 숫자 1, 4, 7을 입력할 때는 왼손 엄지손가락을 사용합니다.
오른쪽 열의 3개의 숫자 3, 6, 9를 입력할 때는 오른손 엄지손가락을 사용합니다.
가운데 열의 4개의 숫자 2, 5, 8, 0을 입력할 때는 두 엄지손가락의 현재 키패드의 위치에서 더 가까운 엄지손가락을 사용합니다.
4-1. 만약 두 엄지손가락의 거리가 같다면, 오른손잡이는 오른손 엄지손가락, 왼손잡이는 왼손 엄지손가락을 사용합니다.
순서대로 누를 번호가 담긴 배열 numbers, 왼손잡이인지 오른손잡이인 지를 나타내는 문자열 hand가 매개변수로 주어질 때, 각 번호를 누른 엄지손가락이 왼손인 지 오른손인 지를 나타내는 연속된 문자열 형태로 return 하도록 solution 함수를 완성해주세요.

[제한사항]
numbers 배열의 크기는 1 이상 1,000 이하입니다.
numbers 배열 원소의 값은 0 이상 9 이하인 정수입니다.
hand는 "left" 또는 "right" 입니다.
"left"는 왼손잡이, "right"는 오른손잡이를 의미합니다.
왼손 엄지손가락을 사용한 경우는 L, 오른손 엄지손가락을 사용한 경우는 R을 순서대로 이어붙여 문자열 형태로 return 해주세요.



def solution(numbers, hand):
    answer = ''
    dicLeftRightDescret = {"1":"L", "4":"L", "7":"L","3":"R", "6":"R", "9":"R"
                          ,"2":"C","5":"C","8":"C","0":"C"}
    iLeft = '*'
    iRight = '#'
    lKeypad = [["1","4","7","*"],["2","5","8","0"],["3","6","9","#"]]
    lLeftPosition = [0,3]
    lRightPosition = [2,3]
    lCenterPosotion = [0,0]
    
    for i in numbers:
        cCheck = dicLeftRightDescret[str(i)]
        if cCheck == "L":
            answer += "L"
            lLeftPosition = [0, lKeypad[0].index(str(i))]

            iLeft = str(i)
        elif cCheck == "R":
            answer += "R"
            lRightPosition= [2, lKeypad[2].index(str(i))]
            iRight = str(i)
        elif cCheck == "C":
            lCenterPosotion = [1,lKeypad[1].index(str(i))]

            
            iLeftMoveCount = abs(lLeftPosition[0] - lCenterPosotion[0]) + abs(lLeftPosition[1] - lCenterPosotion[1])
            iRightMoveCount = abs(lRightPosition[0] - lCenterPosotion[0]) + abs(lRightPosition[1] - lCenterPosotion[1])
            print("Left move count = {0} and Right move count = {1}".format(iLeftMoveCount, iRightMoveCount))
            if(iLeftMoveCount > iRightMoveCount):
                answer += "R"
                iRight = str(i)
                lRightPosition= [1, lKeypad[1].index(str(i))]
            elif(iLeftMoveCount < iRightMoveCount):
                answer += "L"
                iLeft = str(i)
                lLeftPosition= [1, lKeypad[1].index(str(i))]
            else:
                if(hand == "right"):
                    answer += "R"
                    iRight = str(i)
                    lRightPosition= [1, lKeypad[1].index(str(i))]
                else:
                    answer += "L"
                    iLeft = str(i)
                    lLeftPosition= [1, lKeypad[1].index(str(i))]
                
                
            
            
            
        
    return answer
    
    
    
    
    체육복
    
    점심시간에 도둑이 들어, 일부 학생이 체육복을 도난당했습니다. 다행히 여벌 체육복이 있는 학생이 이들에게 체육복을 빌려주려 합니다. 학생들의 번호는 체격 순으로 매겨져 있어, 바로 앞번호의 학생이나 바로 뒷번호의 학생에게만 체육복을 빌려줄 수 있습니다. 예를 들어, 4번 학생은 3번 학생이나 5번 학생에게만 체육복을 빌려줄 수 있습니다. 체육복이 없으면 수업을 들을 수 없기 때문에 체육복을 적절히 빌려 최대한 많은 학생이 체육수업을 들어야 합니다.

전체 학생의 수 n, 체육복을 도난당한 학생들의 번호가 담긴 배열 lost, 여벌의 체육복을 가져온 학생들의 번호가 담긴 배열 reserve가 매개변수로 주어질 때, 체육수업을 들을 수 있는 학생의 최댓값을 return 하도록 solution 함수를 작성해주세요.

제한사항
전체 학생의 수는 2명 이상 30명 이하입니다.
체육복을 도난당한 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
여벌의 체육복을 가져온 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
여벌 체육복이 있는 학생만 다른 학생에게 체육복을 빌려줄 수 있습니다.
여벌 체육복을 가져온 학생이 체육복을 도난당했을 수 있습니다. 이때 이 학생은 체육복을 하나만 도난당했다고 가정하며, 남은 체육복이 하나이기에 다른 학생에게는 체육복을 빌려줄 수 없습니다.
입출력 예
n	lost	reserve	return
5	[2, 4]	[1, 3, 5]	5
5	[2, 4]	[3]	4
3	[3]	[1]	2
    
    


def solution(n, lost, reserve):
    answer = 0
    '''
    1. 역순이 있을 수 있으니까 reserve랑 lost를 먼저 sort 해준다.
    2. 중복 제거를 먼저 해준다.
    3. reserve의 각 원소별로 먼저  -1, +1을 순서대로 해서 
    그 번호가 lost에 있으면 해당 되는 lost와 reserve에서 remove 해준다.
    (서로 짝지어줌)
    4. 이렇게 쭉 진행해서 로스트에 몇이 남았는지 세어서 n에서 빼주면 return이 된다.
    '''
    iLost_num = 0;
    reserve.sort()
    lost.sort()
    check = reserve.copy()
    
    for i in check:
        if(i in lost):
            reserve.remove(i)
            lost.remove(i)
    for i in range(len(reserve)):
        j = reserve[i- iLost_num]
        if(j-1 in lost):
            reserve.remove(j)
            lost.remove(j-1)
            iLost_num+=1
        elif(j+1 in lost):
            reserve.remove(j)
            lost.remove(j+1)
            iLost_num+=1

    
    answer = n - len(lost)
    
    
    return answer
    
 

'''
