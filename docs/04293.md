# 通过串口进行精神控制

> 原文：<https://hackaday.com/2009/10/21/mind-control-via-serial-port/>

![brain-control-via-serial-port](img/334c583dffc8a83451e166c7de7d6d1a.png "brain-control-via-serial-port")

【Zibri】通过 DB9 串口找到了一个非常简单的[使用脑电波作为控制器的方法。他正在使用米尔顿叔叔的力量训练器，我们昨天在](http://www.zibri.org/2009/09/success.html)[大脑控制的 Arduino](http://hackaday.com/2009/10/20/brain-control-for-the-arduino/) 中看到的。在该项目中，Arduino 接入 led，并通过 USB 将这些信号与计算机连接。这一次，连接是使用 RS-232 收发器通过串行端口将数据从玩具基本单元内部的编程头传递到计算机。接入编程头具有更大的潜力，应该比从 LED 连接中嗅探逻辑更加可靠。[Zibri]已经编写了一个应用程序来显示接收到的数据，但看起来他没有提供可供下载的代码。

显然，他在大约一周前向我们通风报信。我们记得看到这个提交，但你可以告诉它的细节有点轻。所以如果你想让你的建议排在最前面，确保你[尽你所能告诉我们你项目的所有细节。应我们的要求，[Zibri]提供了一张来自原力训练器基本单元的 PCB 图片。休息后再看。 ![force-trainer-base-unit-pcb](img/143d21c2bb16de451b1198f677309354.png "force-trainer-base-unit-pcb")](http://hackaday.com/2009/09/19/how-to-make-your-project-an-internet-sensation/)