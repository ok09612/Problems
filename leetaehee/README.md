# LeetCode - 88. Merge Sorted Array

https://leetcode.com/problems/merge-sorted-array/
  
오름차순으로 정렬되어 있는 두 개의 배열을 병합정렬하기

```Java

class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int idx = 0;
        int idx1 = 0;
        int idx2 = 0;
        int len = m+n;
        int[] newArr = new int[m+n];
        int newLen = newArr.length;
        
        for(int i=0; i<len; i++) {
            if(idx1 >= m) {
                newArr[idx] = nums2[idx2];
                idx++;
                idx2++;
                continue;
            }
            else if(idx2 >= n) {
                newArr[idx] = nums1[idx1];
                idx++;
                idx1++;
                continue;
            }
            
            if(nums1[idx1] <= nums2[idx2]) {
                newArr[idx] = nums1[idx1];
                idx++;
                idx1++;
            } else if(nums1[idx1] > nums2[idx2]) {
                newArr[idx] = nums2[idx2];
                idx++;
                idx2++;
            }
        }
        
        for(int i=0; i<newLen; i++) {
            nums1[i] = newArr[i];
        }
    }
}


```

시간복잡도 : O(N)  
  
각 for문에서 m+n번의 시간이 소요된다. 그러므로 모두 합해 2(m+n)만큼 시간이 소요된다.
<br />