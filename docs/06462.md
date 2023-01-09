# 让 MSATA 与 Mini PCI Express 一起工作

> 原文：<https://hackaday.com/2010/12/18/making-msata-work-with-mini-pci-express/>

[Trucki]想升级他的 JooJoo 的内部存储器。里面有一个 mSATA 连接器，但使用该协议的设备很难获得，当你这样做时，它们会花费你很多钱。他知道他可以便宜地买到使用 mini PCI Express 标准的固态硬盘，这种标准在机械上与 mSATA 兼容。因此，他着手[改造一个迷你 PCI Express 设备，使其与 mSATA 协议](http://www.thejoojooforum.com/viewtopic.php?f=4&t=776&p=4961)一起工作。这需要交换传输线，并重新安排连接器上的电压走线。为了处理 TX-和 TX+线路，他拆下了去耦电容，并重新调整它们以交换信号。对于 3.3V 线路，他必须切断馈电，并将跳线焊接到正确的焊盘上。

这是一些很好的工作，让他增加了一个 32 GB 的驱动器，只需 60 欧元。由于该设备只配备了 4 GB 的固态硬盘，如果你打算在 Joojoo 上安装替代操作系统，升级几乎是强制性的。