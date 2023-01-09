# Xbox 360 被禁后，恢复 Borked 硬盘

> 原文：<https://hackaday.com/2009/11/25/recover-borked-hdd-after-xbox-360-ban/>

[![](img/d95c0dd4cc0446e2b642933c8187b4f2.png "xbox-360-hdd-unscrambling")](http://hackaday.com/files/2009/11/xbox-360-hdd-unscrambling.jpg)

[Incudie]向我们透露了一种修复 Xbox 360 中损坏硬盘的方法。本月早些时候被禁的[100 万台](http://hackaday.com/2009/11/17/banned-xbox-360s-boon-or-bust/)游戏机中的许多硬盘也被加密，使得离线游戏无法进行。原来这是主板上的 NAND 芯片里有 ban 标志造成的。已经发现，由于[损耗均衡](http://en.wikipedia.org/wiki/Wear_levelling)，NAND 将具有存储禁止标志的“secdata.bin”文件的两个副本。请注意，这将不允许主机使用 Xbox Live，它只是重新启用硬盘。

快速和肮脏的修复如下:首先将 [NAND 从你的 Xbox 360 转储到一台计算机上。验证文件后，可以在十六进制编辑器中打开它，并找到“secdata.bin”的两个副本。一旦通过日期识别，旧版本被注入到新版本的顶部以覆盖 ban 标志。](http://forums.xbox-scene.com/index.php?showtopic=690493)

看起来这不适合胆小的人，但是如果你因为修改而被禁止，这应该很容易实现。

**更新**:看起来 xbox-scene 现在有了一个[应用集合来帮助你](http://www.xbox-scene.com/xbox1data/sep/EkVAklFEykKVCRayhA.php)完成这个过程。[谢谢柯林斯小丑]