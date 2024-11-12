
![기본형1](https://github.com/user-attachments/assets/a6845a3b-4e99-41e5-aec6-07d8ba0dd0d5)

## 오늘의 학습 키워드
Greedy - [문제 보러가기](https://www.acmicpc.net/problem/2847)
  
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
	
	int n, t, c = 0;
	cin >> n;
	vector<int> v;
	while (n--) {
		cin >> t;
		v.push_back(t);
	}

	for (int i = v.size() - 2; i >= 0; i--) {
		if (v[i + 1] <= v[i]) {
			c += v[i] - v[i + 1] + 1;
			v[i] = v[i + 1] - 1;
		}
	}
	cout << c;
}

```

<br>

## 오늘의 회고
### 문제 풀기 위한 전략
1. 배열의 마지막 원소는 무조건 가장 큰 숫자가 되어야 한다.
2. 배열을 역순으로 탐색해 전 원소보다 최소한(전 원소의 값 - 1) 작아져야 하므로 두 값을 빼서 카운트에 갱신
3. 원소 내용을 업데이트해서 다음 탐색에도 반영

<br>    
<br>
<br>
<br>
#99클럽 #코딩테스트준비 #개발자취업 #항해99 #TIL
