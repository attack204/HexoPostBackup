---
title: sublime实现一键代码格式化
date: 2018-010-2 21:35:18
tags:
- sublime
---
<Excerpt in index | 首页摘要> 

用Astyle实现sublime代码一键格式化

<!-- more -->

<The rest of contents | 余下全文>

## 效果预览
![](https://ws1.sinaimg.cn/large/005S5cb6ly1fvp25dryq1g30qu0j94qp.jpg)
## 实现

首先下载插件`SublimeAstyleFormatter`

方法：`ctrl + shift + P`后输入`install Package`。

等待一段时间后输入`SublimeAstyleFormatter`即可自动下载

## 使用方法

按下`ctrl + Alt + F`是默认格式化整个文件

按下`ctrl + K + F`即可格式化选中区域

该插件中有许多不同的风格可以选择

我比较习惯google代码风格，可以这样设置

![](https://ws1.sinaimg.cn/large/005S5cb6ly1fvp1nmvnxqj30f00b074x.jpg)

然后把第$28$行改为

        "style": "google",

![](https://ws1.sinaimg.cn/large/005S5cb6ly1fvp1oh2es1j30bg02574d.jpg)

完成！