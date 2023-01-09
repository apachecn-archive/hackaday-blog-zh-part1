# 存储公司如何构建自己的

> 原文：<https://hackaday.com/2009/09/04/how-a-storoage-company-builds-their-own/>

![blackblaze_storage_pods](img/d94bf0cdc4e806928038548b129b87f4.png "blackblaze_storage_pods")

想要 67tb 的本地存储吗？那要 7867 美元，但前提是你要自己动手。Blackblaze 销售在线存储，但在成立他们的公司时，他们发现唯一经济的方法是构建自己的存储舱。对我们来说幸运的是，他们[跟随其他公司](http://hackaday.com/2009/04/11/googles-servers-revealed/)的脚步，决定分享[他们如何使用一些定制、一些消费者和一些开源组件构建自己的存储场](http://blog.backblaze.com/2009/09/01/petabytes-on-a-budget-how-to-build-cheap-cloud-storage/)。

每个 pod 都是一个独立的 [HTTPS 连接的](http://en.wikipedia.org/wiki/HTTP_Secure)存储单元，其中有 45 个硬盘驱动器。九个 SATA 端口扩展器连接到主板上的 4 个 SATA 控制器卡。系统从第 46 块硬盘启动，进入 64 位 [debian](http://www.debian.org/) 。驱动器正在运行 [RAID 6](http://en.wikipedia.org/wiki/Raid6#RAID_6) 并使用[日志文件系统(JFS)](http://en.wikipedia.org/wiki/JFS_(file_system)) 。当我们阅读这篇文章时，首先想到的是这些驱动器产生的热量。一个定制的机箱容纳了所有这些硬件，并包括 6 个大风扇来负责冷却。

[谢谢戴夫]