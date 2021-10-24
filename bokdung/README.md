# Problems
## 나선행렬
### 처음에 x,y로만 지정한다음 하니 머리가 복잡해져서 다른 코드 참고함.
### 행열의 시작,끝을 지정하고 하니 훨씬 수월.
<pre>
<code>
/**
 * @param {number[][]} matrix
 * @return {number[]}
 */
var spiralOrder = function(matrix) {
    
    //각 방향
	let rowBegin = 0,
	    rowEnd = matrix.length - 1,
	    colBegin = 0,
	    colEnd = matrix[0].length - 1;

	let result = [];
	while(rowBegin <= rowEnd && colBegin <= colEnd){

		//right
		for(let i= colBegin; i<= colEnd; i++){
				result.push(matrix[rowBegin][i]); //[0,0], [0,1], [0,2]
		}
		rowBegin++; // 처음행 끝 다음 행이 시작됨, rowBegin = 1;

		//down
		for(let i=rowBegin; i<= rowEnd; i++){ //rowBegin=1 rowEnd=2 colEnd=2
				result.push(matrix[i][colEnd]); //[1,2], [2,2]
		}
		colEnd--; // 열의끝을 도달했으니 이전 열의끝이 마지막이됨,colEnd=1;

		//left
		if(rowBegin <= rowEnd){ //1 <= 2 
				for(let i=colEnd; i >= colBegin; i--){ //colEnd=1 colBegin=0 rowEnd=2
						result.push(matrix[rowEnd][i]); //[2,1] , [2,0]
				}
		}
		rowEnd--; // 마지막행을 도달했으니 이전 행이 마지막이됨, rowEnd=1;

		//up
		if(colBegin <= colEnd){ //0 <= 1
				for(let i=rowEnd; i >= rowBegin; i--){ //rowEnd=1 rowBegin=1
						result.push(matrix[i][colBegin]); //[1,0]
				}
		}
		colBegin++; // 처음열 끝 다음 열이 시작됨, colBegin=1
	}

	return result;
};
</code>
</pre>