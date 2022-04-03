# Problems

https://leetcode.com/problems/group-anagrams/

``` C#
public class Solution
{
	public IList<IList<string>> GroupAnagrams(string[] strs)
	{
		var dict = new Dictionary<string, IList<string>>();

		foreach (var item in strs)
		{
			var arr = item.ToCharArray();
			Array.Sort(arr);
			var key = new string(arr);
			if (!dict.TryGetValue(key, out var list))
			{
				dict.Add(key, new List<string>());
			}

			dict[key].Add(item);
		}

		return dict.Values.OrderBy(x => x.Count).ToList();
	}
}
```

https://leetcode.com/problems/search-a-2d-matrix/

``` C#
public class Solution
{
	public bool SearchMatrix(int[][] matrix, int target)
	{
		var m = matrix.Length;
		var n = matrix[0].Length;

		for (int i = 0; i < m; i++)
		{
			if (matrix[i].Last() >= target)
			{
				var index = Array.BinarySearch(matrix[i], target);

				if (index > -1)
				{
					return true;
				}
			}
		}

		return false;
	}
}
```