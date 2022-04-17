# Problems (그래프 및 노드 관련 문제 1개)


https://programmers.co.kr/learn/courses/30/lessons/43165?language=cpp
# 타겟 넘버 (LV2)
```cpp
// 못풀었지만 분석은 끝났다!
#include <string>
#include <vector>
using namespace std;

vector<int> numbers_;
int target_;
int answer = 0;
void dfs(int sum, int depth)
{
    if (depth == numbers_.size())
    {
        if (sum == target_)
            ++answer;            
       return;            
    }
    dfs(sum + numbers_[depth], depth + 1);
    dfs(sum - numbers_[depth], depth + 1);
}

int solution(vector<int> numbers, int target) {
    numbers_ = numbers;
    target_ = target;
    
    dfs(0, 0);
    return answer;
}```

