# Merge Nodes in Between Zeros (2181)
### O(N)

```C#

/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public int val;
 *     public ListNode next;
 *     public ListNode(int val=0, ListNode next=null) {
 *         this.val = val;
 *         this.next = next;
 *     }
 * }
 */
public class Solution {
    public ListNode MergeNodes(ListNode head) {
        ListNode tempNode = new ListNode();
        ListNode result = tempNode;
        int sum = 0;
        
        while (head.next != null) {
            head = head.next;
            sum = 0;
            
            while (head.val != 0) {
                sum += head.val;
                head = head.next;
            }
            
            tempNode.next = new ListNode(sum);
            tempNode = tempNode.next;
        }
        
        return result.next;
    }
}

```

# Multiply Strings (43)
### O(1)

```C#

public class Solution {
    public string Multiply(string num1, string num2) {
        return (BigInteger.Parse(num1) * BigInteger.Parse(num2)).ToString();
    }
}

```
