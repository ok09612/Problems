# 타겟 넘버
- https://programmers.co.kr/learn/courses/30/lessons/43165

```c#
using System;

public class Solution {
    private int count = 0;

    public int solution(int[] numbers, int target)
    {
        dfs(numbers, target, 0, 0);

        return count;
    }

    public void dfs(int[] numbers, int target, int currentIndex, int total)
    {
        if (currentIndex == numbers.Length)
        {
            if (target == total)
                count++;
        }
        else
        {
            dfs(numbers, target, currentIndex + 1, total + numbers[currentIndex]);
            dfs(numbers, target, currentIndex + 1, total - numbers[currentIndex]);
        }
    }
}
```

# Binary Tree Zigzag Level Order Traversal
- https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/

```c#
public class Solution {
    public IList<IList<int>> ZigzagLevelOrder(TreeNode root) {
        IList<IList<int>> output = new List<IList<int>>();

        if (root != null)
            SearchTree(new List<TreeNode> { root }, 0, true, ref output);

        return output;
    }

    void SearchTree(List<TreeNode> nodes, int level, bool asc, ref IList<IList<int>> output)
    {
        List<TreeNode> lstChild =  new List<TreeNode>();

        if (output.Count < level + 1)
            output.Add(new List<int>());

        for (int i=nodes.Count - 1; i>=0; i--)
        {
            TreeNode r = nodes[i];

            output[level].Add(r.val);

            if (asc)
            {
                if (r.left != null)
                    lstChild.Add(r.left);

                if (r.right != null)
                    lstChild.Add(r.right);
            }
            else
            {
                if (r.right != null)
                    lstChild.Add(r.right);

                if (r.left != null)
                    lstChild.Add(r.left);
            }
        }

        if (lstChild.Count > 0)
            SearchTree(lstChild, level + 1, !asc, ref output);
    }
}
```

# Number of Islands
- https://leetcode.com/problems/number-of-islands/

```c#
public class Solution {
    int MaxX = 0;
    int MaxY = 0;
    int IslandCount = 0;
    public int NumIslands(char[][] grid) {
        if (grid.Length > 0 && grid[0].Length > 0)
        {
            MaxY = grid.Length;
            MaxX = grid[0].Length;

            bool[,] flags = new bool[MaxX, MaxY];

            for (int i=0; i<MaxX; i++)
            {
                for (int j=0; j<MaxY; j++)
                    flags[i,j] = false;
            }

            for (int y=0; y<MaxY; y++)
            {
                for (int x=0; x<MaxX; x++)
                {
                    if (grid[y][x] == '1')
                    {
                        SearchArray(grid, flags, x, y, true);
                    }
                }
            }

            return IslandCount;
        }
        return 0;
    }

    void SearchArray(char[][] grid, bool[,] flag, int x, int y, bool newIsland)
    {
        if (flag[x,y])
            return;

        flag[x,y]=true;

        if (newIsland)
            IslandCount++;

        if (x - 1 >= 0 && grid[y][x - 1] == '1' && !flag[x-1,y])
            SearchArray(grid, flag, x - 1, y, false);

        if (y - 1 >= 0 && grid[y - 1][x] == '1' && !flag[x,y-1])
            SearchArray(grid, flag, x, y - 1, false);

        if (x + 1 < MaxX && grid[y][x + 1] == '1' && !flag[x+1,y])
            SearchArray(grid, flag, x + 1, y, false);

        if (y + 1 < MaxY && grid[y + 1][x] == '1' && !flag[x,y+1])
            SearchArray(grid, flag, x, y + 1, false);    
    }
}
```
