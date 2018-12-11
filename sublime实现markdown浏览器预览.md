---
title: sublime实现markdown浏览器预览
date: 2018-10-03 8:31:18
tags:
- sublime
---
<Excerpt in index | 首页摘要> 

利用sublime实现markdown浏览器预览

<!-- more -->

<The rest of contents | 余下全文>

## 效果预览

![](http://ou46et6i2.bkt.clouddn.com/18-9-27/33325638.jpg)

## 实现

首先下载插件`OmniMarkupPreviewer`

方法：`ctrl + shift + P`

![](https://ws1.sinaimg.cn/large/005S5cb6ly1fvo7xqsatzj30ct046dfv.jpg)

安装完成后搜索'OmniMarkupPreviewer'双击即可

下载完成后新建.md文件

按'ctrl + Alt + O'即可在浏览器内预览

注意这里可能会出现两个问题

### 404

打开浏览器后可能会出现404情况

更改方法如下

![](https://ws1.sinaimg.cn/large/005S5cb6ly1fvo84fvewhj30ay0abdg9.jpg)

加入代码

```cpp
{
    "renderer_options-MarkdownRenderer": {
        "extensions": ["tables", "fenced_code", "codehilite"]
    }
}
```

### Mathjax数学公式不支持

打开

![](https://ws1.sinaimg.cn/large/005S5cb6ly1fvo86hmencj30ao0a0wez.jpg)

把这里的'false'改为'true'，过一会儿重启sublime即可

![](https://ws1.sinaimg.cn/large/005S5cb6ly1fvo86w28qvj30cw03l3yl.jpg)