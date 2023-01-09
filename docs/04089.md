# 入侵 USB 串行端口适配器

> 原文：<https://hackaday.com/2009/09/23/hacking-usb-serial-port-adapters/>

![keyspan_all (Custom)](img/415ee0b6f66ae5bcd1e23c26767cb49a.png "keyspan_all (Custom)")

Openschemes.com 的人写了一篇文章，介绍如何[将 USB 串行端口适配器转换为低压串行接口](http://www.openschemes.com/modules/wordpress/2009/09/17/hacking-usb-serial-ports/1/)，以便与微控制器接口。虽然你总是可以只买一个，这是一个相当快速和便宜的解决方案，尤其是如果你手头拮据或者没有零售商。您应该注意的特定型号是带有两个芯片、一个微控制器和一个线路转换器的型号。他们会经历一个过程，寻找确切的接入位置，以添加额外的接口。只需要几根电线，你就可以开始了。

您不仅可以将它用作与另一个微控制器的串行连接，还可以实际控制电路板上的微控制器。如果你加载了 TI 的驱动程序，你就可以访问闪存，做任何你想做的事情。不过，他们在这里没有详细说明，只是说他们会就此写另一篇文章。

我们觉得这个小家伙看起来很眼熟，所以我们翻遍了我们的档案。果然，我们在 2008 年 1 月发现这个系统[在运行。](http://hackaday.com/2008/01/21/embedding-apps-in-wifi-finders/)

[via [被黑的小工具](http://hackedgadgets.com/2009/09/22/usb-to-rs232-adapter-hack/)