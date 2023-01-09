# 无源网络抽头

> 原文：<https://hackaday.com/2008/09/14/passive-networking-tap/>

制作一个[无源网络窃听器](http://en.wikipedia.org/wiki/Network_tap)可能是一个简单且廉价的任务，如本[说明书](http://www.instructables.com/id/Make_a_Passive_Network_Tap/)所示。需要被动监控或端口镜像，因为大多数网络使用隔离网络流量的交换机，这不允许监控整个网络。本例使用单抽头，使用[多抽头](http://www.sun.com/bigadmin/content/submitted/passive_ethernet_tap.html)将分别提供对全双工数据的访问。通过使用两个分路器，您可以监控通过一个分路器的入站数据和通过另一个分路器的出站数据。因为大多数嗅探器软件只处理半双工流量，而全双工需要两个网卡，所以需要单独的 tap。

![](img/8eec5403e684c53e1275ee334166c767.png "multi tap")

很容易插入一个无源以太网分接头，如上图所示，来自[不同的 multitap 项目](http://thnetos.wordpress.com/2008/02/22/create-a-passive-network-tap-for-your-home-network/)，只需将输入线插入一个主机端口，并将跳线从另一个主机端口插入输出端口，然后验证您的连接状态。现在将你的嗅探器计算机的以太网端口连接到无源以太网 tap 上的任一 tap 连接器。这种窃听的工作原理是使用嗅探应用程序，将你的[以太网卡置于混杂模式](http://en.wikipedia.org/wiki/Promiscuous_mode)。这允许您监控网络上的所有流量，而不仅仅是定向到您的网络适配器的流量。在你安装了你最喜欢的嗅探器程序后，比如 [Wireshark](http://www.wireshark.org/) 、 [Snort](http://www.snort.org/) 、 [TCPDump](http://www.tcpdump.org/) 、 [WinDump](http://www.winpcap.org/windump/) 或 [Ettercap](http://ettercap.sourceforge.net/) 等等，你就可以以你认为合适的任何方式监控所有流量，比如在下面的视频中寻找密码。

[https://www.youtube.com/embed/7ezGTP99xSw?version=3&rel=0&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/7ezGTP99xSw?version=3&rel=0&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)