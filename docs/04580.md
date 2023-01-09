# BobLight 夜间照明网络

> 原文：<https://hackaday.com/2009/12/22/boblight-night-light-networking/>

![](img/8d83e4cab0aa42e0bf06353786898895.png "x10")

原来，在 X10 网站上可以找到的不仅仅是[女性的图片和闪烁的动画](http://www.x10.com/homepage.htm)。【乔纳森】基于[他的 BobLight 项目](http://gobighometheatre.com/boblight/)围绕[的 MS14A X10](http://www.x10.com/products/x10_ms14a.htm) 模块。

这个设备的想法是从给他岳父岳母的圣诞礼物开始的。当探测到运动时，一个 boblight 打开。然后，它(通过无线电)与其他 boblights 通信，将它们全部打开。如果在一段时间内没有任何一个车灯检测到运动，它们都会熄灭。不是让用户每天早上都关掉所有的灯，而是用一个光传感器来自动完成这项任务。

每个 boblight 都是一个普通的 LED 实用灯，与 MS14A 的电路板结合在一起，并添加了一个 310MHz RF 接收器。他甚至黑掉了主板，用一个更高规格的[型号](http://www.microchip.com/wwwproducts/Devices.aspx?dDocName=en020095)替换了板载 PIC。我们认为[乔纳森]在实现创新概念方面做得很好。