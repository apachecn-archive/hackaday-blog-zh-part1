# 无线黑客空间状态通知器

> 原文：<https://hackaday.com/2011/05/23/wireless-hackerspace-status-notifier/>

![space_probe](img/a9e592373e26de19bb576429e9e17a3d.png "space_probe")

黑客空间总是在寻找新颖的方式让他们的成员知道他们正在营业，这个来自 Make，Hack，Void 的通知者[Angus]最近也不例外。

有一天在翻垃圾箱时，他发现了一个 70 年代的看起来很棒的实验室电源。他取出了它的内部，为将来的项目保存了变量 transformer，并开始构建他的通知器。当有人进入黑客空间时，他们只需将“太空探测器”上的刻度盘设置为他们预计在那里停留的时间。内置的 Seeduino 通过蓝牙将数据发送到支持 OpenWRT 的路由器，该路由器使用几个 Lua 脚本通过电子邮件和 Twitter 通知成员。

由于几乎所有的处理都是在路由器端完成的，所以它只需让探头中的 Arduino 在任何时候转动旋钮时闪烁 LED 并发送 ASCII 状态消息。[Angus]很清楚这可能会让大多数人晕头转向，但他希望其他黑客空间成员利用这一未开发的潜力来进一步增强通知程序。

留下来看看太空探测器的运行，如果你有兴趣看看其他黑客空间用什么来让他们的成员了解情况，请查看来自 Hack42 的这个状态开关。

[https://www.youtube.com/embed/7_1P8PqnoWg?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/7_1P8PqnoWg?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)