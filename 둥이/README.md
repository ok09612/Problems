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

# 2번 문제 - 추후 업데이트 예정
