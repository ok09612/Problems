# 1528. Shuffle String
# https://leetcode.com/problems/shuffle-string/

```python
class Solution:
    def restoreString(self, s: str, indices: List[int]) -> str:
        
        words = []
        
        # 문자와 대응되는 숫자를 배열로 저장 : [숫자, 문자]
        for i in range(len(s)):
            words.append([indices[i], s[i]])
            
        # 배열을 정렬
        words.sort()
        
        result = ''
        
        # 정렬된 배열의 문자를 결과 문자열로 생성
        for i in range(len(words)):
            result += words[i][1]
            
        return result
```

# 1791. Find Center of Star Graph
# https://leetcode.com/problems/find-center-of-star-graph/

```python
class Solution:
    def findCenter(self, edges: List[List[int]]) -> int:
        
        dict = {}
        
        # 각 노드의 번호를 딕셔너리에 저장
        for i in range(0, 2):
            star = edges[i]
            
            if star[0] in dict:
                dict[star[0]] += 1
            else:
                dict[star[0]] = 1
            if star[1] in dict:
                dict[star[1]] += 1
            else:
                dict[star[1]] = 1
        
        max_num = 0
        max_value = 0
        
        # 저장된 딕셔너리의 가장 큰 수를 찾음
        for num in dict:
            if max_value < dict[num]:
                max_value = dict[num]
                max_num = num
        
        return max_num
```