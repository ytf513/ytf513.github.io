---
layout: post
title: Jekyll安装过程错误处理
category: 技术
tags: [Jekyll, Web]
keywords: Jekyll,web,ruby
description: 
---

> 这并不是一帆风顺的过程

## 过程简介
本文是以Ubuntu为例，其他环境自行Google

1. 安装Jekyll之前，确保系统中已经安装：

> - Ruby(>=1.9.2)
> - RubyGems
> - Nodejs(之后安装也可以)

2. 安装Jekyll请使用`gem install jekyll`命令

## 遭遇的问题

### Q1：`apt-get install ruby-full`下载安装ruby找不到资源
系统提示需要更新已有的安装包，使用命令`sudo apt get update`,之后再下载就可以了；
源码安装方式,首先下载源码，解压后进入目录：

	$ ./configure
	$ make
	$ sudo make install

### Q2：`gem install jekyll`下载没响应，也没提示
其实并不是没反应，而是速度太慢，要查看下载过程，请输入命令`gem install jekyll -V`。整个过程很慢，半个小时都不止，最后很可能提示无法连接等错误。
解决办法：下载淘宝的镜像，首先是删除rubygems.org资源，添加淘宝资源，用gem source 查看资源：

```
$ gem sources --remove https://rubygems.org/
$ gem sources -a http://ruby.taobao.org/
$ gem sources -l
$ gem sources -u
```

### Q3: gem install jekyll提示ruby版本不足
错误如下：

```
ERROR:  Error installing jekyll:
	redcarpet requires Ruby version >= 1.9.2.
```

下载高版本：`sudo apt-get install ruby1.9.3`

### Q4:ruby -v 还算原来的版本
这是因为安装新版本后，并不会替换原来的版本（old version already exsits。
需要用到 rvm 管理版本，切换到1.9.3用
`rvm use 1.9.3`

## Jekyll功能介绍

Jekyll（发音('dʒiːk əl)，"杰克尔")是一个静态站点生成器，它会根据网页源码成4静态文件。它提供了模板、变量、插件等功能，所以实际上可以用来编写整个网站。整个思路到这里就很明显了。你先在本地编写符合Jekyll规范的网站源码，然后上传到github，由github生成并托管整个网站。


## 参考
1. Kekyll官网
2. [淘宝RubyGems和NPM镜像](http://hcy2367.github.io/2015/01/14/taobao-mirror.html)
