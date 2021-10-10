[Spiral Matrix - LeetCode](https://leetcode.com/problems/spiral-matrix/) O(MN)

```c++
int dir[][2] = { {0,1}, {1,0}, {0,-1}, {-1, 0} };

class Solution {
private:
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> answer;
        vector<vector<bool>> visit(matrix.size(), vector<bool>(matrix[0].size()));
        int nr = 0, nc = 0, d = 0;

        int size = matrix.size() * matrix[0].size();
        while (answer.size() < size) {
            visit[nr][nc] = true;
            answer.push_back(matrix[nr][nc]);
            nr += dir[d][0];
            nc += dir[d][1];
           

            if (nr < 0 || nc < 0 || nr >= matrix.size() || nc >= matrix[0].size() || visit[nr][nc]) {
                nr -= dir[d][0];
                nc -= dir[d][1];
                
                d = (d + 1) % 4;

                nr += dir[d][0];
                nc += dir[d][1];
            }
        }

        return answer;
    }
};
```

