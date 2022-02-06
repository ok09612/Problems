# Problems

# 1번 문제 - 프로그래머스_프린터

```C#

using System;
using System.Collections.Generic;
using System.Linq;

public class Solution {
    public int solution(int[] priorities, int location) {
        int answer = 0;
        
        Queue<Tuple<int, int>> locationQueue = new Queue<Tuple<int, int>>();
        for (int i = 0; i < priorities.Length; ++i)
        {
            locationQueue.Enqueue(new Tuple<int, int> ( i, priorities[i] ));
        }

        int priorityIndex = -1;
        int priority = -1;

        while (locationQueue.Count > 0)
        {
            int maxPriority = locationQueue.ToList().Max((tuple) => tuple.Item2);
            var dequeue = locationQueue.Dequeue();

            priorityIndex = dequeue.Item1;
            priority = dequeue.Item2;

            if (priority >= maxPriority)
            {
                answer++;
                if (priorityIndex == location)
                {
                    break;
                }
            }
            else
            {
                locationQueue.Enqueue(new Tuple<int, int>(priorityIndex, priority));
            }
        }
        
        return answer;
    }
}
```

# 2번 문제 - 프로그래머스_가장 큰 수
```C#

using System;
using System.Text;

public class Solution {
    public string solution(int[] numbers) {
        string answer = "";
        int zeroCount = 0;
        StringBuilder sb = new StringBuilder();

        foreach (var num in numbers)
        {
            if (num == 0) ++zeroCount;
        }

        if (zeroCount == numbers.Length)
        {
            answer = "0";
        }
        else
        {
            Array.Sort(numbers, (x, y) => string.Compare(y.ToString() + x.ToString(), x.ToString() + y.ToString()));

            foreach (int num in numbers)
            {
                sb.Append(num.ToString());
            }

            answer = sb.ToString();
        }
        
        return answer;
    }
}

```
