# PTA_7-18
# 二分法求多项式单根
# 题目到PTA里找吧
```cpp
#include<iostream>
#include<iomanip>
#include<cmath>
using namespace std;

double f(double x, double a3, double a2, double a1, double a0) {
return a3 * x * x * x + a2 * x * x + a1 * x + a0;
}

int main() {

double a3, a2, a1, a0;
double a, b;
cin >> a3 >> a2 >> a1 >> a0;
cin >> a >> b;

const double eps = 0.01;
const double fEps = 1e-12;

if (fabs(f(a, a3, a2, a1, a0)) < fEps) {
	cout << fixed << setprecision(2) << a << endl;
	return 0;
}
if (fabs(f(b, a3, a2, a1, a0)) < fEps) {
	cout << fixed << setprecision(2) << b << endl;
	return 0;
}

if (f(a, a3, a2, a1, a0) * f(b, a3, a2, a1, a0) > 0) {
	return -1;
}

double mid ; 
while (b - a >= eps ) {
	mid = (a + b) / 2; 
	if (fabs(f(mid, a3, a2, a1, a0)) < fEps) {
		break;
	}
	if (f(mid, a3, a2, a1, a0) * f(a, a3, a2, a1, a0) < 0) {
		b = mid;
	}
	else {
		a = mid;
	}
}
mid = (a + b) / 2;
cout << fixed << setprecision(2) << mid << endl;

return 0;

}