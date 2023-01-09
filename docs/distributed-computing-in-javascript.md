# JavaScript 中的分布式计算

> 原文：<https://hackaday.com/2009/03/03/distributed-computing-in-javascript/>

![mapreduce](img/4895cc0e2a7a7c56515d749edacf9467.png "mapreduce")

我们听说将浏览器用作分布式计算节点已经有几年了。只是在最近，随着像 Chrome 这样的浏览器向更快的 JavaScript 引擎发展，这个想法才显得有用。[Antimatter15]为反转散列做了一个[概念验证 JavaScript 实现](http://jsdc.appspot.com/)。 [Plura 处理](http://www.pluraprocessing.com/index.html "Plura Processing")使用 Java 小程序进行分布式处理。今天，[伊利亚·格里戈利克]在 JavaScript 中发布了一个使用 MapReduce 的[示例。谷歌的 MapReduce 旨在支持跨计算集群的大型数据集处理。它非常适合计算节点可能随机离线的情况(例如，浏览器导航离开您的站点)。他在 Ruby 中包含了一个 JavaScript 片段和一个作业服务器。看看是否有人想出了这个的好用法，这将是很有趣的；你仍然需要说服人们让你的页面在浏览器中保持打开。我们只是说:当你意识到 Hack a Day 莫名其妙地让你的处理器激增时，试着表现出惊讶…](http://www.igvita.com/2009/03/03/collaborative-map-reduce-in-the-browser/ "Collaborative Map-Reduce in the Browser - igvita.com")

[通过[斜线圆点](http://tech.slashdot.org/article.pl?sid=09/03/03/1910207 "Slashdot | Collaborative Map-Reduce In the Browser")