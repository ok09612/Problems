- Same tree O(N)
```C#
public class Solution
{
    private StringBuilder PreOrder(TreeNode cur)
    {
        if (cur == null)
        {
            return new StringBuilder("null");
        }
        var str = new StringBuilder();
        str.Append(cur.val);
        str.Append(PreOrder(cur.left));
        str.Append(PreOrder(cur.right));
        return str;
    }

    public bool IsSameTree(TreeNode p, TreeNode q)
    {
        return PreOrder(p).ToString() == PreOrder(q).ToString();
    }
}
```

- Maximum Length of Repeated Subarray O(nm)
```c#
public class Solution
{
    public int FindLength(int[] nums1, int[] nums2)
    {
        if (nums1.Length == 0 || nums2.Length == 0)
        {
            return 0;
        }
        var answer = 0;
        var dp = new int[nums1.Length, nums2.Length];
        for (int i = 0; i < nums1.Length; i++)
        {
            for (int j = 0; j < nums2.Length; j++)
            {
                if (nums1[i] == nums2[j])
                {
                    if (i - 1 >= 0 && j - 1 >= 0)
                    {
                        dp[i, j] = dp[i - 1, j - 1];
                    }
                    dp[i, j]++;
                    answer = Math.Max(answer, dp[i, j]);
                }
            }
        }
        return answer;
    }
}
```

- Minimum Path Sum O(nm)
```c#
public class Solution
{
    public int MinPathSum(int[][] grid)
    {
        int m = grid.Length;
        int n = grid[0].Length;
        var dp = new int[m, n];
        for (int i = 0; i < m; i++)
        {
            for (int j = 0; j < n; j++)
            {
                if (i - 1 >= 0 && j - 1 >= 0)
                {
                    dp[i, j] = Math.Min(dp[i, j - 1], dp[i - 1, j]) + grid[i][j];
                } else if(i - 1 >=0)
                {
                    dp[i, j] = dp[i - 1, j] + grid[i][j];
                } else if(j-1>=0)
                {
                    dp[i, j] = dp[i, j - 1] + grid[i][j];
                } else
                {
                    dp[i, j] = grid[i][j];
                }
            }
        }
        return dp[m - 1, n - 1];
    }
}
```
