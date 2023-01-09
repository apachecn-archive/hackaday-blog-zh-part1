# Linux(通过 ILoader)推出 Nano 2G

> 原文：<https://hackaday.com/2009/09/11/linux-via-iloader-out-for-nano-2g/>

![Iloader](img/b51716e3b8220f841446a71821855994.png "Iloader")

[ [Linux4Nano](http://home.gna.org/linux4nano/) ]在[ [Gna！仓库](http://gna.org/)刚刚完成了他们的[引导程序](http://en.wikipedia.org/wiki/Booting#Boot_loader)项目的突破。因为 iPod Nano 2G 有一个[硬件加密芯片](http://www.ipodwizard.net/showthread.php?t=30241)，它以前不能用定制的[固件](http://en.wikipedia.org/wiki/Firmware#Portable_music_players)来刷新。通过在[中挖掘一些汇编代码](http://www.arm.com/miscPDFs/9658.pdf)(并施展他们的魔法),团队能够将 Linux 移植到 2G 上，为其外围设备(屏幕、点击轮和串行接口等)开发驱动程序，并且将所有代码放入一个便于最终用户安装的包中。如果你曾经考虑过在你的 Nano 上安装 uClinux(移植的发行版),那么[Linux4Nano]团队已经让 iLoader 成为一个容易的起点。

**更新:**进一步检查发现，iLoader 还不能将 uClinux 加载到 2G 上，因为它还没有被移植。然而，它可以重新加载其他自定义固件，这仍然是一个坚实的突破。