# 412. Fizz Buzz
https://leetcode.com/problems/fizz-buzz/

```python
class Solution:
    def fizzBuzz(self, n: int) -> List[str]:

        result = []
        
        for n in range(1, n+1):
            
            # print(n)
            
            if n % (3*5) == 0:
                result.append("FizzBuzz")
            elif n % 5 == 0:
                result.append("Buzz")
            elif n % 3 == 0:
                result.append("Fizz")
            else:
                result.append(str(n))
                
        
        return result
```

# 1791. Find Center of Star Graph (선택)
https://leetcode.com/problems/find-center-of-star-graph/
```python
class Solution:
    def findCenter(self, edges: List[List[int]]) -> int:
        
        dict = {}
        
        for star in edges:
            
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
        
        for num in dict:
            
            if max_value < dict[num]:
                max_value = dict[num]
                max_num = num
        
        return max_num
        

```