# Plus One
- https://leetcode.com/problems/plus-one/

```c#
public class Solution {
    public int[] PlusOne(int[] digits) {
        List<int> lst = new List<int>();

        for (int i=0; i<digits.Length; i++)
            lst.Add(digits[i]);

        for (int i=lst.Count - 1; i>=0; i--)
        {
            lst[i]++;

            if ((lst[i] %= 10) != 0)
                break;
                
            if (i == 0)
            {
                lst.Insert(0, 1);
                break;
            }
        }

        return lst.ToArray();
    }
}
```


# Find Right Interval
- https://leetcode.com/problems/find-right-interval/

```c#
public class Solution {
    public int[] FindRightInterval(int[][] intervals) {
        int[] res = new int[intervals.Length];

        for (int i=0; i<intervals.Length; i++)
        {
            int targetIndex = -1;
            int startj = int.MaxValue;

            for (int j=0; j<intervals.Length; j++)
            {
                if (intervals[j][0] < intervals[i][1])
                    continue;

                if (startj > intervals[j][0])
                {
                    targetIndex = j;
                    startj = intervals[j][0];
                }
            }

            res[i] = targetIndex;
        }

        return res;
    }
}
```


# Diagonal Traverse
- https://leetcode.com/problems/diagonal-traverse/
```c#
public class Solution {
    public int[] FindDiagonalOrder(int[][] mat) {
        List<int> res = new List<int>();

        SetLocation(mat, res, (0, 0), true);

        return res.ToArray();
    }

    void SetLocation(int[][] mat, List<int> res, (int x, int y) loc, bool up)
    {
        res.Add(mat[loc.y][loc.x]);

        if (loc.y == mat.Length - 1 && loc.x == mat[0].Length - 1)
            return;

        (int x, int y) locChange = (loc.x + (up ? 1 : -1), loc.y + (up ? -1 : 1));

        bool valid = true;

        if (locChange.x < 0 || locChange.y < 0 || locChange.x > mat[0].Length - 1 || locChange.y > mat.Length - 1)
            valid = false;

        if (!valid)
        {
            if (up)
            {
                if (loc.x + 1 <= mat[0].Length - 1)
                    loc.x++;
                else
                    loc.y++;
            }
            else
            {
                if (loc.y + 1 <= mat.Length - 1)
                    loc.y++;
                else
                    loc.x++;
            }

            locChange = loc;
            up = !up;
        }

        SetLocation(mat, res, locChange, up);
    }
}
```


# Third Maximum Number
- https://leetcode.com/problems/third-maximum-number/
```c#
public class Solution {
    public int ThirdMax(int[] nums) {
        Array.Sort(nums);
        int num = int.MaxValue;
        int interval = 0;

        for (int i=nums.Length - 1; i>=0; i--)
        {
            if (nums[i] < num)
            {
                num = nums[i];

                if (++interval >= 3)
                    break;
            }
        }

        return interval >= 3 ? num : nums[nums.Length - 1];
    }
}
```