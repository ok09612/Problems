# Problems

https://leetcode.com/problems/merge-intervals/

``` C#
public class Solution
{
	public int[][] Merge(int[][] intervals)
	{
        intervals = intervals.OrderBy(x => x[0]).ToArray();
           
		var result = new List<int[]>();
		var start = intervals[0][0];
		var end = intervals[0][1];

		for (int i = 1; i < intervals.Length; i++)
		{
			if (intervals[i][0] <= end)
			{
				if (end < intervals[i][1])
				{
					end = intervals[i][1];
				}
				continue;
			}
			else
			{
				result.Add(new int[] { start, end });
				start = intervals[i][0];
				end = intervals[i][1];
			}
		}

		if (result.Count > 0)
		{
			var last = result[result.Count - 1];

			if (last[0] != start || last[1] != end)
			{
				result.Add(new int[] { start, end });
			}
		}
		else
		{
			result.Add(new int[] { start, end });
		}

		return result.ToArray();
	}
}
```