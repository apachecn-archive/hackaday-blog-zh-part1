# [邦妮] Mods 查姆比捕捉史诗延时视频

> 原文：<https://hackaday.com/2011/08/21/bunnie-mods-chumby-to-capture-epic-time-lapse-video/>

![](img/9b49d62dc2c2e16cd502b254e463f20b.png "chumby-time-lapse")

当[兔子]搬进他在新加坡的公寓时，他惊讶地发现一个巨大的建筑项目正在街区的另一边开始。作为一个好奇的人，他总是对正在发生的事情感兴趣，但只是偶尔看看这个项目是不够的。取而代之的是，他架起摄像机[拍了一段延时视频](http://www.bunniestudios.com/blog/?p=1790)。

这并不难，[你可以找到](http://hackaday.com/2008/07/09/intervalometers-and-timelapse-photography/)一系列的[采访项目](http://hackaday.com/2011/06/27/tiny-hardware-based-dslr-intervalometer/)，这些年我们已经报道过。但是[Bunnie]是 Chumby One 的设计者之一，经常对硬件进行[攻击，所以他选择在项目中使用该硬件也就不足为奇了。](http://hackaday.com/2010/04/29/chumby-one-becomes-a-3g-router/)

幸运的是，他分享了自己通过抓拍照片结识朋友的步骤。他提到最困难的部分是找到一个兼容的 USB 摄像头。如果你有一个 2008 版的 Linux 内核，你应该没问题。剩下的工作由 shell 脚本完成。当从 cron 作业调用脚本时，Mplayer 会捕获图像。一旦所有的帧都被捕获，他就使用 mencoder 将 JPEGs 图像拼接成电影。休息后看结果。

[https://www.youtube.com/embed/bJFdCW1ftiI?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/bJFdCW1ftiI?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)