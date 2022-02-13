# 1번 문제
## 100. Same Tree
#### 시간복잡도 - Log(N)

```C#

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
    public bool IsSameTree(TreeNode p, TreeNode q) {
        bool result = true;
        
        if (p == null && q == null) return result;
        
        // p, q 노드 차례대로 Queue에 저장
        Queue<TreeNode> queue = new Queue<TreeNode>();
        queue.Enqueue(p);
        queue.Enqueue(q);
        
        while (queue.Count > 0) 
        {
            TreeNode firstNode = queue.Dequeue();
            TreeNode secondNode = queue.Dequeue();
            
            // Dequeue한 Node 둘 다 null이면 일치하기 때문에 다음 루프 실행
            if (firstNode == null && secondNode == null) continue;
            
            // 둘 중 하나만 null이면 일치하지 않기 때문에 false 리턴
            // 위의 조건문에서 둘 다 null인 경우를 제외했기 때문에 해당 조건을 통해 둘 중 하나만 null인 경우 판별 가능
            if (!(firstNode != null && secondNode != null)) 
            {
                result = false;
                break;
            }
            
            // Dequeue한 두 개의 노드 값이 일치하면 왼쪽 노드, 오른쪽 노드를 p, q 순서대로 Queue에 저장
            if (firstNode.val == secondNode.val) 
            {
                queue.Enqueue(firstNode.left);
                queue.Enqueue(secondNode.left);
                queue.Enqueue(firstNode.right);
                queue.Enqueue(secondNode.right);
            }
            else
            {
                result = false;
                break;
            }
        }
        
        return result;
    }
}

```


# 2번 문제
## 18. Maximum Length of Repeated Subarray
#### 시간복잡도 - O(N^2)

```C#

public class Solution {
    public int FindLength(int[] nums1, int[] nums2) {
        int result = 0;             // 중복 횟수
        
        int nums1Length = nums1.Length;
        int nums2Length = nums2.Length;

        int[,] dp = new int[nums1Length + 1, nums2Length + 1];

        for (int i = 1; i <= nums1Length; ++i)
        {
            for (int j = 1; j <= nums2Length; ++j)
            {
                if (nums1[i - 1] == nums2[j - 1])
                {
                    dp[i, j] = dp[i - 1, j - 1] + 1;
                    if (result < dp[i, j])
                    {
                        result = dp[i, j];
                    }
                }
            }
        }
        
        return result;
    }
}

```


# 3번 문제
## 64. Minimum Path Sum
#### 시간복잡도 - O(N^2)

```C#

public class Solution {
    public int MinPathSum(int[][] grid) {
        int m = grid.Length;
        int n = grid[0].Length;

        int[,] dp = new int[m, n];
        for (int i = 0; i < m; ++i )
        {
            for (int j = 0; j < n; ++j)
            {
                dp[i, j] = int.MaxValue;
            }
        }

        dp[0, 0] = grid[0][0];
        int sum = 0;

        for (int i = 0; i < m; ++i)
        {
            for (int j = 0; j < n; ++j)
            {
                int up = i - 1;
                int left = j - 1;

                if (up < 0 && left < 0)
                {
                    continue;
                }
                else
                {
                    if (up < 0)
                    {
                        sum = dp[i, left] + grid[i][j];
                        if (dp[i, j] > sum) dp[i, j] = sum;
                    }
                    else if (left < 0)
                    {
                        sum = dp[up, j] + grid[i][j];
                        if (dp[i, j] > sum) dp[i, j] = sum;
                    }
                    else
                    {
                        sum = dp[i, left] + grid[i][j];
                        if (dp[i, j] > sum) dp[i, j] = sum;

                        sum = dp[up, j] + grid[i][j];
                        if (dp[i, j] > sum) dp[i, j] = sum;
                    }
                }
            }
        }
        
        return dp[m - 1, n - 1];
    }
}

```
