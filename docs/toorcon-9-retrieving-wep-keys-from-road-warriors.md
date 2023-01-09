# ToorCon 9:从出差族那里获取 WEP 密钥

> 原文：<https://hackaday.com/2007/10/23/toorcon-9-retrieving-wep-keys-from-road-warriors/>

[![](img/8ece28e3a44b1a5726bb240502fb84f0.png)](http://flickr.com/photos/mattw/1635671617/in/set-72157602526889792/)
【Vivek Ramachandran】咖啡馆的拿铁袭击是我们在 ToorCon 抓到的最后一次谈话之一。我找到了不少关于它的文章，但没有一篇真正正确。这是相当简单的，处理从无关的笔记本电脑破解 WEP 密钥。首先，您的 WEP 蜜罐告诉客户端它已经成功关联。客户端做的下一件事是广播一个 WEP 加密的 ARP 数据包。通过翻转 ARP 信息包中的位，您可以重放 WEP 信息包，客户端会认为它来自网络上另一台主机的 IP MAC 组合。所有的回复都有独特的 iv，一旦你得到 60K，你就可以用 [PTW](http://www.cdc.informatik.tu-darmstadt.de/aircrack-ptw/) 破解它。比特翻转与我们之前讨论的碎片攻击中使用的技术相同，但是拿铁咖啡需要生成的数据包要少得多。你可以阅读关于[咖啡拿铁攻击密闭网络](http://www.airtightnetworks.net/knowledgecenter/wep-caffelatte.html)。

*   [永久链接](http://www.airtightnetworks.net/knowledgecenter/wep-caffelatte.html)