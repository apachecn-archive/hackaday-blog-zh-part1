# 使用 ZigBee 进行无线 Arduino 编程

> 原文：<https://hackaday.com/2008/11/02/wireless-arduino-programming-with-zigbee/>

![](img/6fd1c78370e75445b34254797ea39421.png "xbee")
[ZigBee](http://en.wikipedia.org/wiki/ZigBee "ZigBee - Wikipedia, the free encyclopedia") 是一种使用数字无线电的低功耗通信系统。它的设计意图是比[蓝牙](http://www.mahalo.com/Bluetooth "Bluetooth - Mahalo")更容易使用。Adafruit 最近为 Digi 的 XBee 产品线添加了一个适配器板，并提供了一个很好的方法来展示这些设备的潜力。使用两个 XBee 无线电和适配器，你可以对 Arduino 板进行无线编程。如果你的 Arduino 安装在一个难以接近的地方，或者可能离你工作的地方超过 100 英尺，那就太好了。无线电可以很好地进行串行通信。操作方法包括让复位线工作，这样 Arduino 可以在你编程后自动重启。一旦无线电对被正确配置，它将把 RTS 线路状态直接从一个设备传递到另一个设备。