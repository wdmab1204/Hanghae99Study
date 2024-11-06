
![기본형1](https://github.com/user-attachments/assets/a6845a3b-4e99-41e5-aec6-07d8ba0dd0d5)

## 오늘의 학습 키워드
BFS - [문제 보러가기](https://www.acmicpc.net/problem/18352)
  
<br>


## 제출한 코드
```
#include <vector>
#include <iostream>
#include <queue>

using namespace std;
int main() {
	cin.tie(0);
	cout.tie(0);
	ios::sync_with_stdio(false);
	
	int n, m, k, x;
	cin >> n >> m >> k >> x;

	vector<vector<int>> adjlist(n + 1);
	while (m--) {
		int from, to;
		cin >> from >> to;
		adjlist[from].push_back(to);
	}

	queue<int> q;
	vector<int> visited(n + 1);

	q.push(x);
	visited[x] = 1;

	while (!q.empty()) {
		int n = q.front();
		q.pop();

		for (int i = 0; i < adjlist[n].size(); i++) {
			int next = adjlist[n][i];
			if (visited[next] == 0) {
				visited[next] = visited[n] + 1;
				q.push(next);
			}
		}
	}

	bool canFind = false;
	for (int i = 1; i < visited.size(); i++) {
		if (visited[i] == k + 1) {
			cout << i << endl;
			canFind = true;
		}
	}

	if (canFind == false)
		cout << -1;
}

```

<br>

## 오늘의 회고
### 문제 풀기 위한 전략
1. 노드외 간선의 최대갯수가 각각 30만, 100만개이기 때문에 입출력 비용을 감소시키는 작업을 했다.
2. bfs로 방문한 노드에 순번을 매겨 각각 이동거리를 구했고, k로 비교하여 똑같은 숫자대로 출력했다.

<br>    
<br>
<br>
<br>
#99클럽 #코딩테스트준비 #개발자취업 #항해99 #TIL
