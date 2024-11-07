

![기본형1](https://github.com/user-attachments/assets/a6845a3b-4e99-41e5-aec6-07d8ba0dd0d5)

## 오늘의 학습 키워드
DFS - [문제 보러가기](https://www.acmicpc.net/problem/25195)
  
<br>


## 제출한 코드
```
#include <vector>
#include <iostream>
#include <unordered_set>
using namespace std;

vector<vector<int>> adjlist;
unordered_set<int> fanclub;
string answer = "Yes";

void dfs(int n) {
	
	if (fanclub.find(n) != fanclub.end())
		return;

	int size = adjlist[n].size();

	if (size == 0)
	{
		answer = "yes";
		return;
	}

	for (int i = 0; i < size; i++) {
		dfs(adjlist[n][i]);
	}
}

int main() {
	cin.tie(0);
	cout.tie(0);
	ios::sync_with_stdio(false);

	int n, m;
	cin >> n >> m;
	adjlist.resize(n + 1);
	while (m--) {
		int from, to;
		cin >> from >> to;
		adjlist[from].push_back(to);
	}

	int s;
	cin >> s;
	while (s--)
	{
		int node;
		cin >> node;
		fanclub.insert(node);
	}

	dfs(1);
	cout << answer;
}
```

<br>

## 오늘의 회고
### 문제 풀기 위한 전략
![image](https://github.com/user-attachments/assets/a0f85922-de04-4f42-bfd8-0f9f4c76c6b1)

1. 이 문제는 팬을 피해서 갈수있는 길이 하나라도 있으면 yes, 없다면 YES를 출력하는 문제이다.
2. 탐색 중 팬을 만났다면 그 이상 탐색할 필요가 없으니 팬을 만났을때 "YES"를 출력하고 바로 dfs 종료
3. 길이 막다랐을 때(노드의 인접리스트 원소의 개수가 0일 때) 팬을 한번도 만나지 않았으므로 yes출력

<br>    
<br>
<br>
<br>
#99클럽 #코딩테스트준비 #개발자취업 #항해99 #TIL
