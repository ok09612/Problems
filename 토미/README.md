# Problems

https://leetcode.com/problems/deepest-leaves-sum/

``` C#
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
	public int DeepestLeavesSum(TreeNode root)
	{
		var deepestIndex = 0;

		SetDeepestIndex(root, ref deepestIndex, 0);

		var sum = 0;

		SumDeepestValues(root, ref sum, 0, deepestIndex);

		return sum;
	}

	private void SumDeepestValues(TreeNode node, ref int sum, int currentIndex, int deepestIndex)
	{
		if (node == null)
		{
			return;
		}

		if (currentIndex == deepestIndex)
		{
			sum += node.val;

			return;
		}

		if (currentIndex < deepestIndex)
		{
			SumDeepestValues(node.left, ref sum, currentIndex + 1, deepestIndex);
			SumDeepestValues(node.right, ref sum, currentIndex + 1, deepestIndex);
		}

		return;
	}

	private void SetDeepestIndex(TreeNode node, ref int deepestIndex, int currentIndex)
	{
		if (deepestIndex < currentIndex)
		{
			deepestIndex = currentIndex;
		}

		if (node.left != null)
		{
			SetDeepestIndex(node.left, ref deepestIndex, currentIndex + 1);
		}

		if (node.right != null)
		{
			SetDeepestIndex(node.right, ref deepestIndex, currentIndex + 1);
		}
	}
}
```

https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/

``` C#
/*
// Definition for a Node.
public class Node {
    public int val;
    public Node left;
    public Node right;
    public Node next;

    public Node() {}

    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, Node _left, Node _right, Node _next) {
        val = _val;
        left = _left;
        right = _right;
        next = _next;
    }
}
*/
public class Solution
{
    public Node Connect(Node root)
    {
        if(root is null)
        {
            return root;
        }
        
        var result = root;
        var queue = new Queue<Node>();
        queue.Enqueue(root);

        Add(queue);

        return result;
    }

    private void Add(Queue<Node> queue)
    {
        var count = queue.Count;

        if (count == 0)
        {
            return;
        }

        var frontNode = default(Node);

        while (count-- > 0)
        {
            var node = queue.Dequeue();

            if (frontNode is not null)
            {
                frontNode.next = node;
            }

            frontNode = node;

            if (node.left is not null)
            {
                queue.Enqueue(node.left);
            }

            if (node.right is not null)
            {
                queue.Enqueue(node.right);
            }
        }

        Add(queue);
    }
}
```