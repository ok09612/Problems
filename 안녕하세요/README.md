 [(8) Diagonal Traverse - LeetCode](https://leetcode.com/problems/diagonal-traverse/) O(m x n)

```c#
using System.Collections.Generic;

public class Solution
{

    private int[,] dir = { { -1, 1 },{ 1, -1 } };
    public int[] FindDiagonalOrder(int[][] mat)
    {
        var result = new List<int>();
        (int row, int col) cur = (0, 0);
        var position = 0;

        var (maxCol, maxRow) = (mat[0].Length - 1, mat.Length - 1);
        while (true)
        {
            result.Add(mat[cur.row][cur.col]);
            if (cur.row == maxRow && cur.col == maxCol)
            {
                break;
            }

            cur = (cur.row + dir[position, 0], cur.col + dir[position, 1]);

            var positionChange = (cur.row < 0 || cur.row > maxRow || cur.col < 0 || cur.col > maxCol);

            if ((cur.row < 0 && cur.col > maxCol) || (cur.row <= maxRow && (cur.col < 0 || cur.col > maxCol))) // 오른쪽 상단, 왼쪽벽, 오른쪽 벽
            {
                cur.row++;
            } else if (positionChange)
            {
                cur.col++;
            }

            if (positionChange)
            {
                cur = backstep(cur, position);
                position = (position + 1) % 2;
            }
        }

        return result.ToArray();
    }

    private (int row, int col) backstep((int row, int col) cur, int position)
        => (cur.row - dir[position, 0], cur.col - dir[position, 1]);
}
```

