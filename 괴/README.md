# 2181. Merge Nodes in Between Zeros
# https://leetcode.com/problems/merge-nodes-in-between-zeros/

```C#
public class Solution {
    public ListNode MergeNodes(ListNode head) {
        
        var dummy = new ListNode(0);
        var result = dummy;
        
        var sum = 0;
        
        while (head != null)
        {
            var val = Convert.ToInt32(head.val);
            
            if (val > 0) {
                sum += val;  
            } else {
                if (sum > 0)
                {
                    result.next = new ListNode(sum);
                    result = result.next;
                    
                }
                sum = 0;
            } 
            
            head = head.next;
        }
        
        return dummy.next;
    }
}
```

# 43. Multiply Strings
# https://leetcode.com/problems/multiply-strings/

```C#
public class Solution {
    public string Multiply(string num1, string num2) {
        return (BigInteger.Parse(num1) * BigInteger.Parse(num2)).ToString();
    }
}
```