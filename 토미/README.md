# Problems

https://leetcode.com/problems/trim-a-binary-search-tree/submissions/

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
    public TreeNode TrimBST(TreeNode root, int low, int high)
    {
        if (root == null)
        {
            return null;
        }

        if (root.val > high)
        {
            return TrimBST(root.left, low, high);
        }
        else if(root.val < low)
        {
            return TrimBST(root.right, low, high);
        }
        else
        {
            root.left = TrimBST(root.left, low, high);
            root.right = TrimBST(root.right, low, high);
            return root;
        }
    }
}
```

https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree/

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
    public TreeNode BstToGst(TreeNode root)
    {
        Gst(root, 0);

        return root;
    }

    private int Gst(TreeNode node, int val)
    {
        if (node == null)
        {
            return val;
        }

        node.val += Gst(node.right, val);
        return Gst(node.left, node.val);
    }
}
```