# Problems

https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/

``` C#
public class Solution
{
    public IList<IList<int>> ZigzagLevelOrder(TreeNode root)
    {
        var result = new List<IList<int>>();

        if (root == null)
        {
            return result;
        }

		//순차적인 작업을 보장하기위한 Queue
        var nextNodes = new Queue<TreeNode>();

        nextNodes.Enqueue(root);

		//방향 전환용 변수
        var fromLeft = true;

        while (nextNodes.Count > 0)
        {
            if (fromLeft)
            {
                ToRight(nextNodes, result);
            }
            else
            {
                ToLeft(nextNodes, result);
            }

            fromLeft = !fromLeft;
        }

        return result;
    }

    private void ToLeft(Queue<TreeNode> nextNodes, List<IList<int>> result)
    {
        var nodeCount = nextNodes.Count;

        var currentResult = new List<int>();

		//Queue에 의해 순서대로 작업을 진행하지만 다음 작업의 경우 순서가 반전이 되어야하기 때문에 Stack으로 순서 백업
        var stack = new Stack<TreeNode>();

        for (int i = 0; i < nodeCount; i++)
        {
            var item = nextNodes.Dequeue();

            currentResult.Add(item.val);

			//실제로 ToLeft와 ToRight 메서드에서 다른 부분 순서에따라 어느방향의 노드부터 저장할지 결정
            if (item.right != null)
            {
                stack.Push(item.right);
            }

            if (item.left != null)
            {
                stack.Push(item.left);
            }
        }

        while (stack.Count > 0)
        {
            nextNodes.Enqueue(stack.Pop());
        }

        result.Add(currentResult);
    }

    private void ToRight(Queue<TreeNode> nextNodes, List<IList<int>> result)
    {
        var nodeCount = nextNodes.Count;

        var currentResult = new List<int>();

        var stack = new Stack<TreeNode>();

        for (int i = 0; i < nodeCount; i++)
        {
            var item = nextNodes.Dequeue();

            currentResult.Add(item.val);

            if (item.left != null)
            {
                stack.Push(item.left);
            }

            if (item.right != null)
            {
                stack.Push(item.right);
            }
        }

        while (stack.Count > 0)
        {
            nextNodes.Enqueue(stack.Pop());
        }

        result.Add(currentResult);
    }
}
```

https://leetcode.com/problems/number-of-islands/

``` C#
public class Solution
{
	//맵 크기 저장용 변수
    int n, m;

    public int NumIslands(char[][] grid)
    {
		//크기 정보 ㅊ초기화
        n = grid.GetLength(0);
        m = grid[0].Length;

		//land 마킹용 변수, grid 변수와 동일한 크기를 가짐.
        var lands = new int[n][];

        for (int i = 0; i < n; i++)
        {
            lands[i] = new int[m];
        }

		//land의 id, 1부터 증가시킬 예정이므로 최종값이 land의 개수
        var landId = 0;

        for (int i = 0; i < n; i++)
        {
            for (int j = 0; j < m; j++)
            {
				//땅이 아니거나 이미 마킹이 되어있다면 작업을 할 필요가 없음.
                if (!IsValid(i, j, grid, lands))
                {
                    continue;
                }

                Mark(i, j, grid, lands, ++landId);
            }
        }

        return landId;
    }

    private void Mark(int i, int j, char[][] grid, int[][] lands, int landId)
    {
		//땅이 아니거나 이미 마킹이 되어있다면 작업을 할 필요가 없음.
        if (!IsValid(i, j, grid, lands))
        {
            return;
        }

        lands[i][j] = landId;

        var left = j - 1;
        var right = j + 1;
        var top = i - 1;
        var bottom = i + 1;

		//위치별로 
        if (left > -1)
        {
            Mark(i, left, grid, lands, landId);
        }

        if (right < m)
        {
            Mark(i, right, grid, lands, landId);
        }

        if (top > -1)
        {
            Mark(top, j, grid, lands, landId);
        }

        if (bottom < n)
        {
            Mark(bottom, j, grid, lands, landId);
        }
    }

	private bool IsValid(int i, int j, char[][] grid, int[][] lands)
    {
        return grid[i][j] == '0' || lands[i][j] != 0 ? false : true;
    }
}
```