# 大修 LED 跑马灯

> 原文：<https://hackaday.com/2008/11/14/overhauling-led-marquees/>

![led-sign](img/f6214281968f0e5d9709635501aea448.png "led-sign")

在之前的工作中，[sprite_tm]负责处理许多不同的 LED 文字广告。硬件相当简单，他总是认为只要稍加努力就可以把它们推得更远。他最近购买了 10 个 32×16 的 LED 显示屏，决定用它们做些什么。项目结束时，他在显示器上播放了全动态视频。如果你想了解 LED 矩阵显示器，这是一个很好的项目。他从逆向工程电路板上的电子元件开始。然后他安装了一个 ATmega88 来驱动显示模块。多个显示模块通过串行菊花链连接在一起。本文还介绍了 PWM 控制和刷新时序。查看下面几个演示视频之一。

[https://www.youtube.com/embed/b9KougCn3mk?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/b9KougCn3mk?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)