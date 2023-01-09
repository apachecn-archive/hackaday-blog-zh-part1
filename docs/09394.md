# WPA/WPA2 无线网络安全的一个漏洞

> 原文：<https://hackaday.com/2011/12/29/a-chink-in-the-armor-of-wpawpa2-wifi-security/>

![](img/aaf4b0b997dc33a1de586fe4c50ebdb0.png "wi-fi-protected-setup")

看起来你的无线网络可能没有你想象的那么安全。[Stefan viehbck]最近发表的一篇论文详细描述了本应强大的 WPA/WPA2 WiFi 安全协议中的一个安全缺陷。实际上，并不是这个协议是罪魁祸首，而是一个名为 [Wi-Fi 保护设置](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup)的内置功能。这是一个附加的安全协议，允许您轻松设置网络设备，如打印机，而不需要给他们 WPA 密码。[Stephan 的]概念验证允许他使用蛮力在 4-10 小时内获得 WPS pin。一旦攻击者获得了该 pin，他们就可以立即获得 WPA 密码。即使密码频繁更改，这种方法仍然有效。

显然，大多数 WiFi 接入点不仅提供 WPS，而且默认启用。更糟糕的是，一些硬件设置面板提供了一个实际上什么也不做的禁用开关！

看起来[Stephan]并不是唯一一个致力于此漏洞的人。[克雷格]写信告诉我们他已经发布了利用漏洞的软件。