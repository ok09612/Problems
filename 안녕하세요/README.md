## [타겟넘버](https://programmers.co.kr/learn/courses/30/lessons/43165?language=csharp)

- 시간복잡도 : 2^N

```c#
using System;
using System.Collections.Generic;

public class Solution
{
    public int Backtracking(int[] numbers, int target, int cur = 0)
    {
        if (cur >= numbers.Length)
        {
            if (target == 0)
            {
                return 1;
            }
            return 0;
        }
        return Backtracking(numbers, target - numbers[cur], cur + 1) + Backtracking(numbers, target + numbers[cur], cur + 1);
    }

    public int solution(int[] numbers, int target)
    {
        return
        Backtracking(numbers, target);
    }
}
```

## [103. Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

- 시간복잡도 O(N)

```c#
public class Solution
{
    private void PreOrder(TreeNode cur, int level, Dictionary<int, IList<int>> data)
    {
        if (cur == null)
        {
            return;
        }
        if (data.ContainsKey(level) == false)
        {
            data[level] = new List<int>();
        }
        data[level].Add(cur.val);
        PreOrder(cur.left, level + 1, data);
        PreOrder(cur.right, level + 1, data);
    }
    public IList<IList<int>> ZigzagLevelOrder(TreeNode root)
    {
        var answer = new List<IList<int>>();
        if (root == null)
        {
            return answer;
        }

        var data = new Dictionary<int, IList<int>>();
        PreOrder(root, 1, data);
        foreach(var level in data.Keys)
        {
            if (level % 2 == 0)
            {
                data[level] = data[level].Reverse().ToList();
            }
            answer.Add(data[level]);
        }
        return answer;
    }
}
```

## [200. Number of Islands](https://leetcode.com/problems/number-of-islands/)

- 시간복잡도: O(MN) ?? 모든 배열 탐색(M x N) + BFS 탐색(노드 MN, 간선 4MN => MN + 4MN)

```c#

public class Solution
{
    private int[,] dir = new int[,] { { 1, 0 }, { -1, 0 }, { 0, 1 }, { 0, -1 } };
    
    private void VisitIsland(char[][]grid, ref bool[,] visit, int row, int col)
    {
        var que = new Queue<(int r, int c)>();
        que.Enqueue((row, col));
        visit[row, col] = true;
        while (que.Count > 0)
        {
            var (r, c) = que.Dequeue();

            for (int i = 0; i < 4; i++)
            {
                int nr = r + dir[i, 0];
                int nc = c + dir[i, 1];

                if (nr < 0 || nc < 0 || nr >= grid.Length || nc >=grid[0].Length)
                {
                    continue;
                }
                if (visit[nr,nc])
                {
                    continue;
                }
                if (grid[nr][nc] == '0')
                {
                    continue;
                }
                visit[nr, nc] = true;
                que.Enqueue((nr, nc));
            }
        }
    }
    
    public int NumIslands(char[][] grid)
    {
        bool[,] visit = new bool[grid.Length, grid[0].Length];
        int answer = 0;
        for(int i =0;i<grid.Length;i++)
        {
            for(int j =0;j<grid[0].Length;j++)
            {
                if (grid[i][j] == '1' && visit[i,j] == false)
                {
                    VisitIsland(grid,ref visit, i, j);
                    answer++;
                }
            }
        }
        return answer;
    }
}
```
