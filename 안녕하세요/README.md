```c#
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
public class Solution
{
    private ListNode? Partition(ListNode? node)
    {
        if (node?.next == null)
        {
            return node;
        }

        ListNode? temp = null;
        var slow = node;
        var fast = node;

        while (fast?.next != null)
        {
            temp = slow;
            slow = slow.next;
            fast = fast?.next?.next;
        }
        
        if (temp!= null) {
            temp.next = null;
        }

        var left = Partition(node);
        var middle = Partition(slow);

        var result = new ListNode(0, null);
        var answer = result;


        while(left != null && middle != null)
        {
            if (left.val < middle.val)
            {
                result.next = left;
                left = left.next;
            } else
            {
                result.next = middle;
                middle = middle.next;
            }
            result = result.next;
        }

        if(left != null)
        {
            result.next = left;
        }

        if(middle != null)
        {
            result.next = middle;
        }

        return answer.next;
    }

    public ListNode SortList(ListNode head)
    {
        return Partition(head);
    }
}
```
