# 收集和分析心电图数据

> 原文：<https://hackaday.com/2009/08/22/collect-and-analyze-ecg-data/>

![ecg](img/355bce57048fce8f4425c38e1f365475.png "ecg")

虽然我们在之前已经介绍过 [DIY 心电图](http://hackaday.com/2008/05/26/make-an-ecg-with-your-sound-card/) [，但是【斯科特·哈登】发来了他的版本](http://hackaday.com/2007/02/02/build-your-own-ecg-heart-monitor/)[，对如何处理收集到的数据做了深入的解释](http://www.swharden.com/blog/2009-08-14-diy-ecg-machine-on-the-cheap/)。他以不到 1 美元的价格制造了一款基于电池供电运算放大器的基本心电图仪。该电路只是放大来自胸导联的信号，并通过麦克风端口将其输入计算机。然后他用金波来记录、过滤和保存信号。在那里，他使用 python 来分析心跳，计算他的心率，并进一步处理数据。他之前的博客文章[更详细地介绍了 python 代码是如何工作的，以及他为什么选择软件而不是硬件过滤器。](http://www.swharden.com/blog/category/diy-ecg-home-made-electrocardiogram/)