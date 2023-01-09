# CCCamp 2007: GSM A5 破解

> 原文：<https://hackaday.com/2007/08/11/cccamp-2007-gsm-a5-cracking/>

Steve Schear 和 David Hulton 做了一个关于 A5 破解的演讲。A5 是 GSM 手机网络在手机和发射塔(网络中的其他地方)之间采用的加密技术。为了监听 GSM 频段，他们使用 GNU 无线电 [USRP](http://www.ettus.com/) 。 [GNU radio](http://gnuradio.org/trac) 是一个软件定义的无线电项目，付出一些努力，你应该能够在任何射频波段接收和发射。你可以用它来播放数字电视，追踪无线电标签，甚至摆弄车库开门器。在最初的研究中，他们使用诺基亚 3310 在跟踪模式下转储初始帧。使用一个至少有 27 个 FPGA 的盒子，他们计划构建一个 6tb 以上的彩虹表(这将需要几个月的时间)。一旦完成，任何 GSM 对话都可以在不到 5 分钟的时间内用一个 FPGA 破解。《黑客选择》有更多关于基于 USRP 的 GSM 分析仪的信息和[他们如何破解 A5](http://wiki.thc.org/cracking_a5) 。

*   [永久链接](http://wiki.thc.org/cracking_a5)