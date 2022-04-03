- https://algospot.com/judge/problem/read/PICNIC O(n!)
```c++
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;


int matching(bool friends[10][10], bool selected[10], int size)
{
	int first = -1;
	for (int i = 0; i < size; i++) {
		if (selected[i] == false) {
			first = i;
			break;
		}
	}
	if (first == -1) {
		return 1;
	}
	int counter = 0;
	for (int j = first + 1; j < size; j++) {
		if (selected[j] == false && friends[first][j]) {
			selected[first] = selected[j] = true;
			counter += matching(friends, selected, size);
			selected[first] = selected[j] = false;
		}
	}
	return counter;
}

int main()
{
	int testCase;
	cin >> testCase;

	while (testCase--) {
		int n, m;
		bool friends[10][10] = { 0 };
		cin >> n >> m;

		for (int i = 0; i < m; i++) {
			int a, b;
			cin >> a >> b;
			friends[a][b] = friends[b][a] = true;
		}
		bool selected[10] = { 0 };

		cout << matching(friends, selected, n) << "\n";
	}
}
```

- 
