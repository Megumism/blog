---
title: Hexo 前期安装和配置
date: 2020-02-21 22:08:30
index_img: /img/covers/HexoPage.png
categories: 配置
tags:
  - Hexo
---

在这里非常感谢@Sufe.曲水的大力协助，新手建站可以直接阅读他的[从零开始用 Hexo 搭建一个博客](https://jordan-li.github.io/hexo-new/)，当然可能需要你了解一些 git 的基本操作才能实现*将 Hexo 上的博文推到远端*的操作。

但是总的来说，这是一篇非常好的入门教程。

<!--more-->

## hexo-server

嫌弃`hexo s`还要关？嫌弃`hexo d`上传慢？利用 hexo-server 就可以持续进行调试了！

以下内容基于[官方文档-服务器](https://hexo.io/zh-cn/docs/server)，更详细的内容当然需要你去官方文档探索。

> ```shell
> $ npm install hexo-server --save
> + hexo-server@1.0.0
> ```
>
> 安装完成后，输入以下命令以启动服务器，您的网站会在 <http://localhost:4000> 下启动。在服务器启动期间，Hexo 会监视文件变动并自动更新，您无须重启服务器。
>
> ```shell
> hexo server
> ```
>
> ### 更改端口
>
> 如果您想要更改端口，或是在执行时遇到了 EADDRINUSE 错误，可以在执行时使用 -p 选项指定其他端口，如下：
>
> ```shell
> hexo server -p 5000
> ```
>
> ### 静态模式
>
> 在静态模式下，服务器只处理 public 文件夹内的文件，而不会处理文件变动，在执行时，您应该先自行执行 hexo generate，此模式通常用于生产环境（production mode）下。
>
> ```shell
> hexo server -s
> ```

## hexo-deployer-git 自动爆炸

除了重装之外没有找到好办法。

```shell
$ cnpm install --save hexo-deployer-git
√ All packages installed
```

## 一个顺带的 git 收获

对于 git 在 clone 时出现的错误`error: RPC failed; curl transfer closed with outstanding read data remaining`，StackOverflow 上有一位老哥给出了很好的解决方案：

> When I tried cloning from the remote, got the same issue repeatedly:
>
> ```text
> remote: Counting objects: 182, done.
> remote: Compressing objects: 100% (149/149), done.
> error: RPC failed; curl 18 transfer closed with outstanding read data remaining
> fatal: The remote end hung up unexpectedly
> fatal: early EOF
> fatal: index-pack failed
> ```
>
> Finally this worked for me:
>
> ```shell
> $ git clone https://username@bitbucket.org/repositoryName.git --depth 1
> ```
