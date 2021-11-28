- https://leetcode.com/problems/generate-parentheses/
- 시간복잡도 O(N^2)
```c#
public class Solution
{
    public IList<string> GenerateParenthesis(int n)
    {
        var parenthesis = new List<string>();
        var st = new Stack<(string bracket, int top)>();
        var length = n * 2;
        st.Push(("(", 1));
        while (st.Count > 0)
        {
            var (bracket, top) = st.Pop();
            if (top < 0) {
                continue;
            }
            if (bracket.Length == length)
            {
                if (top == 0)
                {
                    parenthesis.Add(bracket);
                }
                continue;
            }
            st.Push((bracket + "(", top + 1));
            st.Push((bracket + ")", top - 1));
        }
        return parenthesis;
    }
}
```

- https://programmers.co.kr/learn/courses/30/lessons/42898
- 등굣길
- 시간복잡도 O(NM + P)
```c++
#include <string>
#include <vector>
#include <set>
using namespace std;
const int MOD = 1000000007;

int solution(int m, int n, vector<vector<int>> puddles) {
    int cache[101][101] = {1};
    set<pair<int, int>> puddlesSet;
    for(auto puddle: puddles) {
        puddlesSet.insert({ puddle[0] - 1, puddle[1] - 1});
    }
    for(int i = 0; i < m; i++) {
        for(int j = 0; j < n;j++) {
            if (puddlesSet.find({ i, j }) != puddlesSet.end()) {
                continue;
            }
            if (i - 1 >= 0) cache[i][j] = (cache[i][j] + cache[i-1][j]) % MOD;
            if (j - 1 >= 0) cache[i][j] = (cache[i][j] + cache[i][j-1]) % MOD;
        }
    }
    return cache[m-1][n-1];
}
```
