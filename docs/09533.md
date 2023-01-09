# 编译 OpenWRT 的完整指南

> 原文：<https://hackaday.com/2012/01/19/complete-guide-to-compiling-openwrt/>

![](img/0068cf89475098319c8741b1e4018130.png "wrt-feat")

普通读者[MS3FGX]最近从源代码为[写了一个编译 OpenWRT 的指南。你可能想知道为什么编译开源程序的方向值得如此关注。软件包的大小和范围使您很难在过程的每一点遍历可用的选项，但是[MS3FGX]通过一路上尽可能多的讨论增加了清晰度。](http://www.thepowerbase.com/2012/01/openwrt-build-guide-start-to-finish/)

OpenWRT 是一个开源的替代固件包，可以在许多路由器上运行。这是一种释放 Linksys WRT54G 潜力的方式。但是用户界面的多功能性，以及 Linux 内核的可访问性[使得它成为任何路由器的必备](http://hackaday.com/2012/01/12/cheap-wifi-bridge-for-pen-testing-or-otherwise/)。这是使构建过程变得复杂的部分原因。有许多不同的架构支持，你必须配置软件包，为您的特定硬件(或风险坏固件闪存！).

你需要一些笨重的硬件来减少处理时间。源文件包大约有 300 MB，但是在编译之后，磁盘使用量将达到千兆字节范围。[MS3FGX]使用 6 核处理器进行编译，但它仍然需要 20 多分钟才能完成一个基本的发行版。难怪预构建的二进制文件是我们唯一尝试过的东西。但是这是一个向你介绍这个包的内部工作的好方法，并且可能成为一个令人沮丧的有趣的周末项目。