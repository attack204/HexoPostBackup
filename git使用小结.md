---
title: git使用小结
date: 2019-1-18 21:29:07
tags:
- git 
categories:
- 学习笔记 
---

<Excerpt in index >

记录一下，忘的太快了qwq

<!-- more -->

<The rest of contents >

首先需要弄好SSH，这一部分我早就弄好了，等以后需要重新弄的时候再更新吧

## 上传方法

1、首先进入文件夹，初始化工作目录

```cpp
git init
```

2、把文件都添加到暂存区中

```cpp
git add .
```

3、执行预提交命令

```cpp
git commit -m '提交说明'
```

4、关联到远程库

git remote add origin 你的远程库地址

远程仓库地址可以在这里获取

![](http://wx2.sinaimg.cn/small/005S5cb6ly1fzb22pkhaxj30v508rmxx.jpg)

5、获取远程库与本地同步合并（如果远程库不为空必须做这一步，否则后面的提交会失败）

```cpp
git pull --rebase origin master
```

6、把本地库的内容推送到远程，使用 git push命令

实际上是把当前分支master推送到远程。执行此命令后会要求输入用户名、密码，验证通过后即开始上传。(如果配好ssh的话则不需要输入用户名密码)

```cpp
git push -u origin master
```

## 常见错误

### nothing to commit, working tree clean

就是说没有什么可以更新的。。

### fatal: remote origin already exists.

说明重复输入了第四步

这时候只要输入`git remote rm origin`，再输入原命令就可以了

## 常用命令

![命令查询](http://wx2.sinaimg.cn/small/005S5cb6ly1fzb245et6lj316i0u0wvw.jpg)

## 参考资料

[如何用命令将本地项目上传到git](https://www.cnblogs.com/eedc/p/6168430.html)

[Git使用教程](http://www.cnblogs.com/tugenhua0707/p/4050072.html)



