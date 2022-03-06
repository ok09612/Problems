- 1028. Recover a Tree From Preorder Traversal O(N)
```c#
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left;
 *     public TreeNode right;
 *     public TreeNode(int val=0, TreeNode left=null, TreeNode right=null) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
public class Solution
{
    private int GetLevel(string traversal,ref int cur)
    {
        int count = 0;
        while (traversal[cur] == '-')
        {
            count++;
            cur++;
        }
        return count;
    }

    private int GetNumber(string traversal, ref int cur)
    {
        int number = 0;
        while (cur < traversal.Length && traversal[cur] != '-')
        {
            number = number * 10 + (traversal[cur] - '0');
            cur++;
        }
        return number;
    }

    public TreeNode RecoverFromPreorder(string traversal)
    {
        int idx = 0;
        var number = GetNumber(traversal,ref idx);
        var root = new TreeNode(number);
        Stack<(TreeNode Cur, int Level)> stack = new();
        stack.Push((root, 0));
        
        while (stack.Count > 0 && idx < traversal.Length)
        {
            var (cur, level) = stack.Peek();

            var nextLevel = GetLevel(traversal, ref idx);
            number = GetNumber(traversal, ref idx);

            var nextNode = new TreeNode(number);
            if (level + 1 == nextLevel)
            {
                cur.left = nextNode;
            } else
            {
                while (stack.Peek().Level + 1 != nextLevel)
                {
                    stack.Pop();
                }
                (cur, level) = stack.Peek();
                cur.right = nextNode;
            }

            stack.Push((nextNode, nextLevel));
        }

        return root;
    }
}
```

- 1342. Number of Steps to Reduce a Number to Zero O(log N)
```c#
public class Solution {
    public int NumberOfSteps(int num) {
        int answer = 0;
        while (num > 0) 
        {
            if (num % 2 == 0) {
                num /= 2;
            } else {
                num--;
            }
            answer++;
        }
        return answer;
    }
}
```

- 1116. Print Zero Even Odd, (Busy Waiting)
```c#
public class ZeroEvenOdd
{
    private int n;
    private int _printOrder;
    public ZeroEvenOdd(int n)
    {
        _printOrder = 0;
        this.n = n;
    }

    private object _printLock = new();

    private void Increase()
        => _printOrder = (_printOrder + 1) % 4;

    private void Wait(Action action, params int[] target)
    {
        while (true)
        {
            lock(_printLock)
            {
                if (target.Contains(_printOrder))
                {
                    action();
                    break;
                }
            }
        }
    }

    // printNumber(x) outputs "x", where x is an integer.
    public void Zero(Action<int> printNumber)
    {
        for (int i = 0; i < n; i++)
        {
            Wait(() => {
                printNumber(0);
                Increase();
            }, 0, 2);
        }
    }

    public void Even(Action<int> printNumber)
    {
        for (int i = 1; i <= n; i++)
        {
            if (i % 2 == 0)
            {
                Wait(() => {
                    printNumber(i);
                    Increase();
                },3);
            }
        }
    }

    public void Odd(Action<int> printNumber)
    {
        for (int i = 1; i <= n; i++)
        {
            if (i % 2 != 0)
            {
                Wait(() => {
                    printNumber(i);
                    Increase();
                }, 1);
            }
        }
    }
}
```
