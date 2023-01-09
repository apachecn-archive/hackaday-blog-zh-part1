# 黑掉一个 IButton

> 原文：<https://hackaday.com/2009/07/09/hacking-an-ibutton/>

![breadboard1](img/c9aa2a6ac52c5042f98e097cca12511a.png "breadboard1")

Maxim 的 iButtons 是纽扣大小的小集成电路，开始在越来越多的地方出现。它们有广泛的用途，从温度记录器到身份识别，都使用 1 线协议进行通信。在一辆[furtek](http://furrtek.free.fr/index.php?p=crea&a=ibutton&i=2)上，他们黑了一个用于从自动售货机买东西的 iButton，创造了一个无限的金钱骗局。他们在 ATmega8 的基础上建造了一个小型平台来读写芯片上的数据。数据是加密的，所以在卡上随意放多少钱是不可行的。取而代之的是，他们使用了与[波士顿地铁黑客](http://hackaday.com/2008/08/09/defcon-16-mit-boston-transit-presentation-gagged/)相似的技术，在购买了某样东西后，恢复了 iButton 的先前状态。他们还创造了一种手持设备来备份和恢复便携式黑客的按钮内容。

[谢谢 furtek]