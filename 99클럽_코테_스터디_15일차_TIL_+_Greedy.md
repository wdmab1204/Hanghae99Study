

![기본형1](https://github.com/user-attachments/assets/a6845a3b-4e99-41e5-aec6-07d8ba0dd0d5)

## 오늘의 학습 키워드
Greedy - [문제 보러가기](https://www.acmicpc.net/problem/13417)
  
<br>


## 제출한 코드
```
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

int main() {
	cin.tie(0);
	cout.tie(0);
	ios::sync_with_stdio(false);
	
	int n, t;
	char c;
	cin >> n;
	while (n--) {
		cin >> t;
		vector<char> words;
		while (t--)
		{
			cin >> c;
			if (words.size() == 0)
				words.push_back(c);
			else if (words[0] < c)
				words.push_back(c);
			else
				words.insert(words.begin(), c);
		}

		for (int i = 0; i < words.size(); i++)
			cout << words[i];
		cout << endl;
	}
}
```

<br>

## 오늘의 회고
### 문제 풀기 위한 전략

1. 문자를 차례대로 받고 최대한 사전 오름차순에 가깝도록 알파벳 배치
2. 첫글자보다 현재 입력받은 알파벳이 더 크면 뒤로, 작다면 앞으로 배치

<br>    
<br>
<br>
<br>
#99클럽 #코딩테스트준비 #개발자취업 #항해99 #TIL
