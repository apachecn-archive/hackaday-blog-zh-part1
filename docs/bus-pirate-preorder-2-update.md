# 巴士海盗预购 2 更新

> 原文：<https://hackaday.com/2009/07/23/bus-pirate-preorder-2-update/>

![bp-unbox-0](img/b6ed3daecf541cf00b6a21a4a782c002.png "bp-unbox-0")

几周前，我们[为](http://hackaday.com/2009/06/25/bus-pirate-preorders-open/)[的总线盗版通用串行接口工具](http://www.buspirate.com/)举行了预购。由于缺少 [PIC 24FJ64GA002-I/SO](http://www.microchip.com/wwwproducts/Devices.aspx?dDocName=en026374) 芯片，我们将预购分成两部分。第一个预定订单是[现在全球到货](http://hackaday.com/2009/07/20/parts-unboxing-the-bus-pirate/)，第二个预定订单[有一个更长的交付周期](http://hackaday.com/2009/06/30/bus-pirate-preorder-update/)。这是我们目前所知道的关于 preorder 2 的一切，它可能会发生变化，但我们希望让您了解最新情况。

预订 2 包含 563 辆巴士海盗的订单。Seeed Studio 注意到在我们的质量控制测试程序中有一个错误，将大约 50 个预订 1 总线盗版错误分类为有缺陷。我们[更新了测试](http://code.google.com/p/the-bus-pirate/source/detail?r=146)，通过测试的单位将立即发货，以先到先得的方式预订 2 名参与者。另外 500 张照片计划在 8 月 1 日之后到达，这将会处理大部分剩余订单。

特别感谢[微芯片](http://www.microchip.com)的出色工程师，他们花时间仔细阅读了总线盗版代码，并立即给出了我们质量控制问题的正确解决方案。干得好，微芯片，谢谢！

我们发布了总线盗版固件包的更新版本。固件是完全一样的，我们只是改变了 P24qp.exe 快速编程器实用程序的速度设置。在开发过程中，我们提高了 quick programmer 的波特率，以使开发更快，但我们忘记了将它改回正常使用的安全速度。