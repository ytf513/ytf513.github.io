---
layout: post
title: 为博客新增了站内搜索和404页面定制 
category: 技术
tags: [Jekyll, Web]
keywords: Jekyll,web,ruby
description: 
---

> 写于2015年8月24日

## 站内搜索

![搜索效果图](http://7xlbds.com1.z0.glb.clouddn.com/github_blog_search_result.png)

使用了Google Custom Search Engine服务。具体步骤如下：

### 新增search.md文件
1. 登录cse,增加搜索引擎。设置网站地址、外观等。保存获取代码
2. 在根目录下新建`search.md`文件（布局、标题和index.md类似），把代码粘贴到后面

### 修改`_includes/nav.html <form id="search-form">`代码如下：

```js
<form id="search-form" action="{{site.search.action_url}}" method="get">
      <a href="/index.html" id="mobile-avatar" style="background-image:url({{ site.avatar }})"></a>
      <!-- NOTE: input field is disabled by default -->
      <input id="search-input" type="text" placeholder="Search..." name="q" >
</form>
```

### 在`_config.yml`中增加参数配置

```
# 站内搜索信息
search:
  action_url: http://ytf513.github.io/search.html
```
站内搜索的功能就宣告完成。

## 404页面定制

修改`404.html`为`404.md`,并更改代码为：

```js
---
layout: base
title: 404
---

404 Not Found Error

<script type="text/javascript" src="http://www.qq.com/404/search_children.js" charset="utf-8" homePageUrl="http://ytf513.github.io" homePageName="回到我的主页"></script>

```

此时，默认会跳到404 Not Found Errror页面，如果网络许可，则会跳到腾讯寻人界面，并有返回我的网站功能
