# 1. Two Sum 
# Java 풀이
# 시간복잡도: O(n)

class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap <Integer, Integer> map = new HashMap<>();
        
        // for storing indices
        int[] storeIndex = new int[2];
        
        // inserting it on HashMap
        for (int i=0; i < nums.length; i++)
        {
            if (map.containsKey(target - nums[i]))
            {
                storeIndex[1] = i;
                storeIndex[0] = map.get(target - nums[i]);
                return storeIndex;
            }
            map.put(nums[i], i);
        }
        
        return nums;
    }
}
