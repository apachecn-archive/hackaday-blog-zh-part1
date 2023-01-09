# 黑掉安吉星全球定位系统 V2

> 原文：<https://hackaday.com/2009/12/26/hacking-the-onstar-gps-v2/>

![](img/62b36677d04329eb7f9c8e9086820bf1.png "onstar-logo1 (1)")

[安迪]为我们提供了他的新指南[黑掉 OnStar GPS](http://sites.google.com/site/radioetcetera/home/onstar-gps) 。之前，我们已经介绍了一种从[未使用的 OnStar 系统](http://hackaday.com/2005/03/29/gm-onstar-hacking/)中获取 GPS 数据的方法，然而近年来通用汽车增加了更复杂的系统，这比更换串行线更难。对于新版本，[安迪]已经弄清楚了通用汽车的控制器局域网(CAN)，他们称之为 [GMLAN](http://en.wikipedia.org/wiki/GMLAN) 。他还完成了大部分的软件窥探和侦查工作，并且基本上解决了 GMLAN 公布 GPS 数据的方法。有示例代码可以将这些信息转换成通用的纬度和经度。

对这个项目来说不幸的是，(对[Andy]来说非常幸运的是)，他有一个即将出生的孩子和新的工作职责，所以他将他的结果提供给 HaD 社区来完成、复查，并为其他人提供一个好的方法。对于任何决定接下这个项目并执行它的人，请告诉我们！