https://leetcode.com/problems/powx-n/

```python3
class Solution:
    def myPow(self, x: float, n: int) -> float:
        x = x ** n
        
        return x
```

https://leetcode.com/problems/baseball-game/

```python3
class Solution:
    def calPoints(self, ops: List[str]) -> int:
        
        result = []
        
        for op in ops:
            if op == "+":
                result.append(result[-2]+result[-1])
            elif op == "D":
                result.append(result[-1]*2)
            elif op == "C":
                result.pop()
            else:
                result.append(int(op))
                
        return sum(result)
```
