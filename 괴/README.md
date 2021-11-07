# 56. Merge Intervals
https://leetcode.com/problems/merge-intervals/

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        
        result = []
        
        if (len(intervals) <= 1):
            return intervals
        
        intervals.sort()
        
        result.append(intervals[0])
        
        for i in range(1, len(intervals)):
            
            if (result[len(result)-1][1] >= intervals[i][0]):
                if (result[len(result)-1][1] < intervals[i][1]):
                    result[len(result)-1] = [result[len(result)-1][0], intervals[i][1]]
            else:
                result.append(intervals[i])
        
        return result
```
