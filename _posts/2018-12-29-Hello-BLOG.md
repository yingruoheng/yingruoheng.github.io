---
layout:     post
title:      Hello Bolg
subtitle:    "\"Hello World, Hello Blog\""
date:       2018-12-29
author:     RH
header-img: img/post-bg-hello-blog.jpg
catalog: true
tags:
    - 生活
---

> “🙉🙉🙉 ”


## 前言

哇 期待了很久的博客终于开通啦。

其实很早以前就打算搭一个自己的博客了，之前在CSDN和博客园发过一些文章，但总觉得不在自己的网站上写东西不自在，所以就被我拖到了现在(其实是因为太懒了哈哈哈。。)

[跳过废话，直接看技术实现 ](#build) 

搭这个博客的目的呢，主要是想有个记录自己技术成长轨迹的地方，顺便也可以分享下生活日常。自己搭建的东西维护起来也更有动力一点不是嘛😆。我一直认为，对技术人员来说分享交流是一件很重要的事情，可能在有些公司这种机会比较少，所以我觉得博客应该是比较好的一个方式了。

![](https://ws4.sinaimg.cn/large/006tNbRwly1fys6njp4y6j31400u01ky.jpg)

<p id = "build"></p>
---

## 正文

接下来说说搭建这个博客的技术细节。  

正好之前就有关注过 [GitHub Pages](https://pages.github.com/) + [Jekyll](http://jekyllrb.com/) 快速 Building Blog 的技术方案，非常轻松时尚。

其优点非常明显：

* **Markdown** 带来的优雅写作体验
* 非常熟悉的 Git workflow ，**Git Commit 即 Blog Post**
* 利用 GitHub Pages 的域名和免费无限空间，不用自己折腾主机
* 如果需要自定义域名，也只需要简单改改 DNS 加个 CNAME 就好了 
* Jekyll 的自定制非常容易，基本就是个模版引擎



---


博客主题我是Fork的[BY的博客主题](https://github.com/qiubaiying/qiubaiying.github.io) 的进行修改，遇到了些小问题，不过都解决了，后面又加上了Gitalk的评论插件。

本地调试环境需要 `gem install jekyll`，结果 rubygem 的源居然被墙了，~~后来手动改成了我大淘宝的镜像源才成功~~，淘宝的源已经[停止维护](https://gems.ruby-china.org/)，换成了OSChina的源 `https://gems.ruby-china.org/`。


## 后记

最后，感谢 Hux 提供的的 [Blog 主题](https://github.com/Huxpro/huxpro.github.io)

如果你恰好逛到了这里，希望你也能喜欢这个博客主题，感兴趣的话可以自己动手搭建一个。

—— RH 后记于 2018.12