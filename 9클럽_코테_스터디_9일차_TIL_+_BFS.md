
![기본형1](https://github.com/user-attachments/assets/a6845a3b-4e99-41e5-aec6-07d8ba0dd0d5)

## 오늘의 학습 키워드
BFS - [문제 보러가기](https://www.acmicpc.net/problem/7562)
  
<br>

## 옛날 코드
```
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

struct pos {
	int y, x;
};

bool inarr(pos p, int len) {
	return p.x >= 0 && p.x < len && p.y >= 0 && p.y < len;
}

int bfs(pos s, pos e, int len) {
	queue<pos> q;
	int visit[300][300] = { 0 }, max_size = 0;
	int a[8] = { 1,2,2,1,-1,-2,-2,-1 };
	int b[8] = { -2,-1,1,2,2,1,-1,-2 };

	q.push(s);
	visit[s.y][s.x] = 1;

	while (!q.empty()) {
		pos tmp = q.front();
		q.pop();
		for (int i = 0; i < 8; i++) {
			pos next = { tmp.y + b[i],tmp.x + a[i] };
			if (visit[next.y][next.x] == 0 && inarr(next, len)) {
				q.push(next);
				visit[next.y][next.x] = visit[tmp.y][tmp.x] + 1;
				if (next.x == e.x && next.y == e.y) {
					return visit[e.y][e.x] - 1;
				}
			}
		}
	}
	return 0;
}

int main() {
	int map[300][300], N, len;
	scanf("%d", &N);
	while (N--) {
		pos s, e;
		scanf("%d %d %d %d %d", &len, &s.x, &s.y, &e.x, &e.y);
		printf("%d\n", bfs(s, e, len));
	}
    return 0;
}

```

## 제출한 코드
```
#include <vector>
#include <iostream>
#include <queue>
#include <vector>
using namespace std;

int bfs(int sx, int sy, int ex, int ey, int size) {
    queue<int> qx, qy;
    vector<vector<int>> visited(size, vector<int>(size));
    int dirX[] = { -2, -1, 1, 2, 2, 1, -1, -2 };
    int dirY[] = { 1, 2, 2, 1, -1, -2, -2, -1 };
    qx.push(sx);
    qy.push(sy);
    visited[sy][sx] = 1;

    while (!qx.empty()) {
        int x = qx.front(); qx.pop();
        int y = qy.front(); qy.pop();

        for (int i = 0; i < 8; i++) {
            int nx = x + dirX[i];
            int ny = y + dirY[i];

            if (nx < 0 || nx >= size || ny < 0 || ny >= size)
                continue;

            if (visited[ny][nx] == 0) {
                visited[ny][nx] = visited[y][x] + 1;
                qx.push(nx);
                qy.push(ny);
            }

            if (nx == ex && ny == ey)
                return visited[ny][nx] - 1;
        }
    }

    return -1;
}

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);

    int t, size, sx, sy, ex, ey;

    cin >> t;
    while (t--) {
        cin >> size >> sx >> sy >> ex >> ey;
        cout << bfs(sx, sy, ex, ey, size) << endl;
    }
}


```

<br>

## 오늘의 회고
### 문제 풀기 위한 전략
1. 이 문제는 5년전에 이미 풀었던 문제이며, BFS를 사용해서 풀었다.
2. 과거는 배열을 최대치만큼 미리 선언하고 풀었다면, 이번에는 벡터로 유동적으로 사이즈만큼만 사용했다.
3. 한번도 방문한 적이 없는 노드면 -1, 그렇지 않다면 그 노드의 방문순서를 출력했다.

<br>    
<br>
<br>
<br>
#99클럽 #코딩테스트준비 #개발자취업 #항해99 #TIL
