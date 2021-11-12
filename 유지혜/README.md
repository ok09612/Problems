# Uniqe string


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