- Deepest Leave Sum (O(N))
```c#
public class Solution
{
    private void Travel(TreeNode root, Action<TreeNode, int> action)
    {
        Queue<(TreeNode, int level)> que = new();
        que.Enqueue((root, 1));
        while (que.Count > 0)
        {
            var (cur, level) = que.Dequeue();
            if (cur.left is null && cur.right is null)
            {
                action(cur, level);
            }
            if (cur.left != null)
            {
                que.Enqueue((cur.left, level + 1));
            }
            if (cur.right != null)
            {
                que.Enqueue((cur.right, level + 1));
            }
        }
    }
    public int DeepestLeavesSum(TreeNode root)
    {
        int sum = 0;
        int treeLevel = 1;
        Travel(root, (node, level) =>
        {
            treeLevel = Math.Max(treeLevel, level);
        });

        Travel(root, (node, level) =>
        {
            if (level == treeLevel)
            {
                sum += node.val;
            }
        });

        return sum;
    }
}
```

- permutations-ii O(n!)
