# 25C3:电力线通信

> 原文：<https://hackaday.com/2008/12/28/25c3-power-line-communication/>

![plc](img/2d7f9a80e3b43fc47ed095ef693a4f31.png "plc")

[Florian]和[Xavier Carcelle]在 [25C3](http://hackaday.com/tag/25c3) 开始一天的工作，由[负责电力线通信](http://events.ccc.de/congress/2008/Fahrplan/events/2901.en.html)。 [PLC](http://en.wikipedia.org/wiki/Power_line_communication) 技术在美国并不普遍，但在法国等国家已经流行起来，在法国，它被包含在机顶盒中。PLC 可让您使用墙上的交流电线创建一个本地网络。该团队开始探索 PLC，因为尽管它是一种较新的技术，但它有一些与旧网络相似的原理。布线中没有分段，这意味着它的行为类似于第 2 层集线器。与交换网络不同，你可以看到所有的流量。大多数功率计不会过滤信号，因此您可能会看到隔壁邻居在您的线路上的流量。[Florian]有报道说，我只需要插上电源就能看到一栋六层大楼里的所有交通。该线路也充当一个大天线，所以你可以使用风暴攻击。

所涉及的技术当然很有趣，但是他们发现缺少使用它的工具。他们写了 [FAIFA](https://dev.open-plc.org/) 来填补这个空白。目前它是一个命令行工具，用于探测和配置基于 Intellon 的 PLC 设备(Intellon 是 PLC 的主要芯片供应商)。你可以查询设备，它甚至有一个嗅探模式。嗅探似乎并不有趣，因为支持 [HomePlug AV](http://en.wikipedia.org/wiki/HomePlug_Powerline_Alliance) 标准的设备使用加密技术，但它们出厂时都使用相同的默认密钥。未来，他们希望构建自己的基于开源 FPGA 的 PLC 设备，以便对系统进行更多的控制。