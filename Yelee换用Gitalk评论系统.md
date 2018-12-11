---
title: Yelee换用Gitalk评论系统
date: 2018-12-11 12:24:61
tags:
- Hexo
categories:
- Hexo
---

<Excerpt in index >

嗯。。又换了个评论系统

<!-- more -->

<The rest of contents >

## 步骤

主要还是因为我比较懒，而且valine的后台是在太难弄了。所以还是换成了第三方的评论系统`Gitalk`

- 首先[在这里](https://github.com/settings/applications/new)注册一个Github OAuth application

<img src="https://ws1.sinaimg.cn/large/005S5cb6ly1fy2p16kyj6j30jo0gatbx.jpg" width="500" hegiht="313" align=center />

- 在Yelee主题目录下的`_config.yml`中添加

```cpp
gitalk:
  on: true
  clientID: 'your clientID'
  clientSecret: 'your clientSecret'
  repo: 'attack204.github.io' # 仓库地址
  owner: 'attack204' # 拥有者
  admin: ['attack204'] # admin 用户
```

- 在`_partial/comments`下创建`gitalk.ejs`

注意！下面的`id`选项中如果按照原式方法填的话会出现`Error: Validation Failed`的问题

一个比较好的解决思路是直接填写`id: '<%= page.title %>'`

```cpp
<section id='comments' style='margin: 2em; padding: 2em; background: rgba(255, 255, 255, 0.5)'>
  <link rel="stylesheet" href="https://unpkg.com/gitalk/dist/gitalk.css">
  <script src="https://unpkg.com/gitalk@latest/dist/gitalk.min.js"></script>
  <div id="gitalk-container"></div>
  <script type="text/javascript">
    var gitalk = new Gitalk({
      clientID: '<%= theme.gitalk.clientID %>',
      clientSecret: '<%= theme.gitalk.clientSecret %>',
      repo: '<%= theme.gitalk.repo %>',
      owner: '<%= theme.gitalk.owner %>',
      admin: ['<%= theme.gitalk.owner %>'],
      id: window.location.pathname
    })
    gitalk.render('gitalk-container')
  </script>
</section>
```

 - 修改 _partial/article.ejs


```cpp
 <% if (!index && post.comments){ %>
    <% if (theme.duoshuo.on) { %>
      <%- partial('comments/duoshuo', {
          key: post.path,
          title: post.title,
          url: config.url+url_for(post.path),
          }) %>
    <% } else if (theme.youyan.on) { %>
        <%- partial('comments/youyan') %>
    <% } else if (theme.disqus.on) { %>
        <%- partial('comments/disqus', {
            shortname: theme.disqus.shortname
          }) %>
    <% } else if (config.disqus_shortname) { %>
        <%- partial('comments/disqus', {
            shortname: config.disqus_shortname
          }) %>
    <% } else if (theme.valine.on) { %>
        <%- partial('comments/valine', {
          key: post.slug,
          title: post.title,
          url: config.url+url_for(post.path)
        }) %>
+   <% } else if (theme.gitalk.on) { %>
+       <%- partial('comments/gitalk') %>
    <% } %>
<% } %>
```

## 参考资料

[更换博客评论系统](https://blog.wangriyu.wang/2018/03-valine.html)