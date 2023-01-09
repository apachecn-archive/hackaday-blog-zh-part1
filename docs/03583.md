# Dell Vostro 成就 A90 Hackintosh

> 原文：<https://hackaday.com/2009/06/16/dell-vostro-a90-hackintosh/>

![dell_vostro_a90](img/10dcba849aac8c3c59d4aa48931facff.png "dell_vostro_a90")

一个朋友最近委托我们在上网本上安装 OSX。我们建议他购买 Dell Vostro 成就 A90。它本质上是一个重新命名的戴尔 Mini 9，一个已经停产的型号，但是非常适合 OSX。它仅配备 1.6GHz Atom 处理器、1GB RAM 和 16GB SSD。根据不同的交易，价格在 250-300 美元之间。我们还让他购买了 2GB 的内存，这是 BIOS 支持的上限。

之前读过 Gizmodo 的指南，我们知道这个过程不会太难。在过去的几个月里，安装变得更加容易了。我们按照 mechdrew 上的 [DellEFI 指南进行了操作，没有遇到太多问题。我们需要的唯一设备是一个零售的 Leopard 磁盘、一台 Mac 电脑和我们可靠的](http://dellefi.mechdrew.com/guide/method1.shtml "Guide Method 1 - Single USB Drive (Mac-only) | DellEFI | mechdrew") [USB/SATA 适配器](http://www.newegg.com/Product/Product.aspx?Item=N82E16812232002 "Newegg.com - VANTEC CB-ISATAU2 SATA/IDE to USB 2.0 Adapter - Adapters & Gender Changers")，它连接到一个旧的 120GB 笔记本电脑驱动器上。我们将合法的 10.5.6 零售磁盘的映像复制到硬盘上，然后使用 DellEFIBootMaker 使其可引导。我们将 DellEFI 1.2a5 程序和 10.5.7 累积更新也复制到了驱动器中。有了这个，驱动器就有了我们完成安装所需的一切。

将驱动器插入 Vostro 成就 A90 后，我们进入 BIOS 设置，打开 USB 传统支持，这样我们就可以启动驱动器。我们发现，我们通常必须先进入 BIOS，然后退出，以便让驱动器有时间启动并出现在引导菜单中。对笔记本电脑驱动器进行分区后，安装与任何其他 Leopard 安装完全相同。在我们完成安装之前，这个过程在两个不同的场合冻结了。这只是一个尝试，再尝试让它工作的问题。我们认为这可能是我们使用的驱动器的故障。完成后，我们能够启动我们全新的 OSX 机器并安装 10.5.7 更新。我们使用 DellEFI 来安装永久引导程序。

一切似乎都很好，这是一个可爱的小机器。我们强烈推荐在撰写本文时版本为 3.02 的 [DellEFI 单 USB 驱动器方法](http://dellefi.mechdrew.com/guide/method1.shtml "Guide Method 1 - Single USB Drive (Mac-only) | DellEFI | mechdrew")。

[奖励:[黑掉一天壁纸](http://hackaday.com/files/2009/06/had_wallpaper.jpg)由约翰·凯佩尔设计]