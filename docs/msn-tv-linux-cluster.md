# MSN 电视 Linux 集群

> 原文：<https://hackaday.com/2006/02/12/msn-tv-linux-cluster/>

![msn cluster](img/755fe9a6210bf1966f084b10a4ee5136.png)

我刚刚在 [Engadget](http://www.engadget.com/2006/02/12/the-msn-tv-linux-cluster/) 上看到这个 [MSN TV Linux 集群](http://mirror.toc2rta.com/index.php/Main_Page)。这些盒子有一个 733mhz 赛扬，128MB 内存，2 个 USB，以太网和一个 64MB CF 卡用于存储。这是 Xbox 内存的两倍，节点成本为 0.99 美元，这使得集群更加合理和紧凑。目前唯一的限制似乎是 CF 卡的 64MB 容量上限。

不过，您确实需要构建一条电平转换串行电缆来与之对话。微软在板上包含了串行引脚，这很方便。我认为 TTL 转 RS-232 电平转换盒正在成为继[台式电源](http://pcs.hackaday.com/entry/1234000687042947/)之后第二有用的设备。无论你是在和 [NSLU](http://www.nslu2-linux.org/wiki/HowTo/AddASerialPort) 、 [iPod](http://ipodlinux.org/Serial_Port) 、 [GP2X](http://wiki.gp2x.org/wiki/Serial_cable) 还是 [WRT54G](http://www.rwhitby.net/wrt54gs/serial.html) 通话，你都需要进行串行电平转换。你还不如[把这个东西做成 USB](http://www.ftdichip.com/Products/FT232BM.htm) 的。那么，谁想做操作指南？

*   [永久链接](http://mirror.toc2rta.com/index.php/Main_Page)