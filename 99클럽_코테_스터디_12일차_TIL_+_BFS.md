

![기본형1](https://github.com/user-attachments/assets/a6845a3b-4e99-41e5-aec6-07d8ba0dd0d5)

## 오늘의 학습 키워드
BFS - [문제 보러가기](https://www.acmicpc.net/problem/7569)
  
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

	int mx, my, mh;
	cin >> mx >> my >> mh;

	vector<vector<vector<int>>> map(mh, vector<vector<int>>(my, vector<int>(mx)));
	vector<vector<vector<int>>> visited(mh, vector<vector<int>>(my, vector<int>(mx)));
	queue<int> qx, qy, qh;
	int zeroCnt = 0;

	for (int h = 0; h < mh; h++) {
		for (int y = 0; y < my; y++) {
			for (int x = 0; x < mx; x++) {
				int v;
				cin >> v;
				map[h][y][x] = v;
				if (v == 1) {
					qx.push(x);
					qy.push(y);
					qh.push(h);

					visited[h][y][x] = 1;
				}
				else if (v == 0)
					zeroCnt++;
			}
		}
	}

	if (zeroCnt == 0)
	{
		cout << 0;
		return 0;
	}

	//오 앞 왼 뒤 위 아래
	int dirX[] = { 1,0,-1,0,0,0 };
	int dirY[] = { 0,1,0,-1,0,0 };
	int dirH[] = { 0,0,0,0,1,-1 };
	int max = 0;

	while (!qx.empty()) {
		int x = qx.front(); qx.pop();
		int y = qy.front(); qy.pop();
		int h = qh.front(); qh.pop();

		for (int i = 0; i < 6; i++) {
			int nx = x + dirX[i];
			int ny = y + dirY[i];
			int nh = h + dirH[i];

			if (nx < 0 || nx >= mx || ny < 0 || ny >= my || nh < 0 || nh >= mh)
				continue;

			if (visited[nh][ny][nx] == 0 && map[nh][ny][nx] == 0) {
				qx.push(nx);
				qy.push(ny);
				qh.push(nh);

				visited[nh][ny][nx] = visited[h][y][x] + 1;
				zeroCnt--;
				if (visited[nh][ny][nx] > max)
					max = visited[nh][ny][nx];
			}
		}
	}

	if (zeroCnt > 0)
		cout << -1;
	else
		cout << max - 1;
}
```

<br>

## 오늘의 회고
### 문제 풀기 위한 전략
![image](https://github.com/user-attachments/assets/0e927b26-1489-4a22-80fc-2a3772f77849)


1. 3차원 공간에서 BFS를 사용하는 문제
2. 모든 장소를 탐색하지 못한다면 -1, 이미 전부 익은 토마토라면 0을 출력
3. x,y,z 좌표, 큐를 사용해 너비 탐색 구현

<br>    
<br>
<br>
<br>
#99클럽 #코딩테스트준비 #개발자취업 #항해99 #TIL
