# Problems
## Merge Intervals

<pre>
<code>
/**
 * @param {number[][]} intervals
 * @return {number[][]}
 */
var merge = function(intervals) {
      intervals.sort((a, b) => a[0] - b[0]);
  console.log(intervals);
  const result = [];
  let previous = intervals[0];
  
  for (let i = 1; i < intervals.length; i++) {
  	console.log("pre" ,previous[1] );
    console.log("cur" ,intervals[i][0]);
    if (previous[1] >= intervals[i][0]) {
    console.log( Math.max(previous[1], intervals[i][1]));
      previous = [previous[0], Math.max(previous[1], intervals[i][1])];
      console.log("pre", previous);
    } else {
      result.push(previous);
      previous = intervals[i];
    }
  }
  result.push(previous);
  
  return result;

};
</pre>
</code>
