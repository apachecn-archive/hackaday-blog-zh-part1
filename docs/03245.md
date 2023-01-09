# Android 上的 X11

> 原文：<https://hackaday.com/2009/02/22/x11-on-android/>

![x11](img/f5dc7f1c245bb3837dd649d0da9dbd30.png "x11")

[ghostwalker]整理了在你的 Android 设备上运行 X11 的[指令。这意味着你可以在手机上运行一个成熟的 Linux 桌面环境。它要求你在手机上已经有一个 Debian shell，](http://www.androidfanatic.com/cms/community-forums.html?%20func=view&catid=9&id=1615 "Gnome, KDE, IceWM or LXDE Desktop on your Android! - AndroidFanatic Community Forums")[，我们之前已经讨论过了](http://hackaday.com/2009/01/15/debian-on-the-g1-once-again/ "Debian on the G1 once again  - Hack a Day")。它与一个 [VNC](http://en.wikipedia.org/wiki/Vnc "Virtual Network Computing - Wikipedia, the free encyclopedia") 服务器相连，而不是必须拿出一个定制的显示驱动程序。你可以通过手机上的安卓 VNC 浏览器或任何其他 VNC 客户端连接到它。该指南建议窗口经理要么选择 IceWM，要么选择更轻量级的 LXDE。你可以安装 Gnome 或 KDE，但是如果它比狗慢的话，我们会很惊讶。让我们知道，如果你有这方面的成功，你认为最好的用途是什么。