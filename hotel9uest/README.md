# Generate Parentheses
- https://leetcode.com/problems/generate-parentheses/

```c#
public class Solution {
    public IList<string> GenerateParenthesis(int n) {
        List<string> lst = new List<string>();

        dfs("(", n, ref lst);

        return lst;
    }

    void dfs(string currentString, int n, ref List<string> lst)
    {
        if (!IsValid(currentString, n))
            return;

        if (currentString.Length == n * 2)
        {
            lst.Add(currentString);
            return;
        }

        dfs(currentString + "(", n, ref lst);
        dfs(currentString + ")", n, ref lst);
    }

    bool IsValid(string currentString, int n)
    {
        int left = 0, right = 0;

        for (int i=0; i<currentString.Length; i++)
        {
            if (currentString[i] == '(')
                left++;
            else if (currentString[i] == ')')
                right++;

            if (left < right)
                return false;
        }

        if (left > n || right > n)
            return false;

        if (currentString.Length == n * 2 && left != right)
            return false;

        return true;
    }
}
```
