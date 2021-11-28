# Generate Parentheses

<pre>
<code>
/**
 * @param {number} n
 * @return {string[]}
 */
var generateParenthesis = function(n) {
      const result = [];
    dfs(result, "", 0, 0, n);
    return result;
};

function dfs(result, s, left, right, n) {

    if (left === n && right === n) {
        result.push(s);
        return;
    }

    if (left < n) {
        dfs(result, s + "(", left + 1, right, n);
    }

    if (right < left) {
        dfs(result, s + ")", left, right + 1, n);
    }
};
</code>
</pre>
