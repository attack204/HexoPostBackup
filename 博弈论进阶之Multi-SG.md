---
title: 博弈论进阶之Multi-SG
date: 2018-02-25 16:53:07
tags:
- oi
- 博弈论
- Multi-SG
categories:
- oi
---

<Excerpt in index >
## Multi-Nim

从最简单的Nim模型开始

它的定义是这样的
>有$n$堆石子，两个人可以从任意一堆石子中拿任意多个石子(不能不拿)**或把一堆数量不少于$2$石子分为两堆不为空的石子**，没法拿的人失败。问谁会胜利
<!-- more -->

<The rest of contents >

## 博弈分析

这个问题的本质还是Nim游戏，可以利用[SG定理](http://attack204.com/2018/02/23/%E5%8D%9A%E5%BC%88%E8%AE%BA%E8%BF%9B%E9%98%B6%E4%B9%8BSG%E5%87%BD%E6%95%B0/)来解释

通过观察不难不发现，操作一与普通的Nim游戏等价

操作二实际上是将一个游戏分解为两个游戏，根据SG定理，我们可以通过异或运算把两个游戏连接到一起，作为一个后继状态

煮个栗子

SG(3)的后继状态有$\{ (0),(1),(2),(1,2) \}$他们的SG值分别为$\{ 0,1,2,3 \}$，因此$SG(3)=mex\{ 0,1,2,3 \}=4$

另外这种游戏还有一个非常神奇的性质

$$SG\left( x\right) =\begin{cases}x-1\left( x\mod4=0\right) \\ x\left( x\mod4=1 \lor 2\right) \\ x+1\left( x\mod4=3\right) \end{cases}$$

然后把这个结论背过就好啦233

## Multi-SG

根据上面的游戏，我们定义Multi-SG游戏

- Multi-SG 游戏规定，在符合拓扑原则的前提下，一个单一游戏的`后继`可以为`多个单一游戏`。
- Multi-SG其他规则与SG游戏相同。

注意在这里要分清楚`后继`与`多个单一游戏`

对于一个状态来说，不同的划分方法会产生多个不同的后继，而在一个后继中可能含有多个独立的游戏

一个后继状态的SG值即为后继状态中独立游戏的异或和

该状态的SG值即为后继状态的SG值中未出现过的最小值


## 例题

难度跨度好大啊QWQ。。

直接放题解吧

[HDU 3032](http://www.cnblogs.com/zwfymqz/p/8464819.html)

[POJ 2311](http://www.cnblogs.com/zwfymqz/p/8465524.html)

[BZOJ 2940](http://www.cnblogs.com/zwfymqz/p/8468781.html)

[BZOJ 1188](http://www.cnblogs.com/zwfymqz/p/8469290.html)

[洛谷 3235](https://www.luogu.org/problemnew/show/P3235)
