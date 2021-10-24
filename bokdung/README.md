# Problems
## Merge Sorted Array
### 주석처리된 부분은 맨처음 제출하고 틀린 코드
<pre>
<code>
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function(nums1, m, nums2, n) {
   
    // nums1 = nums1.concat(nums2);
     //nums1.sort((a,b) => a-b);
    
    //var count=0;
    for(let i=0; i< nums1.length; i++){
        if(i+1 > m){
          // count++;
            nums1[i] = nums2[i-m];
        }
    }
      //console.log(count);
    /*for(let i=0; i< count; i++){
       nums1.shift();
     }*/
  
    return nums1.sort((a,b) => a-b);
    
};
</code>
</pre>

