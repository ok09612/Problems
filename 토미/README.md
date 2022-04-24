# Problems

https://leetcode.com/problems/sort-the-matrix-diagonally/

``` C#
using System.Drawing;

public class Solution
{
    public int[][] DiagonalSort(int[][] mat)
    {
        var dataPerStartPoint = new Dictionary<Point, List<int>>();
        var rowSize = mat.Length;
        var columnSize = mat[0].Length;

        for (int i = 0; i < rowSize; i++)
        {
            var items = new List<int>();
            dataPerStartPoint.Add(new Point(i, 0), items);
            var row = i;
            var column = 0;

            while (row < rowSize && column < columnSize)
            {
                items.Add(mat[row++][column++]);
            }

            items.Sort();
        }

        for (int i = 1; i < columnSize; i++)
        {
            var items = new List<int>();
            dataPerStartPoint.Add(new Point(0, i), items);
            var row = 0;
            var column = i;

            while (row < rowSize && column < columnSize)
            {
                items.Add(mat[row++][column++]);
            }

            items.Sort();
        }

        foreach (var item in dataPerStartPoint)
        {
            var row = item.Key.X;
            var column = item.Key.Y;
            var data = item.Value;
            var index = 0;

            while (index < data.Count)
            {
                mat[row++][column++] = data[index++];
            }
        }

        return mat;
    }
}
```