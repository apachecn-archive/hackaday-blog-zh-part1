# 超高频能量采集

> 原文：<https://hackaday.com/2009/01/29/uhf-power-harvesting/>

![hdpowerharvesting](img/a380055e85ee6e8ffd6fef6cfba8fd9f.png "hdpowerharvesting")

[Alanson Sample]和[Joshua R. Smith]一直在为他们的传感平台进行[无线电力传输的实验。他们选择的微控制器是 MSP430，我们在我们的](http://www.techonline.com/learning/techpaper/212902041 "TechOnline | Experimental Results with two Wireless Power Transfer Systems")[电子纸时钟](http://hackaday.com/2008/10/14/how-to-make-an-e-paper-clock-and-hack-esquire-magazine/ "Make an e-paper clock from Esquire magazine  - Hack a Day")上使用了它。他们特别选择了它在低电压下工作能力，并讨论了它在不同电压下的特殊行为。他们论文的第一部分使用超高频 [RFID](http://hackaday.com/tag/rfid/ "rfid  - Hack a Day") 阅读器向传感器的四级电荷泵传输信号。他们添加了一个超级电容，在节点不在阅读器附近时，为 24 小时的日志记录提供足够的电力。在论文的后半部分，他们使用了一种为数字电视设计的超高频天线，使用相同的电路，并将其指向约 4.1 公里外的电视塔。它的开路电压为 5.0V，8KOhm 负载上的开路电压为 0.7V，计算得出功率为 60uW。他们将它连接到上图中温度计/湿度计的 AAA 电池端子上。它工作没有问题。温度计在 1.5V 时消耗实验室电源 25uA

这是一种为设备供电的有趣方法。您的应用程序需要这样的东西吗？关于无线电力的更多信息，请查看这篇关于 [scratch building RFID 标签](http://hackaday.com/2008/11/11/scratch-built-rfid-tags/ "Scratch built RFID tags  - Hack a Day")的早期文章。

[via [DVICE](http://dvice.com/archives/2009/01/intel_snags_ene.php "Intel snags energy out of thin air, tinfoil hat crowd cowers in the basement")