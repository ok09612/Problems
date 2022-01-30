# 66. Plus One
https://leetcode.com/problems/plus-one/

```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        
        num = ''
        
        for i in digits:
            num += str(i)
        
        num = int(num) + 1
        
        result = []
        
        for i in str(num):
            result.append(i)
            
        return result
```

# 414. Third Maximum Number (번외)
https://leetcode.com/problems/third-maximum-number/

```python
class Solution:
    def thirdMax(self, nums: List[int]) -> int:
        
        result = sorted(set(nums), reverse=True)
        
        if len(result) < 3:
            return result[0]
        else:
            return result[2]
```