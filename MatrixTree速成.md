---
title: MatrixTree速成
date: 2018-02-21 19:10:18
tags:
- oi
- 线性代数
- MatrixTree定理
---
<Excerpt in index | 首页摘要> 
MatrixTree定理是用来解决生成树计数问题的有利工具

比如说[这道题](https://www.luogu.org/problemnew/show/SP104)

MatrixTree定理的算法流程也非常简单

我们记矩阵$A$为无向图的度数矩阵
    记矩阵$D$为无向图的邻接矩阵
    
<!-- more -->

<The rest of contents | 余下全文>
## 前言
MatrixTree定理是用来解决生成树计数问题的有利工具

比如说[这道题](https://www.luogu.org/problemnew/show/SP104)

MatrixTree定理的算法流程也非常简单

我们记矩阵$A$为无向图的度数矩阵
    记矩阵$D$为无向图的邻接矩阵

$A$矩阵是除了对角线之外各个点值都为$0$的矩阵，$A[i][i]$表示$i$号点的度数

$D$矩阵记录两点之间的度数，$D[i][j]$表示$i$号点与$j$号点之间的边数

## MatrixTree定理

我们记矩阵$G=A-D$
那么$G$的所有不同生成树的个数等于$G$的任何一个 $n-1$ 阶主子式的行列式的绝对值

## 实现

MatrixTree定理的实现非常简单
1. 计算出$D$矩阵
2. 后对其进行高斯消元
3. 把消元后的矩阵的对角线乘起来
4. 输出

## 代码

就是上面那道题目的代码

```cpp
#include<cstdio>
#include<iostream>
#include<cstring>
#include<cmath>
using namespace std;
const int MAXN=3001;
const double eps=1e-12;
inline int read()
{
    char c=getchar();int x=0,f=1;
    while(c<'0'||c>'9'){if(c=='-')f=-1;c=getchar();}
    while(c>='0'&&c<='9'){x=x*10+c-'0';c=getchar();}
    return x*f;
}
double G[MAXN][MAXN],a[MAXN][MAXN];
char s[MAXN][MAXN];
int xx[5]={0,-1,+1,0,0};
int yy[5]={0,0,0,-1,+1};
int N,M;
int dcmp(int x)
{
    if(x<=eps||x>=-eps) return 0;
    else return x<0?-1:1;
}
void Gauss()
{
    N--;
    for(int i=1;i<=N;i++)//每一行 
    {
        int mx=i;
        for(int j=i+1;j<=N;j++)//下面的每一行 
            if(dcmp(G[mx][i]-G[j][i])<0) mx=j;
        if(mx!=i) swap(G[i],G[mx]);
        if(!G[i][i]) {printf("0\n");return ;}
        for(int j=i+1;j<=N;j++)
        {
            double t=G[j][i]/G[i][i];
            for(int k=i;k<=N+1;k++)
                G[j][k]-=t*G[i][k];
        }
    }
    double ans=1;
    for(int i=1;i<=N;i++) ans=ans*G[i][i];
    printf("%.0f\n",abs(ans));
}
int main()
{  
    int T=read();
    while(T--)
    {
        memset(G,0,sizeof(G));
        N=read(),M=read();
        for(int i=1;i<=M;i++)
        {
            int x=read(),y=read();
            G[x][x]++;G[y][y]++;
            G[x][y]--;G[y][x]--;
        }
        Gauss();  
    }
    return 0;  
}
```