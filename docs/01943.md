# 检测 ISP 节流

> 原文：<https://hackaday.com/2008/06/14/detecting-isp-throttling/>

互联网服务提供商最近对他们的客户变得越来越咄咄逼人。他们一直在阻止或改变流量，以防止您使用特定的程序或协议。谷歌的高级政策主管最近表示，他们正在开发工具，允许人们[检测 ISP 干扰](http://www.hothardware.com/News/Google_To_Develop_ISP_Throttling_Detector/)。其他几个团体也在开发工具:T4 网络中立小组刚刚发布了他们的网络测量代理的第二个测试版。该工具目前通过[监控连接的往返时间](http://www.nnsquad.org/nnma-methodology.html)来检测欺骗数据包；早期复位分组将具有低于平均水平的 RTT。如果你想更深入地了解，EFF 已经发布了使用 Wireshark 进行检测的指南[。我们甚至听说有人在一个看起来完全不同的会话中构建工具来隧道化一个会话。](http://www.eff.org/wp/detecting-packet-injection)

[photo: [nrkbeta](http://flickr.com/photos/nrkbeta/2305831708/) ]

*   [永久链接](http://www.nnsquad.org/agent)