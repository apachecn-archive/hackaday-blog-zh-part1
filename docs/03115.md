# 在 Amazon EC2 上使用 Bittorrent

> 原文：<https://hackaday.com/2009/01/17/using-bittorrent-on-amazon-ec2/>

![](img/a18936ce281e2a13751122e6cfd513d9.png)

Bittorrent 是一种很好的大文件分发方法，但是它的大量带宽使用可能会破坏工作和家庭网络。【布雷特·奥康纳】已经决定[把他所有的种子活动都推到云端](http://negatendo.net/blog/2009/01/17/howto-use-amazon-ec2-for-bittorrent/ "Negatendo.Net  » Blog Archive   » HOWTO Use Amazon EC2 for Bittorrent")。亚马逊的 [EC2](http://aws.amazon.com/ec2/ "Amazon Elastic Compute Cloud (Amazon EC2)") 服务可以让你在硬件上运行任意数量的亚马逊机器映像(AMI，虚拟机)。您需要为处理时间和传输的数据付费。[Brett]为在服务上构建自己的 [seedbox](http://hackaday.com/2008/07/17/should-you-get-a-seedbox-for-your-bittorrent-needs/ "Should you get a seedbox for your bittorrent needs?  - Hack a Day") 整理一份指南。首先，设置安全组，即机器的防火墙。接下来，指定想要使用的 AMI。在这个例子中，它是一个社区版本的 Ubuntu。一旦有了 SSH 密钥对，就可以启动实例并安装 Apache、PHP 和 MySQL。在这种情况下， [TorrentFlux](http://www.torrentflux.com/ "TorrentFlux - PHP BitTorrent Client") 是 bittorrent 的 web 前端。它管理所有的种子，当你想抓取完整的文件时，你只需要点击下载。

即使你不打算设置 seedbox，这篇文章也是一个简单的例子，告诉你如何开始使用 EC2。他不确定成本会是多少；目前的估计是每月大约 30 美元。

[via [蜡质](http://waxy.org/links/ "Links Miniblog")

[photo: [nrkbeta](http://flickr.com/photos/nrkbeta/2305831708/) ]