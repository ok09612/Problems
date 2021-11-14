# Fizz Buzz

``` c#
public class Solution {
    public IList<string> FizzBuzz(int n) {
        List<string> lst = new List<string>();

        for (int i = 1; i <= n; i++)
        {
            string result;

            if (i % 3 == 0 && i % 5 == 0)
                result = "FizzBuzz";
            else if (i % 3 == 0)
                result = "Fizz";
            else if (i % 5 == 0)
                result = "Buzz";
            else
                result = i.ToString();
            
            lst.Add(result);
        }
        
        return lst;
    }
}
```

# Split a String Into the Max Number of Unique Substrings
- 못 풀겠어서.. 열심히 삽질한 코드만 올립니다.. ㅠㅠ

```c#
public class Solution {
    public static int MaxUniqueSplit(string s)
    {
        List<KeyValuePair<int, List<string>>> lst = new List<KeyValuePair<int, List<string>>>();

        for (int i=0; i<s.Length; i++)
            lst.Add(GetMaxUniqueSplit(s, i));

        return lst.Max(x => x.Value.Count);
    }

    public static KeyValuePair<int, List<string>> GetMaxUniqueSplit(string s, int index)
    {
        List<string> lstChars = new List<string>();
        string currentTarget = string.Empty;
        int lastIndex = index - 1;

        for (int i=0; i<s.Length; i++)
        {
            int currentIndex = i + index;

            if (currentIndex >= s.Length)
                currentIndex %= s.Length;

            currentTarget += s[currentIndex];

            if (currentIndex != s.Length - 1 && lstChars.Contains(s.Substring(currentIndex + 1)))
                continue;

            if (index > 0 && currentIndex != index - 1)
            {
                int startIndex = currentIndex > lastIndex ? 0 : currentIndex + 1;

                if (startIndex != lastIndex && lstChars.Contains(s.Substring(startIndex, lastIndex - startIndex - 1)))
                    continue;
            }

            if (lstChars.Contains(currentTarget))
                continue;

            lstChars.Add(currentTarget);
            currentTarget = string.Empty;
        }

        return new KeyValuePair<int, List<string>>(index, lstChars);
    }
}
```