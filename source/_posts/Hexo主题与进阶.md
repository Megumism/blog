---
title: Hexo主题与进阶
date: 2020-02-22 13:21:51
index_img: /img/covers/HexoPage.png
categories: 配置
tags:
  - Hexo
---

关于配置、改进、创造 Hexo 主题的笔记。

> 当你看到你用的主题出现在两个以上的博客的时候，那你就要考虑自己写一个了。

操蛋的是，我的前端水平还不够。

<!--more-->

## Hexo 主题的优化配置

### 主题平滑升级

虽然 stun 主题崩掉了，但是我意外地发现这个文档写的非常的细致！在[新手进阶](https://liuyib.github.io/hexo-theme-stun/zh-CN/advanced/advanced-setting.html#%E5%B9%B3%E6%BB%91%E5%8D%87%E7%BA%A7)中作者给出了以下的方案：

> 更新 Hexo 主题时，一般都会有这样的经历：先将主题目录下的 `_config.yml` 文件备份，更新完主题后，再将备份的数据复制粘贴还原回去。
>
> 这个过程繁琐又浪费时间，因此我们需要一种友好的更新方式。如果你也经历着这样的痛苦，那么不妨尝试 Hexo 3.0 新增的功能 -- **数据文件**。
>
> Stun 主题利用该功能实现了平滑升级的特性，使用步骤如下：将主题目录下的 `_config.yml` 文件复制到博客根目录下的 `/source/_data/` 中，并重命名为主题名称。例如使用 stun 主题，那么就叫做 `stun.yml` 。如果 `source` 目录下没有 `_data` 文件夹请自行创建。
>
> 这两个文件的关系为 `stun.yml` 覆盖 `_config.yml`，也就是说，想要修改配置时，只需要修改 `stun.yml` 里的即可（修改 `_config.yml` 里的不会生效）。这样就实现了平滑升级，更新时 `_config.yml` （可能）会更新，而你的配置数据保留在 `stun.yml` 中。
>
> > 注意 ！！！
> >
> > 主题更新后，如果主题目录下的 `_config.yml` 文件里出现了新的选项，那么你必须从该文件中将它们复制到 `/source/_data/stun.yml` 中，并设置它们的值为你想要的选项。
> >
> > 如果你使用了平滑升级这一特性，那么 `/themes/stun/_config.yml` 和 `/source/_data/stun.yml` 这两个文件里的选项没有同步，是更新主题后，启动报错的最主要的原因！

另外，对于特定的主题请看对应的文档！对于 fluid 主题，他的命名是`fluid_config.yml`。

## Hexo-theme-next 的下载与改进

这些文章暂且马克在这里，其实我对 next 还是有点抵触的，但无奈于它迭代比较多也比较稳定，所以先用着吧。

- [简书-Hexo-NexT 配置超炫网页效果](https://www.jianshu.com/p/9f0e90cc32c2)
- [CSDN-Hexo 的 Next 主题详细配置](https://blog.csdn.net/qq_33840251/article/details/90712422)
- [iissnan 大佬写的中文老版本文档](http://theme-next.iissnan.com/getting-started.html#theme-settings)
- [Next 官方相当于什么都没说的破烂文档](https://theme-next.org/)

## Hexo-theme 的编写

希望有一天，我可以做出 Hexo 的主题叭……

- [简书-搭建Hexo博客进阶篇---主题自定义（三）](https://www.jianshu.com/p/4b9ee8fec3a3)
- [Melody 开发者写的 Hexo 主题开发经验杂谈](https://molunerfinn.com/make-a-hexo-theme/#%E5%89%8D%E8%A8%80)
- [Hexo 主题开发](https://www.cnblogs.com/yyhh/p/11058985.html)
  上面的文档写的很详细，不过按他的步骤已经行不通了，还是要先用一个生成主题目录结构的脚手架工具`yeoman`：
- [前端之路多坎坷 - hexo 主题开发历程](https://www.m-finder.com/2018/08/30/about-web-view/)
- [从零开始制作 Hexo 主题](https://www.ahonn.me/blog/create-a-hexo-theme-from-scratch)
