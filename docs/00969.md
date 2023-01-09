# GP2X，内置 USB 主机端口

> 原文：<https://hackaday.com/2006/07/23/gp2x-with-built-in-usb-host-port/>

![gp2x usb host mode](img/d5d2290b9e5c6f4841044082a9578796.png)

黑客[Sprite_tm]是我们的最爱之一。他继续用他的最新技术取悦我们，[给他的 GP2X](http://sprite.student.utwente.nl/%7Ejeroen/projects/gp2x-usb/) 增加了一个 USB 主机端口。GP2X 是一个基于 Linux 的手持游戏系统。它通过外部端口支持 USB 设备。问题是:它不供电，你必须使用加密狗。GP2X 使用 MAX1566 DC-DC 转换器，因此 Sprite_tm 能够从芯片中获得 5V 电压，否则将无法使用。一旦安装到位，他需要做的就是编写一个简单的脚本来安装 USB 设备。芯片应该提供 500 毫安，但不能保证。高牵引可能会锁定 GP2X，因此如果您不确定，仍应使用电动集线器。

*   [永久链接](http://sprite.student.utwente.nl/~jeroen/projects/gp2x-usb/)