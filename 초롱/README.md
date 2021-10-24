# 8. Merge Sorted Array -> Javascript
# 시간복잡도 : O(n)

var merge = function(nums1, m, nums2, n) {
    for(let i = 0; i < nums1.length; i++) {
        if(i >= m) {
            nums1[i] = nums2[i-m];
        }
    }
    return nums1.sort((a,b) => a-b);
}
