# 包含 Conficker

> 原文：<https://hackaday.com/2009/03/30/containing-conficker/>

![conficker](img/462ce5435c95ae9c8879b8b3d3253572.png "conficker")

随着所有关于 [Conficker](http://en.wikipedia.org/wiki/Conficker "Conficker - Wikipedia, the free encyclopedia") 在 4 月 1 日把你的电脑变成液态热岩浆的噪音，实际上有一些积极的消息。来自[蜜网项目](http://www.honeynet.org/ "Honeynet Project Blog | The Honeynet Project")的研究人员从 2008 年末蠕虫开始感染以来就一直在跟踪它。他们最近发现了一种远程识别受感染系统的简单方法。Conficker 试图在感染期间修补 MS08-067 漏洞。补丁中的一个缺陷导致机器的响应不同于未打补丁的系统和正式打补丁的系统。利用这一知识，该团队用 python 开发了一个概念验证网络扫描器来查找受感染的机器。可以在[【有钱的莫古尔】的初始帖](http://securosis.com/2009/03/30/easily-detect-conficker-infections-over-the-network/ "(Updated) Easily Detect Conficker Infections- Over the Network | securosis.com")中找到。[丹·卡米尼斯基]已经把它打包成一个 EXE 文件[，并给出了如何构建 SVN 版本的](http://www.doxpara.com/?p=1291 "Tools, Tools, Tools : DoxPara Research")[Nmap](http://nmap.org/ "Nmap - Free Security Scanner For Network Exploration & Security Audits.")的说明，其中包括新的签名。其他网络扫描仪供应商也在添加代码。

结合这个检测代码，该团队还发布了白皮书[了解你的敌人:包含 Conficker](http://www.honeynet.org/papers/conficker "Know Your Enemy: Containing Conficker | The Honeynet Project") 。它讨论了检测、遏制和删除 Conficker 的方法。他们将此与一个[工具发布](http://iv.cs.uni-bonn.de/wg/cs/applications/containing-conficker/ "Informatik IV: Containing Conficker")结合起来，该工具涵盖了 Conficker 的动态域生成等内容。