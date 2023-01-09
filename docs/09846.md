# 逆向工程诺基亚液晶显示器

> 原文：<https://hackaday.com/2012/03/08/reverse-engineering-a-nokia-lcd/>

![](img/13dfa67d19ec508615cdc8abd234cea9.png "display")

多年来，从旧诺基亚手机上取下的 LCD 显示屏一直是硬件制造商的主要产品，所以我们很高兴看到[Andy] [对全彩色 QVGA 显示屏进行逆向工程](http://andybrown.me.uk/ws/2012/03/06/reverse-engineering-the-nokia-2730-qvga-lcd/)，这样我们就可以将我们的灰度项目转移到全彩色显示屏上。

诺基亚 2730、5000 和 7100 手机的屏幕是一个技术奇迹——它的 18 位彩色和非常高的分辨率激起了[安迪]的兴趣。他从易贝买了一辆二手诺基亚 2730，并开始把它拆开。检查完手机的原理图后，[安迪]做了一些分线板；特别有用，因为他还发现了一些连接器。

通过大量的谷歌搜索，[Andy]找到了另一个迷失的灵魂，他成功地闯入了一个类似的 LCD 显示器，并发现它与 Magnachip LCD 控制器兼容。唯一的方法是发送一些命令到显示器上，然后观察会发生什么。

[Andy]设法在屏幕上绘制像素，并发现了一些有趣的功能:支持硬件滚动，可以在纵向或横向之间切换。从易贝的二手手机上，[安迪]现在有了一个非常好的 QVGA 显示屏。我们称之为胜利，但你可以在休息后自己判断视频。

[https://www.youtube.com/embed/493r8jG8A4E?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/493r8jG8A4E?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)