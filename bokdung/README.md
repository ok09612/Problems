# Problems
## FizzBuzz

<pre>
<code>
/**
 * @param {number} n
 * @return {string[]}
 */
var fizzBuzz = function(n) {
    
    const arr = [];
    for(var i=1; i<= n; i++){
        
        if(i%15=== 0){
            arr.push("FizzBuzz");
        }
        else if(i%5 === 0){
            arr.push("Buzz");
        }
        else if(i % 3 === 0){
            arr.push("Fizz");
        }else{
            arr.push(String(i));
        }
    }
    
    return arr;
};
</pre>
</code>

## Split a String Into the Max Number of Unique Substrings
<pre>
<code>
/**
 * @param {string} s
 * @return {number}
 */
var maxUniqueSplit = function(s) {
    // 주어진 string을 중복되지 않는 subset으로 구성 하였을 때 가장 긴 구성의 갯수는?
  let resultSet = dfs(s, new Set());
    return resultSet.size;
};

function dfs(s, set) {
    // console.log(set);
    if(s == '') return set;
    let result = new Set();
    for (let i = 1; i <= s.length; i++) {
        let left = s.substring(0, i);
        let right = s.substring(i);

        let nSet = new Set(set);

        if(nSet.has(left)) continue;
        nSet.add(left);

        let nnSet = dfs(right, nSet);
        if(result.size < nnSet.size){
            result = nnSet;
        }
    }
    return result;
}

</pre>
</code>