# Sort Colors

<pre>
<code>
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var sortColors = function(nums) {
    for(var i=0; i<nums.length; i++){
        for(var j=i; j<nums.length;j++){
            if(nums[j] < nums[i]){
                var x = nums[i];
                nums[i] = nums[j];
                nums[j] = x;
            }
        }
    }
    
    return nums;
};
</pre>
</code>

# 완주하지 못한 선수
<pre>
<code>
function solution(participant, completion) {
    var answer = '';
    //answer = participant.filter(x => !completion.includes(x) ).join("");
    participant.sort();
    completion.sort();
     for(var i=0; i<participant.length; i++){
         if(participant[i] !== completion[i]){
             answer = participant[i];
                 return answer;
         }
     }
    //return answer;
}
</pre>
</code>
