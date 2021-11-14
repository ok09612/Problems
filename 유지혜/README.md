# Uniqe string
public class Solution {
    public int MaxUniqueSplit(string s) {
        List<string> list = new List<string>();
        for(int i=0;i<s.Length;i++)
        {
            if(list.Exists(x => x == s.Substring(i, 1)))
            {
                if (i == s.Length-1)
                {
                    break;
                }

                if (!list.Exists(x => x == s.Substring(i, 2)))
                {
                    list.Add(s.Substring(i, 2));
                    i += 1;
                }
            }
            else
            {
                list.Add(s.Substring(i, 1));
            }
        }

        return list.Count;
    }
}

# FizzBuzz
public class Solution {
    public IList<string> FizzBuzz(int n) {        
        List<string> result  = new List<string>();
        
        for(int i=1;i<=n;i++)
        {
            string s = "";
            if (i%3 == 0)
            {
                s = "Fizz";
            }
            
            if (i%5== 0)
            {
                s += "Buzz";
            }
            
            if (s.Length == 0)
            {
                s = i.ToString();
            }
            
            result.Add(s);
        }
        
        return result;
    }
}