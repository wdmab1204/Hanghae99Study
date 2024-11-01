
![기본형1](https://github.com/user-attachments/assets/a6845a3b-4e99-41e5-aec6-07d8ba0dd0d5)

## 오늘의 학습 키워드
BFS - [문제 보러가기](https://www.acmicpc.net/submit/24444/85926664)
  
<br>

## 제출한 코드
```
#include <string>
#include <vector>
#include <algorithm>
#include <queue>

using namespace std;

int main() {
	int n, m, r;
	scanf("%d%d%d", &n, &m, &r);

	vector<vector<int>> adjlist(n + 1);

	while (m--) {
		int from, to;
		scanf("%d%d", &from, &to);
		adjlist[from].push_back(to);
		adjlist[to].push_back(from);
	}

	for (int i = 1; i <= n; i++)
		sort(adjlist[i].begin(), adjlist[i].end());

	queue<int> q;
	vector<int> visited(n + 1);
	int cnt = 0;

	q.push(r);

	while (!q.empty()) {
		int node = q.front();
		q.pop();

		if (visited[node] != 0)
			continue;

		cnt++;
		visited[node] = cnt;

		for (int i = 0; i < adjlist[node].size(); i++) {
			q.push(adjlist[node][i]);
		}
	}

	for (int i = 1; i <= n; i++) {
		printf("%d\n", visited[i]);
	}
}
```

<br>

## 오늘의 회고
### 문제 풀기 위한 전략
1. 4일차에 풀었던 문제와 DFS가 BFS로 바뀐거 빼면 비슷하다 못해 똑같은 유형이다.
2. 대량의 인풋 개수, scanf와 printf를 사용해 비용을 줄였고 인접리스트를 활용해 그래프 정의
3. 각 인접리스트를 오름차순으로 정렬, 큐를 이용해 bfs 로직 구현.

<br>    
<br>
<br>
<br>
#99클럽 #코딩테스트준비 #개발자취업 #항해99 #TIL
