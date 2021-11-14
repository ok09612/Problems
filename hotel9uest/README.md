/*
  Fizz Buzz
 */
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


/*
  Split a String Into the Max Number of Unique Substrings
  "wwwzfvedwfvhsww" < 여기서 막혔습니다 ㅠㅠ
 */
public class Solution {
    public int MaxUniqueSplit(string s) {
        List<string> lstChars = new List<string>();
        string currentTarget = string.Empty;
        
        for (int i=0; i<s.Length; i++)
        {
            currentTarget += s[i];
            
            if (i != s.Length - 1 && lstChars.Contains(s.Substring(i + 1)))
                continue;
            
            if (lstChars.Contains(currentTarget))
                continue;
            
            lstChars.Add(currentTarget);
            currentTarget = string.Empty;
        }
        
        return lstChars.Count;
    }
}