# Problems

https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/

``` C#
public class Solution {
    public int NumberOfSteps(int num) {
        
        var count = 0;
        
        while(num != 0){
            count++;
            if(num % 2 == 1){
                num -= 1;
            }
            else{
                num /= 2;
            }            
        }
        
        return count;
    }
}
```

https://leetcode.com/problems/recover-a-tree-from-preorder-traversal/

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
	public TreeNode RecoverFromPreorder(string traversal)
	{
		var stack = new Stack<TreeNode>();

		for (int i = 0; i < traversal.Length; i++)
		{
			var item = traversal[i];
			
			//Depth일 경우
			if (item == '-')
			{
				var dashLength = GetDashLength(traversal, i);
				i += dashLength - 1;

				while (stack.Count > dashLength)
				{
					stack.Pop();
				}

			}
			//숫자일 경우
			else
			{
				var numberLength = GetNumberLength(traversal, i);
				var value = int.Parse(traversal.Substring(i, numberLength));
				i += numberLength - 1;
				var newNode = new TreeNode(value);

				if (stack.Count > 0)
				{
					var parent = stack.Peek();

					if (parent.left == null)
					{
						parent.left = newNode;
					}
					else
					{
						parent.right = newNode;
					}
				}

				stack.Push(newNode);
			}
		}

		return stack.Last();
	}

	private int GetNumberLength(string traversal, int startIndex)
	{
		var numberLength = 0;

		for (int i = startIndex; i < traversal.Length; i++)
		{
			if (traversal[i] != '-')
			{
				numberLength++;
			}
			else
			{
				break;
			}
		}

		return numberLength;
	}

	private int GetDashLength(string traversal, int startIndex)
	{
		var dashLength = 0;

		for (int i = startIndex; i < traversal.Length; i++)
		{
			if (traversal[i] == '-')
			{
				dashLength++;
			}
			else
			{
				break;
			}
		}

		return dashLength;
	}
}

public class TreeNode
{
	public int val;
	public TreeNode left;
	public TreeNode right;
	public TreeNode(int val = 0, TreeNode left = null, TreeNode right = null)
	{
		this.val = val;
		this.left = left;
		this.right = right;
	}
}
```