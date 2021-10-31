```c#
using System.Text;

public class Solution
{
    public string DecodeString(string s)
    {
        var str = new StringBuilder();
        var cur = 0;
        while (cur < s.Length)
        {
            if (char.IsLetter(s[cur]))
            {
                str.Append(s[cur]);
                cur++;
            }
            else
            {
                int bracketStart = cur;
                while (char.IsNumber(s[bracketStart])) bracketStart++;
                int repeatCount = int.Parse(s[cur..bracketStart]);

                int top = 1;
                int bracketEnd = bracketStart + 1;
                while (top > 0)
                {
                    if (s[bracketEnd] == '[') top++;
                    else if (s[bracketEnd] == ']') top--;
                    bracketEnd++;
                }
                bracketEnd--;
                var subStr = DecodeString(s[(bracketStart + 1)..bracketEnd]);
                while (repeatCount-- > 0)
                {
                    str.Append(subStr);
                }
                cur = bracketEnd + 1;
            }
        }
        return str.ToString();
    }
}
```

