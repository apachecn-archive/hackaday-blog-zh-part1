# 非触摸 Kindle 4 上的自定义屏幕保护程序

> 原文：<https://hackaday.com/2012/01/05/custom-screensaver-on-the-non-touch-kindle-4/>

[Kubbur87]整理出一个指南，用你自己的图片替换非触摸 Kindle 4 屏保。我们已经看到了一种方法[从最新版本的 Kindle 硬件上移除特价横幅](http://hackaday.com/2011/12/20/hack-removes-ads-from-kindle-special-offers-hardware/)，这种黑客可以让你使用自己的 600×800 便携式网络图形(。png)文件，而不是亚马逊推送到设备上的图片。

坦率地说，我们对这种攻击如此简单感到震惊。[Kubbur87]将设备置于开发人员模式，启用 SSH，然后在中运行 Linux shell。似乎唯一的保护线是他不知何故获得的根密码。

休息后，你会发现他的视频显示如何启用开发模式，以及如何执行这一黑客。当设备被识别为 USB 存储设备时，通过在设备上放置一个名为“ENABLE_DIAGS”的无扩展名文件，您可以访问诊断菜单系统。从那里开始，只需浏览菜单就可以获得 SSH 访问。就像我们说的，你需要根密码，这就像给你最喜欢的 1980 年代的电子游戏角色命名一样简单。

进入开发人员模式:

[https://www.youtube.com/embed/XZEhsCKgMHw?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/XZEhsCKgMHw?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

更换屏幕保护程序:

[https://www.youtube.com/embed/fG_pGDMsAYo?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/fG_pGDMsAYo?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)