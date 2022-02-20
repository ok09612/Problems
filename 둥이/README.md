# 2103. Rings and Rods
### 시간복잡도 -> O(N)

```C#

class RodInfo
{
    public bool IsRed { get; set; } = false;
    public bool IsGreen { get; set; } = false;
    public bool IsBlue { get; set; } = false;
    public bool IsThreeColor => IsRed && IsGreen && IsBlue;
    public void SetColor(char color)
    {
        switch (color)
        {
            case 'R':
                IsRed = true;
                break;
            case 'G':
                IsGreen = true;
                break;
            case 'B':
                IsBlue = true;
                break;
        }
    }
}

public class Solution {
    public int CountPoints(string rings) {
        List<RodInfo> rodList = new List<RodInfo>();
        for (int i = 0; i < 10; ++i)
        {
            rodList.Add(new RodInfo());
        }

        char color = ' ';
        for (int i = 0; i < rings.Length; ++i)
        {
            // i가 짝수일 때에는 색깔 구별
            if (i % 2 == 0)
            {
                color = rings[i];
            }
            // i가 홀수일 때에는 해당 위치에 색깔 저장
            else
            {
                int index = int.Parse(rings[i].ToString());
                rodList[index].SetColor(color);
            }
        }

        int result = 0;
        for (int i = 0; i < rodList.Count; ++i)
        {
            if (rodList[i].IsThreeColor) result++;
        }
        
        return result;
    }
}

```

# 1302. Deepest Leaves Sum
### 시간복잡도 -> O(N^2)

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
    public int DeepestLeavesSum(TreeNode root) {
        Queue<TreeNode> queue = new Queue<TreeNode>();
        queue.Enqueue(root);
        
        int result = 0;
        while (queue.Count > 0) {
            result = 0;
            int queueSize = queue.Count;
            
            for (int i = 0; i < queueSize; ++i) {
                TreeNode node = queue.Dequeue();
                
                result += node.val;
                
                if (node.left != null) {
                    queue.Enqueue(node.left);
                }
                
                if (node.right != null) {
                    queue.Enqueue(node.right);
                }
            }
        }
        
        return result;
    }
}

```
