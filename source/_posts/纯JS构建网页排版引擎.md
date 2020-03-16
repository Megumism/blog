---
title: TPA 和排版引擎
date: 2020-02-21 21:38:53
index_img: /img/covers/TPAPage.png
categories: 技术文档
tags:
  - Javascript
---

关于我的第一个前端 TPA 项目的介绍，可以访问 GitHub repo 查看源代码。

<!--more-->

SPA 是（single page web application，单页面富应用程序）的缩写，而[我的前作](www.megumism.com)实际建立了三个页面：首页，目录页和文章页，所以姑且把我网站的结构称作 TPA 吧。

形象地解释一下，对于一般的博客，博文作者写的是手稿，这份手稿读者是都不懂的，所以博文作者要把它交给一个编辑，这个编辑把它电子排版变成一本现成的书，放到书架上，要看书的读者直接去书架上取；但是我偏偏是个神棍（大雾），我请不起正经编辑，所以我把我的神秘手稿写完就堆在了书架上，并且安排了一位吉普赛占卜女郎站在那，你得现场告诉她想听什么，然后她取下对应的手稿口译给你听……

咳咳，说回正题那么为什么要写成 TPA 呢？对于工科学科来说，最好的学习方法就是**做项目**，所以就有了写一个博客来练习自己学的 HTML、CSS 的想法。于是用了几天实践，一个静态主页就写好并且挂在新买的域名上。但是在进一步写其他页面的时候，我感受到了一阵头痛——因为这个博客不基于 Hexo，Wordpress 这一类博客平台，那么如果采用纯手写的方式，那么我每更新一篇博文，就要写一个 HTML 文件，这简直是杀人！就是因为 HTML 写死人所以 John Gruber 才搞了个[markdown](https://en.wikipedia.org/wiki/Markdown)方便广大开发者……等等！

所以就有了第一个想法：我要想办法把我写的 md 弄到我的网页上动态显示。

## 第一步 让文章页加载并解析 MD——让吉普赛人学会读我的手稿

而我的技术又不足以写出一个高效有序的解析程序，那么我通过[用 showdown 给 HTML 网页插入 markdown 笔记](https://blog.csdn.net/mildddd/article/details/79704810)一文，找到了以下现成的 markdown 转 HTML 的 js 包：

- [github 上的 showdown.js](https://github.com/showdownjs/showdown)

下面是为了实现用到的技术贴子：

- [动态加载 js 文件，并在加载成功后执行回调函数](https://blog.csdn.net/weixin_30456039/article/details/95240184)：从而在网页段加载该外部的 js 包。
- [基于 jq 和纯 js 的 读取本地.txt 文件的方法](https://blog.csdn.net/u013970232/article/details/89146426)：稍作一点改动就可以实现读取 markdown，毕竟都是文本文件嘛。
- [动态加载js文件的正确姿势](https://blog.csdn.net/weixin_34387468/article/details/92473457?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task)这是一篇很完善的技术文档。
- [如何在js文件中动态加载另一个js文件？](https://blog.csdn.net/a3025056/article/details/73614554)

接下来我们用一点魔法……啊不，是写一点 js 对 markdown 做一些预处理（比如将 h1 和正文分离，移除 TOC），之后再交给 showdown 解析。那么做到这里，我的文章页（也就是你现在正在读的这一页）已经实现了动态显示。

## 第二步 实现文章的自动加载——让吉普赛人自己学会找手稿

但是我仍然面临一个问题，就是文章页具有了读取 md 的能力，但它不知道读什么，这就需要目录页把要读的文件名称传给它，下面是为了实现这一点所用到的技术贴：

- [html 页面跳转传递参数](https://blog.csdn.net/gnail_oug/article/details/53286694)：而我的网页需要知道访客是从哪里跳过来的，想看什么文章，所以我需要传出一个参数。
- [js 中 window.location.search 的用法和作用](https://blog.csdn.net/qq_27093465/article/details/50731087)：文章页面接住这个参数。

做完之后我又陷入了对人生和社会的大思考：难道我每加一篇文章，我都要写一次目录页的 html？我不，我还是只想写 md，所以我继续写了一个 JavaScript，让它读取一个记录了文章目录的 md 文件，并将它解析为 html 目录。有了第一步的技术和代码铺垫，这一步并不难写。

那么现在享受自己搭建的 Blog 吧！乌拉！

## 后记——我其实不想要吉普赛人

可能有人会问为什么目录用 md 不用 json 啊……其实问题主要在于这是一个纯前端博客，所以并没有一个程序在后端帮我整理、生成一个目录文件，那么 md 实际上要我自己写，显然对于人而言，md 的可写性比 json 高很多……如果你愿意帮我写一个整理并生成目录的程序，欢迎你联系我，比如[给这个 Blog 提 issue](https://github.com/Megumism/SingleBlog/issues)，我永远准备好膝盖。
