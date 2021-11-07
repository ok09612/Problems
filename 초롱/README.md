# https://leetcode.com/problems/palindrome-number/ -> javascript 사용
# 시간복잡도: O(n)

var isPalindrome = function(x) {
    let str = String(x);
    let y = str.split('').reverse().join('');
            console.log(y);
    if(y === str){
        return true;
    }else{
        return false;
    }
};
