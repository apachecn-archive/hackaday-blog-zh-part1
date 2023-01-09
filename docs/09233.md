# 以 Android 和 SPOT 为例对蓝牙进行逆向工程

> 原文：<https://hackaday.com/2011/12/05/reverse-engineering-bluetooth-using-android-and-spot-as-an-example/>

![](img/291d5e0a3dd23c729e0addd7925797f0.png "spot-bluetooth")

[Travis Goodspeed]来信告诉我们他的工作[对 SPOT 模块](http://travisgoodspeed.blogspot.com/2011/12/introduction-to-bluetooth-rfcomm.html)上的蓝牙通信进行逆向工程。他将这篇文章定位为嗅探蓝牙传输的一般指南，但在看到[另一个 SPOT hack](http://hackaday.com/2011/10/01/hacking-spot-personal-satellite-tracker-to-pass-more-information/) 后，他受到启发，以 SPOT 为例。我们知道他是[的粉丝，用他的诺基亚 N900](http://hackaday.com/2011/10/08/rf-sniffing-on-the-go/) 让事情运转起来，这正是他最终完成这个项目的地方。

这个模块被制造成由 Android 手机控制。但没有适用于诺基亚手机的控制应用。由于 Android 将开源的 Bluez 包用于蓝牙协议，所以实际上很容易就能得到这些包。在获取了一些测试集后，他展示了他是如何破译这些数据包的，然后编写了一个快速的 Python 脚本来测试他的发现。在研究了各种可用的命令(获取 SPOT 序列号，从中获取位置数据等)之后，[Travis]在 QT mobility 中编写了一个前端，供 N900 使用。