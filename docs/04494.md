# IPv6 到单线协议转换器

> 原文：<https://hackaday.com/2009/12/02/ipv6-to-1-wire-protocol-translator/>

![](img/d9b58c26cee1b376c3fd90b3af400c05.png "ipv6-1wire")

[Fli]组装了一个基于 AVR 的系统，该系统可以[将 IPv6 地址分配给单总线组件](http://www.shapeshifter.se/2009/07/10/1-wire-meets-ipv6/)。AVR ATmega644 微控制器与 ENC28J60 以太网控制器芯片结合使用。为了在这个温顺的硬件[Fli] [上运行 IPv6，将 uIPv6 栈](http://www.shapeshifter.se/code/uipv6/)从 [contiki 项目](http://www.sics.se/contiki/)移植到 AVR 框架上。尽管他在这个过程中遇到了一些硬件故障，但最终他成功地将五个传感器连接到设备上，每个传感器都使用堆栈的别名功能分配了自己的 IP 地址。

如果您正在寻找一个低成本的 IPv6 解决方案，这是非常好的。我们不确定对它的需求是否很大，但它对你正在考虑的 [1 线家庭自动化](http://hackaday.com/2009/07/29/1-wire-hvac-monitoring-system/)设置很有用。