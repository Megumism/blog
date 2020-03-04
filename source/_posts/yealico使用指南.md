---
title: yealico使用指南
index_img: /img/covers/
categories: 配置
date: 2020-03-04 20:19:24
tags:
- yealico
---

[Yealico](https://apps.apple.com/cn/app/yealico/id1359000639)是一个个性化定制的阅读平台。它可以将资讯、报纸、杂志、图片等众多网页内容，按照用户意愿聚合到一起，再通过简洁精美的排版风格，让用户享受极致的阅读体验。

下面的教程精简自[Yealico小小站](https://yealicositemarket.home.blog/)，感谢一切为互联网变得更好而努力的人们。

<!--more-->

## 导入站点规则

iOS用户可以从App Store获取[Yealico](https://apps.apple.com/cn/app/yealico/id1359000639)，然后打开Yealico并扫描下方二维码导入站点规则，即可把网站的内容搬到iOS设备上直接浏览，还可以收藏或下载自己喜欢的内容，方便快捷。

例如：
> E-hentai二维码：
> ![E-hentai](https://yealicositemarkethome.files.wordpress.com/2019/12/img_4016.jpg?w=400)

## 编辑cookies

Yealico最近更新的两个版本，添加了蛮多使用功能的，其中一个就是自定义Cookie。

有些网友可能不太明白Cookie的用处。简单点说就是账号登录后，一般都会保留登录信息到这个Cookie中，以便网站验证你的身份。因此，这个功能对于需要登录的网站来说还是特别有用的。

下面以exhentai为例介绍这一过程。

![exhentai](https://yealicositemarkethome.files.wordpress.com/2019/12/img_4015.jpg?w=400)

### 获得cookies

e站的cookies格式：

> igneous=015e91709; ipb_member_id=账号ID; ipb_pass_hash=870ffccbf3256454fca21824a98de22a; yay=louder

其中包含了四个参数，分别是：igneous、ipb_member_id、ipb_pass_hash和yay。

下面以PC版的Chrome说明一下，如何找打Cookie。

1. 正常登录exhentai网站首页后，右击网页选择“检查”（F12/Ctrl+Shift+I)打开控制台窗口；
2. 点击上面的Network按钮，然后刷新网页，我们会在检查窗口的左边栏看到一些文件名，继续点击选择exhentai.org（可能需要Ctrl+R刷新一次）；
3. 此时右边栏会显示exhentai.org的一些相关信息，我们需要的Cookie在header这一栏；

唯一不同的是，Yealico第四个参数是yay，而桌面Chrome的是sk。直接把桌面Chrome的Cookie复制到规则中的自定义Cookie一栏也是可以正常浏览的。当然也可以只复制igneous、ipb_member_id、ipb_pass_hash三个参数，然后自己加上yay=louder。

### 写入cookies

将上面的cookie复制到下面的位置，刷新，即可使用。
![step](/img/yealico/step1.jpg)
![step](/img/yealico/step2.jpg)

### 关于更多

更多的站点规则列表可以参见[Yealico小小站的这篇文章](https://yealicositemarket.home.blog/%E7%AB%99%E7%82%B9%E8%A7%84%E5%88%99%E5%88%97%E8%A1%A8/)
