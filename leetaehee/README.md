# LeetCode - 33. Search in Rotated Sorted Array

https://leetcode.com/problems/search-in-rotated-sorted-array/

임의의 위치에서 순서가 뒤바뀐 배열에서 원소찾기

```Java
class Solution {
    public int search(int[] nums, int target) {
        int len = nums.length;
        int start = 0, end = len-1, mid = 0;
        
        while(start <= end) {
            //찾고자하는 원소가 중간값이라면 중간 위치 리턴
            mid = (start + end) / 2;
            if(nums[mid] == target)
                return mid;
            
            //왼쪽이 정렬된 상태
            if(nums[start] <= nums[mid]) {
                //왼쪽 부분으로 검색 범위를 줄임
                if(nums[start] <= target && target < nums[mid]) {
                    end = mid-1;
                }
                //검색 범위를 오른쪽으로 변경함
                else {
                    start = mid+1;
                }
            }
            //오른쪽이 정렬된 상태
            else {
                //오른쪽으로 검색 범위를 줄임
                if(nums[mid] < target && target <= nums[end]) {
                    start = mid+1;
                }
                //검색 범위를 왼쪽으로 변경함
                else {
                    end = mid-1;
                }
            }
        }
        
        return -1;
        
    }
}
```

시간복잡도 : O(log N)
이진탐색 기법을 기반으로 배열을 탐색하여 log N의 시간복잡도를 가진다!
<br />