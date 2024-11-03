
![기본형1](https://github.com/user-attachments/assets/a6845a3b-4e99-41e5-aec6-07d8ba0dd0d5)

## 오늘의 학습 키워드
DFS - [문제 보러가기](https://school.programmers.co.kr/learn/courses/30/lessons/84512)
  
<br>

## 제출한 코드
```
#include <string>
#include <vector>
#include <iostream>

using namespace std;

int cnt = 0;
string target;
bool findTarget;

char GetNextAlphabet(char c) {
	if (c == 'A') return 'E';
	if (c == 'E') return 'I';
	if (c == 'I') return 'O';
	if (c == 'O') return 'U';
	if (c == 'U') return 0;
}

void dfs(string word) {
	if (word.size() >= 6)
		return;

	/*cout << word << endl;
	cout <<cnt++ << endl;*/

	cnt++;

	if (word == target) {
		findTarget = true;
		return;
	}

	dfs(word + 'A');

	if (findTarget)
		return;

	char nextAlphabet = GetNextAlphabet(word.back());

	if (nextAlphabet != 0) {
		word.back() = nextAlphabet;
		dfs(word);
	}
}

int solution(string word) {
	target = word;
	dfs("A");
	return cnt;
}

//int main() {
//	ios::sync_with_stdio(0);
//	cin.tie(0);
//	cout.tie(0);
//
//	cin >> target;
//	dfs("A");
//	cout << cnt;
//}
```

<br>

## 오늘의 회고
### 문제 풀기 위한 전략
1. 프로그래머스 2레벨 상단에 자주 보였지만 읽기만 하고 못풀었던 문제였다.
2. 이번 향해99덕분에 DFS에 좀 익숙해졌는데, 그때 당시 몰랐던 이 문제의 핵심 알고리즘이 DFS라는것을 깨달았다.
3. 문자열을 늘릴땐 무조건 뒤에 A추가, 6자이상일때 아무 작업도 안하게 하면. 생각보다 쉽게 구현할 수 있었다.

<br>    
<br>
<br>
<br>
#99클럽 #코딩테스트준비 #개발자취업 #항해99 #TIL
