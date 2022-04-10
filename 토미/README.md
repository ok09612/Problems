# Problems

https://leetcode.com/problems/first-unique-character-in-a-string/

``` C#
public class Solution
{
    public int FirstUniqChar(string s)
    {
        var increasement = new int[26];

        for (int i = 0; i < s.Length; i++)
        {
            increasement[s[i] - 'a']++;
        }

        for (int i = 0; i < s.Length; i++)
        {
            if (increasement[s[i] - 'a'] == 1)
            {
                return i;
            }
        }

        return -1;
    }
}

public class Solution
{
    public int FirstUniqChar(string s)
    {
        var increasement = new Dictionary<char, int>();
        var indices = new Dictionary<char, int>();

        for (int i = 0; i < s.Length; i++)
        {
            if (!increasement.TryGetValue(s[i], out var value))
            {
                increasement.Add(s[i], 0);
                indices.Add(s[i], i);
            }

            increasement[s[i]]++;
        }

        var first = increasement.FirstOrDefault(x => x.Value == 1);

        return first.Key == default(char) ? -1 :indices[first.Key];
    }
}
```

https://leetcode.com/problems/excel-sheet-column-title/

``` C#
public class Solution
{
    public string ConvertToTitle(int columnNumber)
    {
        var sb = new StringBuilder();
        var stack = new Stack<char>();
        while (columnNumber > 0)
        {
            var remain = columnNumber % 26;
            columnNumber--;
            columnNumber /= 26;

            stack.Push(remain == 0 ? 'Z' : (char)(remain + 64));
        }

        while (stack.Count > 0)
        {
            sb.Append(stack.Pop());
        }

        return sb.ToString();
    }
}
```