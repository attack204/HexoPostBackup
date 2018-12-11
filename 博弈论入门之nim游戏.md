---
title: 博弈论入门之nim游戏
date: 2018-02-22 21:31:49
tags:
- oi
- 博弈论
- nim游戏
categories:
- oi
---

<Excerpt in index >

## nim游戏

> nim游戏

> 有两个顶尖聪明的人在玩游戏，游戏规则是这样的：

> 有$n$堆石子，两个人可以从任意一堆石子中拿任意多个石子(不能不拿)，没法拿的人失败。问谁会胜利


<!-- more -->

<The rest of contents >

nim游戏是巴什博奕的升级版(不懂巴什博奕的可以看[这里](http://attack204.com/2018/02/22/%E5%8D%9A%E5%BC%88%E8%AE%BA%E5%85%A5%E9%97%A8%E4%B9%8B%E5%B7%B4%E4%BB%80%E5%8D%9A%E5%A5%95/))

它不再是简单的一个状态，因此分析起来也棘手许多

如果说巴什博奕仅仅博弈论的一个引子的话，

nim游戏就差不多算是真正的入门了

## 博弈分析

面对新的博弈问题，我们按照套路，从简单的情况入手

当只有一堆石子的时候，先手可以全部拿走。先手必胜

当有两堆石子且石子个数相同的时候，先手不论拿多少，后手都可以从另一堆中拿同样多的石子，先手必败，否则先手必胜

当有三堆的时候呢？

当有$n$堆的时候呢？

这样玩下去却是很繁琐，不过前辈们总结出了一条非常厉害的规律！

## 定理解析

### 定理
对于nim游戏，前辈们发现了一条重要的规律！

当$n$堆石子的数量异或和等于$0$时，先手必胜，否则先手必败

### 证明


设$\oplus$表示[异或运算](https://baike.baidu.com/item/%E5%BC%82%E6%88%96/10993677?fr=aladdin)

nim游戏的必败态我们是知道的，就是当前$n$堆石子的数量都为零

设$a[i]$表示第$i$堆石子的数量，那么当前局面就是

$0 \oplus 0 \oplus 0 \oplus \dots \oplus 0 = 0 $

- 对于先手来说，如果当前局面是

$a_1 \oplus a_2 \oplus a_3 \oplus \dots \oplus a_n = k$

那么一定存在某个$a_i$，它的二进制表示在$k$最高位上一定是$1$

我们将$a_i \oplus k$，这样就变成了

$a_1 \oplus a_2 \oplus a_3 \oplus \dots \oplus a_n \oplus k = 0$

此时先手必胜

- 对于先手来说，如果当前局面是

$a_1 \oplus a_2 \oplus a_3 \oplus \dots \oplus a_n = k$

那么我们不可能将某一个$a_i$异或一个数字后使得

$a_1 \oplus a_2 \oplus a_3 \oplus \dots \oplus a_n = 0$

此时先手必败

## 代码

```cpp
#include<cstdio>
using namespace std;
int a[10001]; 
int main()
{
    int Test;
    scanf("%d",&Test);
    while(Test--)
    {
        int ans=0,N;
        scanf("%d",&N);
        for(int i=1;i<=N;i++) scanf("%d",&a[i]);
        for(int i=1;i<=N;i++) ans=ans^a[i];
        ans==0?printf("No\n"):printf("Yes\n");
    }
    return 0;
}
```

## 题目

临时还没有做太多题目，以后做多了慢慢补吧

- [洛谷P2197](https://www.luogu.org/problemnew/show/P2197)

[题解](http://www.cnblogs.com/zwfymqz/p/8458994.html)

- [POJ 1704](http://poj.org/problem?id=1704)

估计没几个人能一眼秒吧233

[题解](http://www.cnblogs.com/zwfymqz/p/8459698.html)

