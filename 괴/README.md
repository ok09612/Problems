# 숫자 문자열과 영단어
https://programmers.co.kr/learn/courses/30/lessons/81301

```python
def solution(s):
        
    dict = {}
    
    dict["zero"] = 0
    dict["one"] = 1
    dict["two"] = 2
    dict["three"] = 3
    dict["four"] = 4
    dict["five"] = 5
    dict["six"] = 6
    dict["seven"] = 7
    dict["eight"] = 8
    dict["nine"] = 9
    
    result = ""
    word = ""
    
    for char in s:
        if char.isdigit():
            result += str(char)
        else:
            word += char
            
            if word in dict:
                result += str(dict[word])
                word = ""
    
    return int(result)
```

# 로또의 최고 순위와 최저 순위
https://programmers.co.kr/learn/courses/30/lessons/77484

```python
def solution(lottos, win_nums):
    
    dict = {}
    
    dict[6] = 1
    dict[5] = 2
    dict[4] = 3
    dict[3] = 4
    dict[2] = 5
    dict[1] = 6
    dict[0] = 6
    
    answer = []
    max = 0
    min = 0
    
    for lotto in lottos:
        
        if lotto == 0:
            max += 1
        elif lotto in win_nums:
            max += 1
            min += 1
    
    answer.append(dict[max])
    answer.append(dict[min])
    
    return answer
```