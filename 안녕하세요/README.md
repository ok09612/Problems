O(NLogN)
```c#
using System;
using System.Collections.Generic;

public class Solution
{
    public int[][] Merge(int[][] intervals)
    {
        Array.Sort(intervals, (a, b) =>
        {
            if (a[0] == b[0])
            {
                return (a[1] < b[1]) ? -1 : 1;
            }
            return a[0] < b[0] ? -1 : 1;
        });

        var answer = new List<int[]>();
        var item = intervals[0];
        for (int i = 1; i < intervals.Length; i++)
        {
            if (item[1] >= intervals[i][0])
            {
                item[1] = Math.Max(item[1], intervals[i][1]);
            } else
            {
                answer.Add(item);
                item = intervals[i];
            }
        }
        answer.Add(item);
        return answer.ToArray();
    }
}
```
