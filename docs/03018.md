# 25C3:太阳能为你的装备提供动力

> 原文：<https://hackaday.com/2008/12/27/25c3-solar-powering-your-gear/>

![solar](img/404ebf718bafc8a809d6296b9a61e2e5.png "solar")

第 25 届混沌通信大会正在柏林举行。我们参加的第一个讲座是[script]的[太阳能为你的极客装备](http://events.ccc.de/congress/2008/Fahrplan/events/2904.en.html "Solar-powering your Geek Gear")。虽然市场上有相当多的便携式太阳能产品，但到目前为止，我们还没有看到太多的真实世界体验。

[script]经过一番研究，选择了四段折叠式太阳能电池板。他指出，太阳能目前更像是一种必需的技术，而不是省钱的技术，因为太阳能板可能非常昂贵。对于连接器，他推荐了安全、极化、难以短路的连接器，比如他使用的 [RIA connect](http://www.riaconnect.com/ "RIA CONNECT manufactures terminal blocks, modular jacks and USB ports.") 230 系列。大多数设备插头都很容易买到，但有些是从旧的交流适配器中抢救出来的。他的装置的一个关键部件是[可调电压调节器](http://www.elv.de/Universal-Step-up-Step-down-Spannungswandler-USW-525,-Komplettbausatz/x.aspx/cid_74/detail_10/detail2_14231 "Universal-Step-up / Step-down-Spannungswandler USW 525, Komplettbausatz | ELV-Elektronik")。它基于 LTC3780 降压-升压控制器，效率为 98%，可在 4V 至 25V 范围内调节。

[script]讲述了他在使用中遇到的一些问题。第一个是诺基亚，它拒绝充电，直到增加一个电阻来减少电流。不太敏感的设备，如便携式帕尔贴冰箱将没有任何问题。对于笔记本电脑的使用，他遇到了需求峰值扼杀电力输送的问题。他增加了一个通常用于汽车音响系统的大电容，以使功率输出更加稳定。笔记本电脑在正常使用时的功耗只有 15 瓦，但当它们给电池充电时，功耗可能会飙升至 50 瓦。在他的 ThinkPad 上，他可以关闭充电来防止这种情况。他通过使用 ATmega8 测量电流和电压并将其记录到 EEPROM 中，构建了一个[杀死一瓦](http://hackaday.com/2008/11/10/kill-a-watt-teardown/ "Kill A Watt teardown  - Hack a Day")类型的设备，来监控面板的性能。

总之，[script]表示他对自己的体验很满意，但是在阳光直射之外的任何地方使用便携式面板仍然不切实际。