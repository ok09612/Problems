# Problems


https://programmers.co.kr/learn/courses/30/lessons/12950
# 행렬의 덧셈 (LV1)
```js
function solution(arr1, arr2) {
    var answer = [];
    let leng = arr1.length;
    
    for (let i=0; i<leng; ++i) {
        let items = [];
        for (let j=0; j<arr1[i].length; ++j) {
            items.push(arr1[i][j] + arr2[i][j]);
        }
        answer.push(items);
    }
     
    return answer;
}
```


https://programmers.co.kr/learn/courses/30/lessons/12954
# x만큼 간격이 있는 n개의 숫자 (LV1)
```js
function solution(x, n) {
    var answer = [];
    
    let xx = 0;
    for (let k=0; k<n; ++k) {
        xx += x;
        answer.push(xx);
    }
    return answer;
}
```




