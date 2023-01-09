# Chumby 控制的机械轮式机器人

> 原文：<https://hackaday.com/2011/08/29/chumby-controlled-mechanum-wheel-robot/>

[马多克斯]挖出了一个 [Insignia Infocast 来和这个机器人](http://www.madox.net/blog/2011/01/24/mecanum-wheel-rover-2/)一起使用。Insignia 是百思买的自有品牌，他们与 Chumby 合作制作他们的 Infocast 系列。如果你能找到一个二手的或清仓的模型，这是一个很好的方式让你自己和嵌入式 Linux 板这样的一个项目。

车身和车轮是 3D 打印的，设计文件可在[Madox ' s][Thingiverse page](http://www.thingiverse.com/thing:5681)获得。mechanum 车轮工作得非常好，使用七个轴承平稳运行。机身本身包括两组电池的支架。其中一个电池组为 Chumby board 供电，而另一个用于为负责移动的四个伺服电机供电。为了简化电子设备,[Madox]选择使用 USB 伺服驱动器，这只花了他大约 20 美元。

我们不确定机器人顶部的 USB 加密狗是做什么用的。我们猜测这是一个 WiFi 适配器，因为机器设置了自己的接入点作为控制器。但我们以为 Chumby boards 内置了 WiFi。无论如何，休息之后看看视频，你可以看到一部安卓手机在驾驶这个小家伙。代码中有一个阻止左右移动的缺陷，在大约 2:15 的视频中断后得到修复，之后一切正常。

[https://www.youtube.com/embed/iSnTZzrXocM?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/iSnTZzrXocM?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)