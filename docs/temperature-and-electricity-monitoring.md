# 温度和电力监控

> 原文：<https://hackaday.com/2009/12/23/temperature-and-electricity-monitoring/>

![](img/1c115d3c862b76388edbd90434be8f57.png "temperature-and-power-arduino")

[Willem]一直在使用一个 [Arduino 来监控温度和用电量](http://www.secretbatcave.co.uk/electronics/arduino/arduino-house-monitor.html)。为了进行温度监控，他拿起了一些单线温度传感器，类似于我们过去[展示的那些](http://hackaday.com/2008/12/10/parts-1-wire-temperature-sensor-ds1822/)。为了获取用电量，他没有使用[安培传感器](http://hackaday.com/2009/12/21/c-clamp-current-monitoring/)，但因为他在英国，他的电表上确实有一个闪烁的 LED。有一个[已知的技巧](http://hackaday.com/2007/05/30/uk-power-meter-monitor/)用光电池捕捉这些闪光，根据电表读数计算能源使用量。最后，来自三个传感器(室内温度、室外温度和能源使用)的数据通过以太网屏蔽通过互联网传输，以便收集和绘制图表。

这个系统已经运行了一年了。如果你爱管闲事，你可以看看从他收集的数据生成的[温度图](http://www.secretbatcave.co.uk/electronics/arduino/tempYear.png)。