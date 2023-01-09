# TC7 第 1 天–实践中的碎片攻击

> 原文：<https://hackaday.com/2005/09/17/tc7-day-1-the-fragmentation-attack-in-practice/>

![andrea](img/58373b364506803d09983a604aa24684.png)
**更新:** [幻灯片、纸张和代码](http://toorcon.org/2005/slides/abittau/)

Andrea Bittau(现实生活中不模糊)演示了 WEP 碎片攻击。这种攻击只需要一个来自 WEPed 网络的嗅探数据包，而不像重放攻击那样通常需要您获得一个 ARP 数据包。他构建了一个简单的工具来嗅探数据包，然后构建数据包来创建到接入点的合法连接。此时，将联系互联网上的服务器，以每秒 1400 个数据包的速度向网络发送大量数据包。这产生了一吨独特的 IVs 和 aircrack 被调用每 100000 包，直到 WEP 密钥被破解。在演示中，完成自动化流程不到 5 分钟。

*   [永久链接](http://www.darkircop.org/)