# 硬盘密码恢复

> 原文：<https://hackaday.com/2011/02/18/hard-drive-password-recovery/>

这里有一个从 ATA 硬盘恢复保护密码的指南 ( [翻译](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http://elettrofreak.blogspot.com/2011/02/estrarre-le-password-ata-da-un-hard.html))。这些密码存储在硬盘的特殊区域，其中也包含设备的固件。通常情况下，你无法获得它们，但[超音速]带我们了解了一种用于从 Western Digital Scorpio 硬盘中获取数据的方法。启动一个名为 MHDD 的程序，你可以绕过 BIOS(它不允许你读取受保护的数据),直接驱动主板上的 SATA 或 PATA 控制器。一旦你转储了数据，就可以用十六进制编辑器查看，如果你知道在哪里可以找到锁定磁盘的密码。

这让我们想起了一些最初的 Xbox 黑客，他们使用了各种方法来解锁股票硬盘。