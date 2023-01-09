# 温度感应杯意味着再也不会烫到你的嘴

> 原文：<https://hackaday.com/2011/04/12/temperature-sensing-mug-means-never-burning-your-mouth-again/>

![temp_sensing_mug](img/6dba34c86b097e157fd7647b25063b06.png "temp_sensing_mug")

有些人会非常依恋他们最喜欢的杯子。就像一个老朋友一样，这个杯子在他们心中占据着特殊的位置，当它最终死去时，会有一种奇怪的悲伤。在冬天的几个月里，[本的]女朋友从来没有离开过她，当它坏了，他决定给她一个新的有一些附加功能的。

他给她做了一个温度感应杯，用一种相当新颖的方法来确定里面的东西有多冷或多热。他没有使用热敏电阻来确定饮料的温度，而是选择使用一个简单的二极管，因为众所周知，二极管的正向电压随温度而变化。在使用冷热饮料确定二极管的电压范围后，他将它连接到 PIC12F615 微控制器的 ADC。温度通过 10 个 led 显示，这些 led 通过一对 8 位移位寄存器和缓冲器驱动，因为他的 PIC 没有足够的引脚来单独控制它们。

他做了一些印刷电路板，几经周折后，终于把所有东西都组装好了。他说这个杯子工作得很好，尽管显示屏的变化比他希望的要慢一些。他还提到，如果他构建第二个版本，他一定会选择一个不同的 PIC，它有足够的 I/O 引脚来完成这项工作，并使用热敏电阻而不是简单的二极管来检测温度。

继续阅读，查看[Ben]整理的简短演示视频。

[https://www.youtube.com/embed/a3rdqrNcfKg?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/a3rdqrNcfKg?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)