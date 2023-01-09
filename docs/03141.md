# 瓦特彻，推特上发布了杀死瓦特的计划

> 原文：<https://hackaday.com/2009/01/24/wattcher-twittering-kill-a-watt-plans-posted/>

![kill-a-watt](img/af62d345b8b82aaa77ae52df6bfbd739.png "kill-a-watt")

本周早些时候，你可能已经看过菲利普·托伦和利莫尔·弗里德的推特。这是 T2 core 77/Greener Gadgets 设计竞赛的参赛作品。我们看到了一点关于它是如何组装的，但现在他们已经发布了一个[组装硬件](http://www.ladyada.net/make/wattcher/ "Wattcher")的完整指南。每杀死一瓦特，就会得到一个 XBee 无线电，它会传回一个记录用电量的接收器。将这种设计放在一起的困难部分是 XBee 在发射时需要 50mA。这远远高于 Kill A Watt 的内部电源。他们通过添加一个 10，000uF 的超级电容作为可充电电池来弥补这一缺陷。每日推特只是这个项目的一个副作用。每 2 秒钟发射一瓦特，所以你会得到一个非常准确的用电量报告。对于无法永久改造电力基础设施的租户来说，这是一个非常好的项目。每个 Kill A Watt 可以支持相当多的设备，因为它们的额定功率为 15A ~ 1800 w。