# 练习 5.5
```
#include<iostream>
#include<string>
#include<vector>
#include<iterator>
#include<cstring>

using namespace std;

/*100分对应A++ 低于60 F 60-69 D 70-79 C 80-89 B 90-99 A */

int main() {
	const vector <string>  s1 = { "F","D","C","B","A","A++"};
	string gradeletter;
	int a1;
	cin >> a1;

	if (a1 < 60) {
		gradeletter = s1[0];
	}
	else {
		gradeletter = s1[((a1-60) / 10) + 1];
		if (a1 != 100) {
			if (a1 % 10 > 7) {
				gradeletter += "+";
			}
			else if(a1 % 10 < 4){
				gradeletter += "-";
			}
		}
	}
	cout << gradeletter;
}
```
# 练习 5.7
(a)

```
	if (ival1 != ival2) {
		ival1 = ival2;
	}
	else {
		ival1 = ival2 = 0;
	}
```
(b)
```
	if (ival < minval) {
		minval = ival;
	}
	occurs = 1;
```
# 练习 5.8
给定的else和哪个if匹配？

C++规定else与尚未匹配的if匹配。
