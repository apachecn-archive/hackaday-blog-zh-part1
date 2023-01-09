# 努米隆管教程

> 原文：<https://hackaday.com/2011/12/21/numitron-tube-tutorial/>

Nixies 和 VFD 是很好的显示器，但是当使用它们时，你必须处理一些相当高的电压，至少对于我们在 Hack a Day 上看到的微型项目来说是这样。幸运的是，有另一种古老的技术可以用微小的电压驱动。[Kenneth]贴了一个很棒的关于[Numitron tubes](http://kennethfinnegan.blogspot.com/2011/12/numitron-display-tube-tutorial.html)的教程，向互联网展示如何让这些人工作。

Numitron 电子管就像 Nixies，但不是每个谢妮中的十个数字形状的灯丝，而是老式的七段显示器。[Kenneth]在 ebay 上买了一些，卖家很友好地附上了一份俄罗斯数据表。他的 IV-9 numitron 中的每根灯丝都需要大约 20mA 来点亮，非常适合恒流 LED 驱动器[Kenneth]使用

测试电路由 ATtiny2313 和 A6278 LED 驱动器组成。ATtiny 上的代码循环显示数字 0 到 9。这是通过 LED 驱动器发出的，点亮了灯管内的微小灯丝。休息之后，请观看视频，了解 Numitron 的运行情况

[https://www.youtube.com/embed/fcs1IpGQDKs?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/fcs1IpGQDKs?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)