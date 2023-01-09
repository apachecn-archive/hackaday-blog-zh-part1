# 所有复古系统的无线控制器

> 原文：<https://hackaday.com/2012/02/13/wireless-controllers-for-all-your-retro-systems/>

还记得那些为我们年轻一代的游戏机制造的老式无线控制器吗，比如 NES 和超级任天堂？它们工作不太好，主要是因为它们是用遥控器中发现的同样的红外技术制造的。现在所有的现代游戏机都是无线的，nftgames 论坛的[micro]决定[更新他的经典系统](http://nfggames.com/forum2/index.php?topic=4393.0)用于无线控制。

发射器和接收器围绕一个工作在 2.4 GHz 频段的 [nRF24L01+](http://www.sparkfun.com/products/691) 无线电模块构建。[微]有将他的控制器转化为科学的过程。他剪断电线，将控制器连接到 16 MHz 的 AVR 上。AVR 将此发送到接收器，在接收器中，按钮按压通过原始控制器端口发送。基本上，[微]为他的 NES、s NES、土星和 N64 重新创造了一个 [WaveBird](http://en.wikipedia.org/wiki/WaveBird_Wireless_Controller) 控制器。

控制器由内部锂电池供电，但充电 IC 太贵，无法放在每个控制器中。为了解决这个问题，[micro]制作了一个小型的[外部充电电路](http://i.imgur.com/OKtHM.jpg)，可以插入每个控制器上的 3.5 毫米插孔。休息之后，请查看[micro]的控制器演示。

[https://www.youtube.com/embed/LlnmfaILCHw?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/LlnmfaILCHw?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)