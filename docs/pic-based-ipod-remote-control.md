# 基于 PIC 的 IPod 遥控器

> 原文：<https://hackaday.com/2005/11/10/pic-based-ipod-remote-control/>

![ipod remote](img/75c901aee8e1c89a037c60c937044f45.png)

我发现了大量关于 iPod 的 dock 引脚和基于串行的远程接口的文档，但从来没有一个像样的解释如何实际实现它。最后，我找到了藏在 iPod Linux wiki 中的 BigCookie 的 iPod to T &遥控适配器。他制造了控制器来接收来自音频接收器的远程信号，然后转换它们来控制 iPod。他有 a PIC16F628 微控制器的原理图和代码。我猜代码可以被修改以支持 PIC 支持的几乎任何输入法。

*   [永久链接](http://ipodlinux.org/IPod_to_T%26A_remotecontrol_adapter)