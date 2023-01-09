# Zigbee AES 密钥嗅探

> 原文：<https://hackaday.com/2009/03/15/zigbee-aes-key-sniffing/>

![zigbeesniffing](img/f1bd2fb557d7d779053cde6210517898.png "zigbeesniffing")

[Travis Goodspeed]发布了他为今年夏天的会议所做工作的预览。上周末，他在 [SOURCE Boston](http://www.sourceconference.com/ "SOURCE Conference") 做了一个在 Zigbee 硬件上[嗅探 AES128 密钥的快速演示。CC2420 无线电模块用于许多 Zigbee/802.15.4 传感器网络，密钥必须通过 SPI 总线传输到模块。[Travis]使用](http://travisgoodspeed.blogspot.com/2009/03/breaking-802154-aes128-by-syringe.html "Travis Goodspeed's Blog: Breaking 802.15.4 AES128 by Syringe")[两个注射器探针](http://hackaday.com/2008/06/15/syringe-logic-probe-revision-2/ "Syringe logic probe, revision 2  - Hack a Day")来监控时钟线和 TelosB 微尘上的数据，TelosB 微尘使用 CC2420。现在他已经获得了捕获，他计划创建一个脚本来自动查找密钥。