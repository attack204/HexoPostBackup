---
title: Berlekamp-Massey算法学习笔记
date: 2018-12-11 21:40:07
tags:
- oi
- Berlekamp-Massey算法
categories:
- oi
---

<Excerpt in index >

很久之前就听说过这个算法，当时六校联考的时候Day1T1是一道很有意思的递推，神仙zzx不会做于是就拿BM算法艹出了递推式Orzzzzzzzzzzx

<!-- more -->

<The rest of contents >


[推荐一篇讲的详细的不能再详细的博客](https://blog.csdn.net/qq_39972971/article/details/80725873)

我就不详细说了，只记一下自己感觉比较难理解的地方

设$r(m)$表示序列的递推式且长度为$m$

$f(r, i)$表示$\sum_{j = 1}^m r_j * a[i - j]$

$\delta(r, i)$表示$a[i] - f(r, i)$

$fail_i$表示第$i$个递推式出错的位置

对于某一个位置$i$，如果我们求出的$\delta(r, i) \not = 0$，这时候我们需要构造一个递推式$r'(m')$，满足$\forall j \in [m' + 1, i - 1] f(r', j) = 0$且$f(r, i) = \delta(r, i)$

这样我们令$r = r + r'$就得到新位置的递推式了

$r'$可以这么构造

设$mul = \frac{\delta(r, i)}{\delta(r, fail_{cnt - 1})}$

那么$r' = \{0, 0, 0 \dots, 0, mul, -mul * R_{cnt - 1} \}$

$0$的个数为$i - fail_{cnt - 1} - 1$

至于为什么这么构造是对的，我思考了挺长时间，简单的证明一下

首先对于$\forall j \in [m' + 1, i - 1]$, $\delta(r', j) = 0$

~~仔细想了想，，发现自己并不会证。。如果哪位大佬会的话可以教教本蒟蒻~~

感性理解就是因为$r$在$[1, M]$处满足任意位置为$0$，然后右移一下还满足？。。


至于为什么$f(r', i) = \delta(r, i)$

可以这么考虑，前$i - fail_{cnt - 1} - 1$个位置产生的贡献为$0$

$mul$产生的贡献为$mul * a_{fail_{cnt - 1}}$

$-mul * R_{cnt - 1}$产生的贡献为$-mul * (a[fail_{cnt - 1}] - \delta(r, fail_{cnt - 1]})$

合并同类项后可以得到$mul * \delta(r, fail_{cnt - 1}) = \delta(r, i)$

代码如下

```cpp
#include<bits/stdc++.h>
using namespace std;
const int MAXN = 2005;
const double eps = 1e-8;
int cnt, fail[MAXN];
double val[MAXN], delta[MAXN];
vector <double> ans[MAXN];
int main() {
	int N; scanf("%d", &N);
	for (int i = 1; i <= N; i++) scanf("%lf", &val[i]);
	for (int i = 1; i <= N; i++) {
		double tmp = val[i];
		for (int j = 0; j < ans[cnt].size(); j++)
			tmp -= ans[cnt][j] * val[i - j - 1];
		delta[i] = tmp;
		if (fabs(tmp) <= eps) continue;
		fail[cnt] = i;
		if (cnt == 0) {
			ans[++cnt].resize(i);
			continue;
		}
		double mul = delta[i] / delta[fail[cnt - 1]];
		cnt++; ans[cnt].resize(i - fail[cnt - 2] - 1);
		ans[cnt].push_back(mul);
		for (int j = 0; j < ans[cnt - 2].size(); j++)
			ans[cnt].push_back(ans[cnt - 2][j] * -mul);
		if (ans[cnt].size() < ans[cnt - 1].size()) ans[cnt].resize(ans[cnt - 1].size());
		for (int j = 0; j < ans[cnt - 1].size(); j++)
			ans[cnt][j] += ans[cnt - 1][j];
	}
	for (int i = 0; i < ans[cnt].size(); i++)
		cout << ans[cnt][i] << ' ';
	return 0;
}
```
