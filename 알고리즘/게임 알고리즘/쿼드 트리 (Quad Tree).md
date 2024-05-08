- 트리의 자식 노드가 4개인 트리를 의미한다.
- 게임에서는 일반적으로 지형 정보를 저장하는데 사용.
- 컬링을 위한 지형 검색에 쿼드 트리를 사용
	- 쿼드 트리를 이용하면 필요 없는 데이터를 큰 덩어리 단위로 버릴 수 있게 되므로 거대한 지형을 빠르게 검색할 수 있기 때문.

#### 예제
백준 1992
```c++
#include <bits/stdc++.h>

using namespace std;

int n;
int arr[64][64] = { 0 };

void func(int n, int y, int x)
{
	bool z = true, o = true;

	if (n == 1) {
		cout << arr[y][x];
		return;
	}
	for (int i = y; i < y + n; i++) {
		for (int j = x; j < x + n; j++) {
			if (arr[i][j])
				z = false;
			else
				o = false;
		}
	}
	if (z == true)
		cout << 0;
	else if (o == true)
		cout << 1;
	else {
		cout << "(";
		func(n / 2, y, x);
		func(n / 2, y, x + n / 2);
		func(n / 2, y + n / 2, x);
		func(n / 2, y + n / 2, x + n / 2);
		cout << ")";
	}
	return;
}

int main() 
{
	ios::sync_with_stdio(0);
	cin.tie(0);

	cin >> n;

	for (int i = 0; i < n; i++) {
		string str;
		cin >> str;
		for (int j = 0; j < n; j++)
			arr[i][j] = str[j] - '0';
	}
	
	func(n, 0, 0);
}
```