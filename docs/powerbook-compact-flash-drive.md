# Powerbook 紧凑型闪存驱动器

> 原文：<https://hackaday.com/2005/12/10/powerbook-compact-flash-drive/>

![powerbook](img/e87aed5f03469cc4bb017979cbd2d74b.png)

这款 Powerbook 150 是作为简单的媒体阅读器购买的。一旦硬盘出现故障，由于 IDE 适配器可用，所有者决定用压缩闪存卡替换它。有一个问题:ATA 设备驱动程序会探测设备，然后立即关闭，因为“识别设备”位不是预期的值。设备驱动程序是在 ATA 规范更新之前编写的。Greg 通过构造一个子卡解决了这个问题，该子卡插入适配器板的 40 针插头，然后在设备最初被探测时翻转识别位。

[谢谢 iamdigitalman]

*   [永久链接](http://www.cosc.canterbury.ac.nz/~greg/hardware/pb150/PB150_and_CompactFlash.html)