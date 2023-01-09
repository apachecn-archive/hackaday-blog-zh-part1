# 向冰管钟学习

> 原文：<https://hackaday.com/2009/08/25/learn-from-the-ice-tube-clock/>

![icetube](img/4fbf7d6321548534914341312748f8a2.png "icetube")

看起来他们又在阿达果餐厅吵架了。这一次他们[生产了一种时钟](http://www.ladyada.net/make/icetube/index.html)，看起来更像是应该挂在弹药上，而不是放在床头。但是，撇开极客信誉不谈，从他们的设计中可以学到很多东西。正如我们所期望的那样，他们已经收集了一些关于组件选择的很好的文档。

从[看一眼](http://www.ladyada.net/make/icetube/design.html)他们的 5v 电源调节器开始。输出端有一个额外的二极管，防止来自 3v 备用电池的反向电流。控制时钟的 AVR ATmega168 用于检测断电并快速切换到备用电池。他们还使用微控制器作为高压 VFD 的升压转换器，这是一个很好的技巧[，我们在](http://hackaday.com/2009/07/07/avr-boost-converter/)之前已经见过。

[感谢 pt]