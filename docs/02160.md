# 主要 DNS 问题导致多供应商补丁日

> 原文：<https://hackaday.com/2008/07/08/major-dns-issue-causes-multivendor-patch-day/>

![](img/d028dc6914ae6b96759447c61ba05d9b.png)
今年早些时候，我们的朋友【丹·卡明斯基】在[发现了一个重大的 DNS 问题](http://securosis.com/2008/07/08/dan-kaminsky-discovers-fundamental-issue-in-dns-massive-multivendor-patch-released/)，这个问题可能会让黑客轻易危及域名服务器和客户端的安全。该漏洞涉及缓存中毒，[Kaminsky]计划在 8 月 6 日公布该漏洞的全部细节。然而，他已经开始了他的工作来控制它，在早期就提醒主要当局注意这个漏洞。

因此，来自许多主要技术供应商的工程师们很快开始为 DNS 服务器开发协调一致的补丁。补丁今天全部发布；供应商和 CERT 顾问敦促组织在漏洞成为常识之前立即应用它们。有关 DNS 问题的更多详细信息，请参见[执行概述(PDF 文件)](http://securosis.com/publications/DNS-Executive-Overview.pdf)。[富豪]在[网络安全播客](http://netsecpodcast.com/?p=49)中采访了【丹】。它没有详细说明攻击，但指出使用端口随机化的服务(如 OpenDNS)不受影响，Bind8 已被弃用。

**更新:**这是今天早上新闻发布会的[音频。](https://media.blackhat.com/webinars/blackhat-kaminsky-dns-press-conference.mp3)

[图片: [Flickr / d70focus](http://flickr.com/photos/23905174@N00/1594411528/)

*   [永久链接](http://securosis.com/2008/07/08/dan-kaminsky-discovers-fundamental-issue-in-dns-massive-multivendor-patch-released/)