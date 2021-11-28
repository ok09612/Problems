# Problems

https://leetcode.com/problems/generate-parentheses/

``` Python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        dp=[[] for i in range(n+1)]
        dp[0].append('')
        for i in range(n+1):
            for j in range(i):
                dp[i]+=['('+ inner + ')' + outer for inner in dp[j] for outer in dp[i-j-1]]
        return dp[n]
```

https://programmers.co.kr/learn/courses/30/lessons/42898

```
def solution(m, n, puddles):
    dp = [[0] * m for _ in range(n)]
    dp[0][0] = 1
    
    if puddles:
        for i in puddles:
            dp[i[1] - 1][i[0] - 1] = -1
            
    for i in range(1, m):
        dp[0][i] = 0 if dp[0][i] == -1 else dp[0][i - 1]
    for i in range(1, n):
        dp[i][0] = 0 if dp[i][0] == -1 else dp[i - 1][0]
        
    for i in range(1, n):
        for j in range(1, m):
            
            if dp[i][j] == -1:
                dp[i][j] = 0
            else:
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1] % 1000000007
                
    return dp[n - 1][m - 1]
    ```
        
