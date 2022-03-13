- merge-nodes-in-between-zeros
```C#
public class Solution {
    public ListNode MergeNodes(ListNode head) {
        var cur = head;
        var sum = 0;
        ListNode answerCur = null;
        ListNode answer = null;
        while (cur != null) {
            if (cur.val == 0 && sum > 0) {
                if (answer == null) {
                    answer = new ListNode(sum);
                    answerCur = answer;
                } else {
                    answerCur.next = new ListNode(sum);
                    answerCur = answerCur.next;
                }
                sum = 0;
            } else {
                sum+= cur.val;
                cur = cur.next;
            }
        }
        return answer;
    }
}
```

- Multiply Strings
```c#
public class Solution
{
    public string Multiply(string num1, string num2)
    {
        var a = BigInteger.Parse(num1);
        var b = BigInteger.Parse(num2);

        var answer = BigInteger.Multiply(a, b);

        return answer.ToString();
    }
}
```
