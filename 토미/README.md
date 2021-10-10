# Problems

https://leetcode.com/problems/spiral-matrix/

``` C#
public class Solution
{
	enum Directions
	{
		Right,
		Bottom,
		Left,
		Top
	}
	public IList<int> SpiralOrder(int[][] matrix)
	{
		var result = new List<int>();
		var direction = Directions.Right;
		var xMin = 0;
		var yMin = 0;
		var xMax = matrix.Length - 1;
		var yMax = matrix[0].Length - 1;
		var x = 0;
		var y = 0;
		while (xMin <= xMax && yMin <= yMax)
		{
			result.Add(matrix[x][y]);
			//Set Next
			switch (direction)
			{
				case Directions.Right:
					if (y < yMax)
					{
						y++;
					}
					else
					{
						direction = Directions.Bottom;
						x++;
						xMin++;
					}
					break;
				case Directions.Bottom:
					if (x < xMax)
					{
						x++;
					}
					else
					{
						direction = Directions.Left;
						y--;
						yMax--;
					}
					break;
				case Directions.Left:
					if (y > yMin)
					{
						y--;
					}
					else
					{
						direction = Directions.Top;
						x--;
						xMax--;
					}
					break;
				case Directions.Top:
					if (x > xMin)
					{
						x--;
					}
					else
					{
						direction = Directions.Right;
						y++;
						yMin++;
					}
					break;
			}
		}
		return result;
	}
}
```