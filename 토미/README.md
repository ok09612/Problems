# Problems

https://leetcode.com/problems/implement-stack-using-queues/

``` C#
public class MyStack
{
    Queue<int> leftQueue = new Queue<int>();
    Queue<int> rightQueue = new Queue<int>();

    public MyStack()
    {

    }

    public void Push(int x)
    {
        rightQueue.Enqueue(x);
    } 

    public int Pop()
    {
        Spin(leftQueue, rightQueue, 1);

        var value = rightQueue.Dequeue();

        Spin(rightQueue, leftQueue, 0);

        return value;
    }

    public int Top()
    {
        Spin(leftQueue, rightQueue, 1);

        var top = rightQueue.Peek();

        Spin(leftQueue, rightQueue, 0);
        Spin(rightQueue, leftQueue, 0);

        return top;
    }

    private void Spin(Queue<int> op1 , Queue<int> op2, int remainCount)
    {
        while (op2.Count > remainCount)
        {
            op1.Enqueue(op2.Dequeue());
        }
    }

    public bool Empty()
    {
        return rightQueue.Count == 0 ? true : false;
    }
}

```

https://leetcode.com/problems/max-number-of-k-sum-pairs/

``` C#
public class Solution
{
    public int MaxOperations(int[] nums, int k)
    {
        var result = 0;
        Array.Sort(nums);

        var left = 0;
        var right = nums.Length - 1;

        while (right > left)
        {
            var sum = nums[right] + nums[left];

            if (sum == k)
            {
                result++;
                right--;
                left++;
            }
            else if(sum > k)
            {
                right--;
            }
            else
            {
                left++;
            }
        }

        return result;
    }
}
```