# 利用 LED 进行低成本检测和通信

> 原文：<https://hackaday.com/2006/02/21/low-cost-sensing-and-communication-with-an-led/>

![ledtouch_photo](img/e9ea3488816913d6c8d943c380c51f91.png "ledtouch_photo")

led 在电子设备中极为常见。它们被用作光发射器，但也可以用作光探测器，因为它们是光电二极管。通过在发光和检测之间快速切换，您可以使用 led 来确定环境照明，甚至进行双向通信。MERL 有一篇很好的论文，涵盖了这个系统如何工作以及他们如何将它用作“最后一厘米”通信设备的基础知识。该系统可以使用一个 LED、一个电阻和两个 I/O 引脚来实现。因此，它几乎可以便宜地用在任何设备上。微处理器在发光、检测光(LED 充当充电电容器)和测量 LED 的放电率之间快速切换 LED 以确定光水平。Jeff Han 有一个简洁的[视频演示](http://mrl.nyu.edu/%7Ejhan/ledtouch/index.html)如何将该系统用作接近传感器。

**更新:**[hawkeyaz 1]指着一篇报道[一个人对 LED 传感器的调查](http://projects.dimension-x.net/technology-and-projects/ledsensors/)的博客。

[谢谢 branen]

*   [永久链接](http://www.merl.com/publications/TR2003-035/)