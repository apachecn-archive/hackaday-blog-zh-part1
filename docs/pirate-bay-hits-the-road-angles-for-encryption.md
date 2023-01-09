# 海盗湾上路，加密角度

> 原文：<https://hackaday.com/2008/07/10/pirate-bay-hits-the-road-angles-for-encryption/>

![](img/3c8cf4ed607749e403368fd34af2bc81.png)
piratbyrn 和他们来自海盗湾的心上人正在进行一场[泛欧夏季之旅](http://torrentfreak.com/pirate-bay-summer-tour-2008-080710/)，旅程将在意大利 [Manifesta 艺术双年展](http://www.manifesta7.it/)结束，但与此同时，他们一直在努力游说[全网络加密](http://arstechnica.com/news.ars/post/20080709-pirate-bay-wants-total-network-encryption-but-does-anyone-else.html)，这是一种可以保护网络(比如 P2P 网络)用户免受深度数据包检查和其他形式活动分析的系统。

实现这一点的系统称为 IPETEE，它通过替换基本操作系统网络堆栈并自己完成所有加密和解密来工作。更多细节可在 [IPETEE 技术建议书](http://www.tfr.org/wiki/index.php?title=Technical_Proposal_(IPETEE))中找到。

Ars Technica 指出了该方案中的许多漏洞，指出大多数 torrent 应用程序已经有了加密选项。然而，IPETEE 不仅仅适用于 torrents，所以更大的问题是加密的包仍然需要源和目的地 IP 地址，这意味着你想要保持私有的最重要的东西之一(你的目的地站点)仍然是可访问的。

*   [永久链接](http://arstechnica.com/news.ars/post/20080709-pirate-bay-wants-total-network-encryption-but-does-anyone-else.html)