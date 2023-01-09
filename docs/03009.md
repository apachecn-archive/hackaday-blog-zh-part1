# RepRap 主板

> 原文：<https://hackaday.com/2008/12/24/reprap-motherboard/>

![reprapmb-1](img/7c920e1ad091dccdceef17ff5aa8f396.png "reprapmb-1")

当 [RepRap](http://hackaday.com/tag/reprap/ "reprap  - Hack a Day") 团队发现自己正在挑战 [Arduino](http://hackaday.com/tag/arduino/ "arduino  - Hack a Day") 的极限时，他们开始寻找替代品。他们在 ATMega644P 里找到的。与标准 Arduino 中使用的 ATMega168 相比，它拥有四倍于 T4 的内存和四倍于 T5 的内存。它还有 32 个 I/O 引脚。他们将 Arduino 软件移植到微控制器上，开始生产 Sanguino 板。既然基础设计已经确定，他们已经开始扩展它以达到他们的特定目的。上图是一个[原型 RepRap 主板](http://blog.reprap.org/2008/12/mother-of-all-boards.html "Mother of all Boards...")。虽然 Sanguino 是准系统，但该电路板上有用于所有 RepRap 电机的板载连接器，因此您可以直接将其插入。它还被设计为支持未来的第 3 代电子产品。大概最有趣的功能就是 SD 卡槽了。我们的目标是最终拥有一个可以在没有主机的情况下运行 RepRap 的主板；它将直接从闪存卡制造设计。