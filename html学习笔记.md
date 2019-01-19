---
title: html学习笔记
date: 2019-1-18 18:42:07
tags:
- html
categories:
- 学习笔记
---


<Excerpt in index >

html好神奇啊qwq

记录一下颓的时候学的东西。

<!-- more -->

<The rest of contents >

# 标签

### body

存放网站的主体内容

### p

段落标签

```html
<p>123 </p>
```
<p>123 </p>

### hx

标题文本

一般分为6级

```html
<h1> </h1>
```

<h1> 123</h1>

### em, strong 

都可以表示强调内容。一般用strong多一些

```html
<strong> </strong> 
```

<strong> 123</strong>

### span

span是没有语义的，它的作用是为了`设置单独样式`

### q

q标签是短文本应用标签

网页会自动给其加上`""`

```html
<q> </q>
```

<q>123 </q>


### blockquote

长文本引用

```html
<blockquote> </blockquote>
```

<blockquote>明月出天山，苍茫云海间。长风几万里，吹度玉门关。汉下白登道，胡窥青海湾。由来征战地，不见有人还。 戍客望边色，思归多苦颜。高楼当此夜，叹息未应闲。</blockquote>

### br

分行标签

一般写为`<br/>`， html4.01后可写为`<br>`

```html
<br>
```

<br>

### &nbsp 空格

使用```&nbsp```可以给文本添加空格

```html
&nbsp
```

<p> &nbsp &nbsp &nbsp &nbsp 123 &nbsp <p/>

### hr

添加水平横线

html4.01版本``` <hr>`

xhtml1.0版本``` <hr />`

```html
<hr>
```

<hr>


### address

用于添加联系地址信息。默认为斜体


```html
<address>联系地址信息</address>
```

<address>联系地址信息</address>


### code

code标签可以加入一行代码


```html
<code>#include<iostream></code>
```
<code>#include<iostream></code>


### pre

pre标签可以插入大段代码


```html
<pre>
#include<iostream>
using namespace std;
int main() {
    puts("GG");
    return 0;
}
</pre>

```

<pre>
#include<iostream>
using namespace std;
int main() {
    puts("GG");
    return 0;
}
</pre>



### ul

ul为新闻信息列表，一般与li标签搭配使用

ul标签默认没有先后顺序

```html
<ul> 
    <li> a </li>
    <li> b </li>
    <li> c </li>
</ul>
```

<ul> 
    <li> a </li>
    <li> b </li>
    <li> c </li>
</ul>


### ol

ol标签与ul标签的区别在于ol标签有先后顺序


```html
<ol> 
    <li> a </li>
    <li> b </li>
    <li> c </li>
</ol>
```
<ol> 
    <li> a </li>
    <li> b </li>
    <li> c </li>
</ol>

### div

div标签应该是应用最广泛的标签，它可以把一些独立的逻辑部分划分出来，此时div标签充当了一个容器

```html
<div>
    123
</div>
```

<div>
    123
</div>


### table

table可以展示表格内容

其中又分为五个元素: table, tbody, tr, th, td

1、`<table>…</table>`：整个表格以`<table>`标记开始、`</table>`标记结束。

2、`<tbody>…</tbody>`：如果不加`<thead><tbody><tfooter>` , table表格加载完后才显示。加上这些表格结构， tbody包含行的内容下载完优先显示，不必等待表格结束后在显示，同时如果表格很长，用tbody分段，可以一部分一部分地显示。（通俗理解table 可以按结构一块块的显示，不在等整个表格加载完后显示。）

3、`<tr>…</tr>`：表格的一行，所以有几对tr 表格就有几行。

4、`<td>…</td>`：表格的一个单元格，一行中包含几对`<td>...</td>`，说明一行中就有几列。

5、`<th>…</th>`：表格的头部的一个单元格，表格表头。

6、表格中列的个数，取决于一行中数据单元格的个数

```html
<table>
    <tr>
        <th> 1 </th>
        <th> 2 </th>
        <th> 3 </th>
    </tr>
    <tr>
        <td> 1 </td>
        <td> 2 </td>
        <td> 3 </td>
    </tr>
    <tr>
        <td> 4 </td>
        <td> 5 </td>
        <td> 6 </td>
    </tr>
</table>
```

<table>
    <tr>
        <th> 1 </th>
        <th> 2 </th>
        <th> 3 </th>
    </tr>
    <tr>
        <td> 1 </td>
        <td> 2 </td>
        <td> 3 </td>
    </tr>
    <tr>
        <td> 4 </td>
        <td> 5 </td>
        <td> 6 </td>
    </tr>
</table>



### summary与caption

summary可以为表格提供摘要，摘要默认不显示

caption可以为表格添加标题


```html
<table summary = "test">
    <caption> My table </caption>
    <tr>
        <th> 1 </th>
        <th> 2 </th>
        <th> 3 </th>
    </tr>
    <tr>
        <td> 1 </td>
        <td> 2 </td>
        <td> 3 </td>
    </tr>
    <tr>
        <td> 4 </td>
        <td> 5 </td>
        <td> 6 </td>
    </tr>
</table>
```
<table summary = "test">
    <caption> My table </caption>
    <tr>
        <th> 1 </th>
        <th> 2 </th>
        <th> 3 </th>
    </tr>
    <tr>
        <td> 1 </td>
        <td> 2 </td>
        <td> 3 </td>
    </tr>
    <tr>
        <td> 4 </td>
        <td> 5 </td>
        <td> 6 </td>
    </tr>
</table>



### a

a标签可以实现超链接

加入`target = "_blank"`可以实现在新标签页内打开

在href使用mailto可以链接email地址

![](http://wx4.sinaimg.cn/mw690/005S5cb6ly1fzavtzhjpnj313o0fadg4.jpg)

```html
<a  href="http://www.baidu.com"  title="鼠标滑过显示的文本">链接显示的文本</a>

<a  href="http://www.baidu.com"  title="鼠标滑过显示的文本" target = "_blank">链接显示的文本</a>

<a  href="mailto:757394026@qq.com"  title="鼠标滑过显示的文本">在当前页面打开</a>
```

<a  href="http://www.baidu.com"  title="鼠标滑过显示的文本">在新页面打开</a>

<a  href="http://www.baidu.com"  title="鼠标滑过显示的文本" target = "_blank">链接显示的文本</a>

<a  href="mailto:757394026@qq.com"  title="鼠标滑过显示的文本">链接邮件</a>



### img

img标签可以插入图片

```html
<img src="http://wx4.sinaimg.cn/mw690/005S5cb6ly1fzavtzhjpnj313o0fadg4.jpg" alt="下载失败时的替换文本" title = "提示文本">
```

<img src="http://wx4.sinaimg.cn/mw690/005S5cb6ly1fzavtzhjpnj313o0fadg4.jpg" alt="下载失败时的替换文本" title = "提示文本">

### form表单标签

表单可以把浏览者输入的数据传送到服务器端，这样服务器端程序就可以处理表单传过来的数据。

1. `<form> ：<form>`标签是成对出现的，以`<form>`开始，以`</form>`结束。

2.action ：浏览者输入的数据被传送到的地方,比如一个PHP页面(save.php)。

3.method ： 数据传送的方式（get/post）。

注意:

1、所有表单控件（文本框、文本域、按钮、单选框、复选框等）都必须放在 <form></form> 标签之间（否则用户输入的信息可提交不到服务器上哦！）。

2、method : post/get 的区别这一部分内容属于后端程序员考虑的问题。感兴趣的小伙伴可以查看本小节的 wiki，里面有详细介绍。



```html
<form method="传送方式" action="服务器文件">

<form method="post"   action="save.php">
        <label for="username">用户名:</label>
        <input type="text" name="username" />
        <label for="pass">密码:</label>
        <input type="password" name="pass" />
</form>
```

<form method="post"   action="save.php">
        <label for="username">用户名:</label>
        <input type="text" name="username" />
        <label for="pass">密码:</label>
        <input type="password" name="pass" />
</form>

### label标签

label标签不会向用户呈现任何特殊效果，它的作用是为鼠标用户改进了可用性。如果你在 label 标签内点击文本，就会触发此控件。就是说，当用户单击选中该label标签时，浏览器就会自动将焦点转到和标签相关的表单控件上（就自动选中和该label标签相关连的表单控件上）。


```html
<label for="控件id名称">

<form>
    你对什么运动感兴趣？<br>
    <label for="SlowRun">慢跑</label> <input type="checkbox" id="SlowRun"/> <br>
    <label for="Climb">登山</label> <input type="checkbox" id="Climb"/> <br>
    <label for="Basketball">篮球</label> <br>
</form>
```
<form>
    你对什么运动感兴趣？<br>
    <label for="SlowRun">慢跑</label> <input type="checkbox" id="SlowRun"/> <br>
    <label for="Climb">登山</label> <input type="checkbox" id="Climb"/> <br>
    <label for="Basketball">篮球</label> <br>
    
</form>



### input文本/密码输入框

就是一个输入框，

1、type：

   当type="text"时，输入框为文本输入框;

   当type="password"时, 输入框为密码输入框。

2、name：为文本框命名，以备后台程序ASP 、PHP使用。

3、value：为文本输入框设置默认值。(一般起到提示作用)

```html
<form>
   <input type="text/password" name="名称" value="文本" />
</form>
```

<form>
   <input type="text/password" name="名称" value="文本" />
</form>

### input提交按钮

当用户需要提交表单信息到服务器时，需要用到提交按钮。

type：只有当type值设置为submit时，按钮才有提交作用

value：按钮上显示的文字

```html
<input   type="submit"   value="提交">
```

<input   type="submit"   value="提交">

### input重置按钮

重置按钮可以使表单内容恢复到最初始的样子



```html
<form method = "post" action = "save.php">
    <label for = "myName"> 姓名：</label>
    <input type = "text" value = "123" name = "myName" />
    <input type = "reset" value = "重置" name = resertBtn">
</form>
```

<form method = "post" action = "save.php">
    <label for = "myName"> 姓名：</label>
    <input type = "text" value = "123" name = "myName" />
    <input type = "reset" value = "重置" name = resertBtn">
</form>

### input单选框，复选框

就是单选框和复选框，以name属性来区分每一组。

1、type:

   当 type="radio" 时，控件为单选框

   当 type="checkbox" 时，控件为复选框

2、value：提交数据到服务器的值（后台程序PHP使用）

3、name：为控件命名，以备后台程序 ASP、PHP 使用

4、checked：当设置 checked="checked" 时，该选项被默认选中

```html
<input type="radio/checkbox" value="值" name="名称" checked="checked"/>
```

<input type="radio/checkbox" value="值" name="名称" checked="checked"/>


### textarea 文本域

可以让用户输入大段文字


1、`<textarea>`标签是成对出现的，以`<textarea>`开始，以`</textarea>`结束。

2、cols ：多行输入域的列数。

3、rows ：多行输入域的行数。

4、在`<textarea></textarea>`标签之间可以输入默认值。

```html
<form  method="post" action="save.php">
        <label>联系我们</label>
        <textarea cols="50" rows="10" >在这里输入内容...</textarea>
</form>
```

<form  method="post" action="save.php">
        <label>联系我们</label>
        <textarea cols="50" rows="10" >在这里输入内容...</textarea>
</form>

### select下拉列表框

select标签可以实现一个下拉列表框

1、value 是服务器提交的值

2.、selected="selected"：

设置selected="selected"属性，则该选项就被默认选中。

3、在标签内设置```multiple = "multiple```属性可以进行多选

```html
<form action="save.php" method="post" >
    <label>爱好:</label>
    <!-- <select multiple = "multiple"> -->
      <select>
      <option value="看书">看书</option>
      <option selected="selected" value="旅游">旅游</option>
      <option value="运动">运动</option>
      <option value="购物">购物</option>
    </select>
</form>
```

<form action="save.php" method="post" >
    <label>爱好:</label>
    <!-- <select multiple = "multiple"> -->
      <select>
      <option value="看书">看书</option>
      <option selected="selected" value="旅游">旅游</option>
      <option value="运动">运动</option>
      <option value="购物">购物</option>
    </select>
</form>


### 


```html
<></>
```

<></>

### 


```html
<></>
```

<></>



# 标签的属性

分为全局属性和部分属性

### 全局属性

#### id 

id是规定元素的唯一id，每个元素的id必须是互不相同的


