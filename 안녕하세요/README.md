```c++
#include <vector>
#include <cmath>
#include <algorithm>
#include <cstring>
#include <iostream>
using namespace std;

int dp[1000][1000];
class Solution {
private:

    /// <summary>
    /// 계산
    /// </summary>
    /// <param name="sum">부분합</param>
    /// <param name="stones">돌</param>
    /// <param name="left">시작 index</param>
    /// <param name="right">마지막 index</param>
    /// <returns></returns>
    int solve(vector<int>& sum, vector<int>& stones, int left, int right)
    {
        if (right - left < 1) {
            return 0;
        }

        int& result = dp[left][right];
        if (result >= 0) {
            return result;
        }
        // 왼
        result = max(result, subSum(sum, left + 1, right) - solve(sum, stones, left + 1, right));
        // 오
        result = max(result, subSum(sum, left, right - 1) - solve(sum, stones, left, right - 1));

        //// 왼왼
        //result = max(result, abs(subSum(stones, left + 1, right) - subSum(stones, left + 2, right)) + solve(sum, stones, left + 2, right));
        //// 왼오
        //result = max(result, abs(subSum(stones, left + 1, right) - subSum(stones, left + 1, right - 1)) + solve(sum, stones, left + 1, right - 1));
        //// 오왼
        //result = max(result, abs(subSum(stones, left, right - 1) - subSum(stones, left + 1, right - 1)) + solve(sum, stones, left + 1, right - 1));
        //// 오오
        //result = max(result, abs(subSum(stones, left, right - 1) - subSum(stones, left, right - 2)) + solve(sum, stones, left, right - 2));

        return result;
    }

    int subSum(vector<int>& subSum, int left, int right) {
        return subSum[right] - (left - 1 < 0 ? 0 : subSum[left - 1]);
    }

public:
    int stoneGameVII(vector<int>& stones) {
        vector<int> sum(stones.size());
        sum[0] = stones[0];
        for (int i = 1; i < stones.size(); i++) {
            sum[i] = sum[i - 1] + stones[i];
        }
        memset(dp, -1, sizeof(int) * (1000 * 1000));

        return solve(sum, stones, 0, stones.size() - 1);
    }
};

```
