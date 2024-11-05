
![기본형1](https://github.com/user-attachments/assets/a6845a3b-4e99-41e5-aec6-07d8ba0dd0d5)

## 오늘의 학습 키워드
DFS - [문제 보러가기](https://www.acmicpc.net/problem/2644)
  
<br>

## 제출한 코드
```
#include <vector>
#include <algorithm>
#include <stdio.h>
#include <iostream>
using namespace std;

vector<int> visited;
vector<vector<int>> adjlist;
int e;

void dfs(int node) {

    for (int i = 0; i < adjlist[node].size(); i++) {
        int neighbor = adjlist[node][i];
        if (visited[neighbor] == 0) {
            visited[neighbor] = visited[node] + 1;
            dfs(neighbor);
        }
    }
}

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);

    int n, s, c;
    cin >> n >> s >> e >> c;

    adjlist.resize(n + 1);
    visited.resize(n + 1);

    while (c--) {
        int from, to;
        cin >> from >> to;
        adjlist[from].push_back(to);
        adjlist[to].push_back(from);
    }

    visited[s] = 1;
    dfs(s);

    if (visited[e] == 0)
        cout << -1;
    else
        cout << visited[e] - 1;
}

```

<br>

## 오늘의 회고
### 문제 풀기 위한 전략
1. 가족관계를 표현하는 노드와 간선의 형태는 마치 트리같지만 그래프 탐색에 사용했던 DFS를 그대로 사용해도 무방하다.
2. BFS를 사용해도 상관없지만 DFS의 숙련도를 더 높이기 위해 채용했다.
3. 한번도 방문한 적이 없는 노드면 -1, 그렇지 않다면 그 노드의 방문순서를 출력했다.

<br>    
<br>
<br>
<br>
#99클럽 #코딩테스트준비 #개발자취업 #항해99 #TIL
