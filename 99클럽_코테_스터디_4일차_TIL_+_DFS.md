![기본형1](https://github.com/user-attachments/assets/59c8f098-d17c-4c81-a65c-d6147f20a611)

<br>

### 목차
> 1. [오늘의 학습 키워드](#오늘의-학습-키워드)
> 2. [제출한 코드](#제출한-코드)
> 3. [오늘의 회고](#오늘의-회고)

<br><br>

## 오늘의 학습 키워드
DFS - [문제 보러가기](https://www.acmicpc.net/problem/24479)
  
<br>

## 제출한 코드
### 실패한 코드
```
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> visited;
vector<vector<int>> adjlist;
int cnt = 1;

void dfs(int node) {
    for (int i = 0; i < adjlist[node].size(); i++) {
        int neighbor = adjlist[node][i];
        if (visited[neighbor] == 0) {
            visited[neighbor] = cnt++;
            dfs(neighbor);
        }
    }
}

int main() {
    int n, e, s;
    cin >> n >> e >> s;

    adjlist.resize(n + 1);
    while (e--) {
        int f, t;
        cin >> f >> t;
        adjlist[f].push_back(t);
        adjlist[t].push_back(f);
    }

    for (int i = 0; i < adjlist.size(); i++) {
        sort(adjlist[i].begin(), adjlist[i].end());
    }

    visited.resize(n + 1);
    visited[s] = cnt++;
    if (adjlist[s].size() == 0)
        visited[s] = 0;

    dfs(s);

    for (int i = 1; i < visited.size(); i++) {
        cout << visited[i] << endl;
    }
}

```

<br>

### 성공한 코드
```
#include <vector>
#include <algorithm>
#include <stdio.h>
using namespace std;

vector<int> visited;
vector<vector<int>> adjlist;
int cnt = 0;

void dfs(int node) {
    if (visited[node] != 0)
        return;
    cnt++;
    visited[node] = cnt;

    for (int i = 0; i < adjlist[node].size(); i++) {
        int neighbor = adjlist[node][i];
        dfs(neighbor);
    }
}

int main() {
    int n, e, s;
    scanf("%d%d%d", &n, &e, &s);

    adjlist.resize(n + 1);
    visited.resize(n + 1);
    while (e--) {
        int f, t;
        scanf("%d%d", &f, &t);
        adjlist[f].push_back(t);
        adjlist[t].push_back(f);
    }

    for (int i = 0; i <= n; i++) {
        sort(adjlist[i].begin(), adjlist[i].end());
    }

    dfs(s);

    for (int i = 1; i <= n; i++) {
        printf("%d\n", visited[i]);
    }
}

```

<br>

## 오늘의 회고
### 문제 풀기 위한 전략
1. 문제에서 친절하게 DFS구현방법 까지 나와있었지만 정점과 간선의 개수가 최대 20만개여서 시간초과와 메모리초과가 빈번히 일어났습니다.
2. 메모리초과는 인접리스트를 DFS의 매개변수로 넘겼더니 재귀호출할 때 마다 그만큼 메모리가 늘어나 발생하였습니다. 인접리스트를 전역변수로 바꿔주니 그 이후로 더이상 메모리 초과가 나타나지 않았습니다.
3. 시간초과는 처음에 인접리스트를 정렬하는 부분이 원인일것이라고 생각했습니다. 그래서 우선순위큐를 쓰거나, 인접배열로 바꾸는 등 다양한 시도를 해봤지만 소용이 없었습니다.
4. cout, cin을 printf, scanf로 바꿨더니 시간초과를 해결했습니다. 의외로 정렬이 원인이 아니였고 입출력이였다는 점이 허무하면서도 cin cout의 성능을 깨닫게 되었습니다.
5. 다음부턴 입력개수가 많고 시간초과가 일어난다면 입출력을 다시 생각해보는 습관을 길러야겠습니다.
   <br>

<br>    
<br>
<br>
<br>

#99클럽 #코딩테스트준비 #개발자취업 #항해99 #TIL
