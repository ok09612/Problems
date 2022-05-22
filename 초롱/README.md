// Recursion + Bit manipulation solution
// Time: O(2 ^ n), 1ms
// Space: O(n) for call stack, O(2 ^ n) for ans, 34.4mb
// https://leetcode.com/problems/gray-code/
class Solution {
    public List<Integer> grayCode(int n) {
        // Base case
        if(n == 0) {
            List<Integer> ans = new ArrayList<>();
            ans.add(0);
            return ans;
        }

        // grayCode(n) = grayCode(n - 1) + (1 << (n - 1) + reversed(grayCode(n - 1) ))
        List<Integer> ans = grayCode(n - 1);
        int base = 1 << (n - 1); // 01 << 2 -> 0100
        int size = ans.size();
        for(int i = size - 1; i >= 0; i--) {
            ans.add(base + ans.get(i));  // 1 + the mirror of the grayCode(n - 1)0
        }

        return ans;
    }
}

// https://leetcode.com/problems/maximum-subarray/
class Solution {
    public int maxSubArray(int[] nums) {
        int sum=nums[0], ret=nums[0];
        for(int i=1; i<nums.length; i++) {
            sum = Math.max(sum+nums[i], nums[i]); // 1차 거름
            ret = Math.max(sum, ret); // 2차 거름
        }
        return ret;
    }
}
