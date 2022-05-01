# Problems

https://leetcode.com/problems/increasing-order-search-tree/

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
public class Solution {
    TreeNode currentNode;
    public TreeNode IncreasingBST(TreeNode root) {
        currentNode = new TreeNode();
        var result = currentNode;
        Search(root);
                    
        return result.right;
    }
    
    
    private void Search(TreeNode node)
    {
        if(node == null)
        {
            return;
        }
        
        Search(node.left);
        node.left = null;
        currentNode.right = node;
        currentNode = node;
        
        Search(node.right);
    }
}
```

https://leetcode.com/problems/trim-a-binary-search-tree/

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