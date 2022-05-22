```C#
public class Solution
{
    public int MaxSubArray(int[] nums)
    {
        var n1 = nums[0];
        var cur = n1;
        var answer = n1;
        for(int i =1;i<nums.Length;i++)
        {
            n1 = cur;
            if (nums[i] + n1 > nums[i])
            {
                cur = nums[i] + n1;
            } else
            {
                cur = nums[i];
            }

            answer = Math.Max(answer, cur);
        }

        return answer;
    }
}
```
