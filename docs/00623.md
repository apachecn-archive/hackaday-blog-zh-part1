# 入侵摩托罗拉 A780

> 原文：<https://hackaday.com/2005/10/18/hacking-the-motorola-a780/>

![A780](img/8d6d207c225d665c32f2fb2b93da16d3.png)

摩托罗拉 A780 是一款基于 Linux 的四频 GSM 手机。内核黑客哈拉尔德·韦尔特拿起了其中一部手机，[开始在系统中四处窥探](http://gnumonks.org/%7Elaforge/weblog/linux/a780/index.html)。首先要注意的是，这款手机没有使用大多数嵌入式系统中常见的典型轻量级工具。它不使用 busybox 或 uClibc，而是使用它们更重的对应物。该手机也有 2.4 内核，切换到 2.6 内核是一个长期目标。Harald 成功构建了一个兼容的工具链，并在 A780 上运行 netfilter/iptables。应该可以在 GPRS 和 USB 连接之间构建防火墙。其他黑客正致力于添加 Linux 蓝牙代码库；这可能是首批支持 A2DP 立体声耳机的手机之一。对于黑客来说，未来看起来很光明，每天都有新的可利用功能出现，如处理器的 JTAG 垫和内置于工厂代码中的调试回调。Harald Welte 将于 12 月在[第 22 届混沌通信大会](http://www.ccc.de/congress/2005/?language=en)上展示这些和未来的发现。

*   [永久链接](http://gnumonks.org/~laforge/weblog/linux/a780/index.html)