# 便携式磁卡阅读器

> 原文：<https://hackaday.com/2006/05/01/portable-magnetic-card-reader/>

![portable magnetic card reader](img/4ec7fec0b2c820201605a1f3dbe5ba4c.png)

[ned]的 HandySwipe 是一个[便携式磁卡读卡器](http://camelspit.org/handyswipe/)。它依靠 4 节 AA 电池运行，并从轨道 2 卡收集数据。它使用 PIC 16F688，并在一个小 LCD 上显示卡的数据。它可以存储多达 50 张卡，并以 CSV 格式转储它们。它还将输出原始比特流，供 Acidus 的 [StripeSnoop](http://stripesnoop.sourceforge.net/index.html) 使用。Ned 的项目记录非常有趣，因为他涵盖了在刷卡时使用逻辑分析仪，以及使用移位寄存器只用三个引脚驱动 LCD。

*   [永久链接](http://camelspit.org/handyswipe/)