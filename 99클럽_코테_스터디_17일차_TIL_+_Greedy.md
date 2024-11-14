

![기본형1](https://github.com/user-attachments/assets/a6845a3b-4e99-41e5-aec6-07d8ba0dd0d5)

## 오늘의 학습 키워드
Greedy - [문제 보러가기](https://www.acmicpc.net/problem/31926)
  
<br>


## 제출한 코드
```
#include <iostream>
using namespace std;

int main(void)
{
    int answer = 10;
    int n, i = 1, offset = 0;
    cin >> n;
    while (i <= n) {
        i *= 2;
        offset++;
    }

    cout << answer + offset - 1;

    return 0;
}
```

<br>

![image](https://github.com/user-attachments/assets/6ca27c99-c5ad-4415-be31-bd5bf75a6c2a)


## 오늘의 회고
### 문제 풀기 위한 전략
1. 코드를 작성하는건 어렵지 않았지만 로직을 깨닫는데 많은 시간을 들였다.

n=4 이고 daldidalgo를 X, daldidan을 Y로 치환했을 때
XXXXY는 첫번재 X는 8, 두번째는 1, 세네번째는 합쳐서 1의 비용이다.
n=8 일 때
XXXXXXXXY는 첫번째 X가 8, 두번째는 1, 세네번째는 1, 네번째~8번째까지 1이다.

문제의 패턴은 2의 배수를 활용하는 것이며 이 패턴의 숫자들을 나열했을 때

N=1  10<br> 
N=2  11<br> 
N=3  11<br> 
N=4  12<br> 
<br> 
...
<br> 
N=7  12<br> 
N=8  13<br> 
N=9  13<br> 
<br> 
...
<br> 
N=15  13<br> 
N=16  14<br> 
<br> 
이다.

2. N이 2의배수를 넘을 때마다 카운트를 1씩 해주는 방식을 이용하고 정답은 N=1인 10을 더하여 답을 출력하였다.

<br>    
<br>
<br>
<br>
#99클럽 #코딩테스트준비 #개발자취업 #항해99 #TIL
