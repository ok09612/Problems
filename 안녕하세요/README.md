- 1593. Split a String Into the Max Number of Unique Substrings
```c#
// O(2^N) ???
using System;
using System.Collections.Generic;
using System.Text;
public class Solution
{
    private HashSet<string> _set = new HashSet<string>();
    private int _answer = 0;
    private void Split(string s, int cur)
    {
        if (cur >= s.Length)
        {
            _answer = Math.Max(_answer, _set.Count);
            return;
        }

        var str = new StringBuilder();
        for (int i = cur; i < s.Length; i++)
        {
            str.Append(s[i]);
            var next = str.ToString();
            if (_set.Contains(next) == false)
            {
                _set.Add(next);
                Split(s, i + 1);
                _set.Remove(next);
            }
        }
    }
    public int MaxUniqueSplit(string s)
    {
        Split(s, 0);
        return _answer;
    }
}
```

- fizz buzz
```c#
public class Solution {
    public IList<string> FizzBuzz(int n) {
        var answer = new List<string>();
        for(int i = 1; i <= n; i++) {
            if (i % 3 == 0 && i % 5 == 0) {
                answer.Add("FizzBuzz");
            } else if (i % 3 == 0) {
                answer.Add("Fizz");
            } else if (i % 5 == 0) {
                answer.Add("Buzz");
            } else {
                answer.Add(i.ToString());
            }
        }
        return answer;
    }
}
```
