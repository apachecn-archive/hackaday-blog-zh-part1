# 使用 AVR 的 USB 和 UDP

> 原文：<https://hackaday.com/2005/10/12/usb-and-udp-using-an-avr/>

![usb ir](img/5ae1c8e05f761807e8f3b1c132f58b87.png)

如果你理解了字母汤的标题，你就有得吃了。Igor Cesko 最初的项目是为他的计算机构建一个红外接口，这样他就可以远程控制它。他为这项任务制作了一个简单的串行加密狗，因为他不想使用微控制器来解码红外信号。USB 正变得比串行接口更加普遍，因此 Igor 决定尝试为 USB 通信编写一个[微控制器](http://www.cesko.host.sk/IgorPlugUSB/IgorPlug-USB%20%28AVR%29_eng.htm)。他的控制器为他的红外项目工作，但它应该很容易用于任何其他项目，你想要一个 USB 接口。他最近的项目是[教一个 AVR 做 UDP](http://www.cesko.host.sk/IgorPlugUDP/IgorPlug-UDP%20%28AVR%29_eng.htm) 。使用他的 IR - > UDP 设备和交叉电缆，他可以把接收器放在离电脑更远的地方。它需要全双工连接，并且已经过直接连接到网卡的测试。不知道它是否能正常连接到路由器上。

[谢谢约翰内斯]

*   [永久链接](http://www.cesko.host.sk/)