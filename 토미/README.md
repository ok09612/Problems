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
		//부모 노드를 바로바로 추적 할 수 있도록 stack을 사용
		var stack = new Stack<TreeNode>();
		//부모 노드를 추적하기위한 count
		var depth = 0;

		for (int i = 0; i < traversal.Length; i++)
		{
			var item = traversal[i];
			
			//Depth일 경우
			if (item == '-')
			{
				depth++;
			}
			//숫자일 경우
			else
			{
				//숫자의 문자열 길이가 한글자가 아닐수도 있음.
				var numberLength = GetNumberLength(traversal, i);
				var value = int.Parse(traversal.Substring(i, numberLength));
				//숫자의 길이만큼 index 조정
				i += numberLength - 1;
				var newNode = new TreeNode(value);

				if (stack.Count != 0)
				{
					while (stack.Count > depth)
					{
						stack.Pop();
					}

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

				depth = 0;
			}
		}

		//root 반환
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
}
```