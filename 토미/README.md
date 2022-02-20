# Problems

https://leetcode.com/problems/deepest-leaves-sum/

``` C#
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

https://leetcode.com/problems/rings-and-rods/

``` C#
public class Solution
{
	public int CountPoints(string rings)
	{
		var rods = new Dictionary<int, HashSet<char>>();

		for (int i = 0; i < 10; i++)
		{
			rods.Add(i, new HashSet<char>() { 'R', 'G', 'B'});
		}

		for (int i = 0; i < rings.Length / 2; i++)
		{
			var color = rings[i * 2];
			var rodIndex = Convert.ToInt32(rings[i * 2 + 1]) - 48;

			if (rods.TryGetValue(rodIndex, out var rod))
			{
				rod.Remove(color);

				if (rod.Count == 0)
				{
					rods.Remove(rodIndex);
				}
			}
		}

		return 10 - rods.Count;
	}
}
```