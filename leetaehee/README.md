# LeetCode - 75. Sort Colors

https://leetcode.com/problems/sort-colors/
  
중복이 있는 숫자(색깔)를 오름차순으로 정렬하기

```Java

class Solution {
    public void sortColors(int[] nums) {
        int len = nums.length;
        int a=0, b=0, c=0;
        
        for(int i=0; i<len; i++) {
            if(nums[i] == 0)
                a++;
            else if(nums[i] == 1)
                b++;
            else
                c++;
        }
        
        int i = 0;
        for(int j=0; j<a; i++,j++) {
            nums[i] = 0;
        }
        for(int j=0; j<b; i++,j++) {
            nums[i] = 1;
        }
        for(int j=0; j<c; i++,j++) {
            nums[i] = 2;
        }

    }
}

```

시간복잡도 : O(N)
모든 배열을 2회 탐색하여 O(N) 안에 끝낼 수 있다.
<br />