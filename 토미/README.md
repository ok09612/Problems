# Problems

https://leetcode.com/problems/rotate-image/

``` C#
public class Solution
{
	public void Rotate(int[][] matrix)
	{
		var n = matrix.GetLength(0);
		var size = n - 1;
		var depthSize = n / 2;

		for (int depth = 0; depth < depthSize; depth++)
		{
			var endAmount = size - (depth * 2);
			for (int i = 0; i < endAmount; i++)
			{
				var tmpValue = matrix[depth][depth + i];

				matrix[depth][depth + i] = matrix[size - depth - i][depth];
				matrix[size - depth - i][depth] = matrix[size - depth][size - depth - i];
				matrix[size - depth][size - depth - i] = matrix[depth + i][size - depth];
				matrix[depth + i][size - depth] = tmpValue;
			}
		}
	}
}
```

https://leetcode.com/problems/combination-sum/

``` C#
public class Solution
{
	List<IList<int>> result = new List<IList<int>>();

	public IList<IList<int>> CombinationSum(int[] candidates, int target)
	{
		for (int i = 0; i < candidates.Length; i++)
		{
			Combinatioin(candidates, new List<int>() { candidates[i] }, i, candidates[i], target);
		}

		return result;
	}

	private void Combinatioin(int[] candidates, List<int> elements, int index, int sum, int target)
	{
		if (sum > target)
		{
			return;
		}
		else if(sum == target)
		{
			result.Add(elements);
			return;
		}
		else
		{
			for (int i = index; i < candidates.Length; i++)
			{
				var newElements = new List<int>(elements);
				newElements.Add(candidates[i]);
				Combinatioin(candidates, newElements, i, sum + candidates[i], target);
			}
		}
	}
}
```

https://leetcode.com/problems/divide-two-integers/

``` C#
public class Solution
{
	public int Divide(int dividend, int divisor)
	{
		if (divisor == -1)
		{
			if (dividend == int.MaxValue)
			{
				return int.MinValue;
			}
			else if(dividend == int.MinValue)
			{
				return int.MaxValue;
			}
			else
			{
				return -dividend;
			}
		}

		return dividend / divisor;
	}
}
```

https://leetcode.com/problems/zigzag-conversion/

``` C#
public class Solution
{
	public string Convert(string s, int numRows)
	{
		if (numRows == 1)
		{
			return s;
		}

		var result = new StringBuilder(s.Length);

		var rows = new List<StringBuilder>();

		for (int i = 0; i < numRows; i++)
		{
			rows.Add(new StringBuilder());
		}

		var cycleSize = numRows * 2 - 2;

		for (int i = 0; i < s.Length; i++)
		{
			var remain = i % cycleSize;

			if (remain < numRows)
			{
				rows[remain].Append(s[i]);
			}
			else
			{
				var startIndex = remain - numRows;
				rows[numRows - startIndex - 2].Append(s[i]);
			}
		}

		rows.ForEach(x => result.Append(x));

		return result.ToString();
	}
}
```