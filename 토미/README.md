# Problems

https://leetcode.com/problems/maximum-subarray/

``` C#
public class Solution
{
	public int MaxSubArray(int[] nums)
	{
		var sum = 0;
		var max = nums[0];

		for (int i = 0; i < nums.Length; i++)
		{
			sum = Math.Max(nums[i], nums[i] + sum);
			max = Math.Max(sum, max);
		}

		return max;
	}
}
```