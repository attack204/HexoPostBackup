---
title: css学习笔记
date: 2019-1-19 12:34:07
tags:
- css
categories:
- 学习笔记
---


<Excerpt in index >

css好神奇啊qwq

<!-- more -->

<The rest of contents >

## 简介

CSS 指层叠样式表 (Cascading Style Sheets)
- 样式定义如何显示 HTML 元素
- 样式通常存储在样式表中
- 把样式添加到 HTML 4.0 中，是为了解决内容与表现分离的问题
- 外部样式表可以极大提高工作效率
- 外部样式表通常存储在 CSS 文件中
- 多个样式定义可层叠为一

## 基础知识

## 基础语法

CSS 规则由两个主要的部分构成：选择器，以及一条或多条声明。

```cpp
selector {declaration1; declaration2; ... declarationN }
```

### 使用方法

#### 外部样式表

```css
<head>
    <link rel = "stylesheet" type = "text/css" href = "mystyle.css" />
</head>
```

该文件中只能含有样式表

```css
hr {color: sienna;}
p {margin-left: 20px;}
body {background-image: url("images/back40.gif");}
```

#### 内部样式表

直接在`<head>`标签内插入即可

```css
<head>
<style type="text/css">
  hr {color: sienna;}
  p {margin-left: 20px;}
  body {background-image: url("images/back40.gif");}
</style>
</head>
```

#### 内联样式

直接调用标签的`style`属性

```css
<p style="color: sienna; margin-left: 20px">
    This is a paragraph
</p>
```

### 选择器分组

对选择器分组后，同一组内的选择器会分享相同的声明

若一个选择器被凡在了多个组内，则会同时拥有每个组的样式，当样式冲突时，按规则选择样式

### 继承问题

大部分情况下会直接继承父亲的样式，但是可能会有浏览器兼容问题

## 样式

## 框模型

## 定位


## 选择器

### 派生选择器

派生选择器允许我们根据文档的上下文关系来确定某个标签的样式。

例如
```css
h2 strong {
    color: blue;
}
<strong>233</strong>
<h2>123<strong>233</strong>.</h2>
```

这样设置的话只有h2标签内的strong标签才会变蓝色

### id选择器

id 选择器可以为标有特定id的HTML元素指定特定的样式。

id 选择器以 "#" 来定义。

id选择器常用来建立派生选择器,且可以定义多次

效果：

![test](http://wx1.sinaimg.cn/large/005S5cb6ly1fzbrt9ws7nj305q03jt8h.jpg)

```html
<style>
    #attack p {
        color:blue
    }
    #attack span {
        font-size:23px;
    }
    #attack {
        color:pink;
    }
</style>

<body>
    <div id = "attack">
        123
        <p>123</p>
        <span>456</span>
    </div>
</body>
```

注意：

老版本的ie浏览器可能会忽略该规则，只需加一条定义就可以了

```css
div#sidebar {
	border: 1px dotted #000;
	padding: 10px;
}
```

### 类选择器

类选择器通常用y一个点'.'来表示，它对整个class属性为ClassName的标签进行渲染

class也可以构建派生选择器, 元素也可以基于它们的类而被选择(用于区分不同的标签)


```css
.ClassName {text-align: center}
```

```css
<style>
    .attack p {
        color:blue
    }
    div.attack {
        font-size:46px;
    }
</style>

<body>
    <div class = "attack">
        <p>123</p>
        <span>456</span>
    </div>
    <p class = "attack">123</p>
</body>
```

注意：

类名的第一个字符不能使用数字！

### 属性选择器

可以为拥有指定属性的 HTML 元素设置样式，而不仅限于 class 和 id 属性。

下面的例子为带有 title 属性的所有元素设置样式：

```css
[title] {
    color:red;
}
```

注意：

只有在规定了 !DOCTYPE 时，IE7 和 IE8 才支持属性选择器。在 IE6 及更低的版本中，不支持属性选择。

直接使用title选择器对p和a标签无效..(要你何用。)

## 细节问题

1. 当值为若干个单词时记得加引号

2. CSS本身对大小写并不敏感，但是当与HTML一起使用时对`class`和`id`的大小写敏感

#### 权重

由大到小排列

内联样式（在 HTML 元素内部）  

内部样式表（位于 `<head>` 标签内部）

外部样式表

浏览器缺省设置


