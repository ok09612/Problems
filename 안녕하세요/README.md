O(N^2)

```c#
public class Solution
{
    public int MaxProfit(int[] prices)
    {
        // profit[i] : i day일 때 최대 이익
        var profit = new int[prices.Length];
        profit[0] = 0;
        for (int i = 1; i < prices.Length; i++)
        {
            for (int j = i - 1; j >= 0; j--)
            {
                var sell = Math.Max(0, prices[i] - prices[j]);
                var currentProfit = (j - 2 > 0) ? profit[j - 2] : 0;
                profit[i] = Math.Max(profit[i], sell + currentProfit);
            }
            profit[i] = Math.Max(profit[i], profit[i - 1]);
        }

        return profit.Max();
    }
}

```

O(N)

```c#
public class Solution {
    public void Merge(int[] nums1, int m, int[] nums2, int n) {
        int mi = 0, ni = 0, i = 0;
        int[] nums = new int[m + n];
        while (mi < m && ni < n) {
            if (nums1[mi] < nums2[ni]) {
                nums[i++] = nums1[mi++];
            } else {
                nums[i++] = nums2[ni++];
            }
        }
        while (mi < m) nums[i++] = nums1[mi++];
        while (ni < n) nums[i++] = nums2[ni++];
        
        i = 0;
        while (i < nums1.Length) nums1[i] = nums[i++];
    }
}
```

