# Arduino 气球跟踪

> 原文：<https://hackaday.com/2010/03/17/arduino-balloon-tracking/>

雪貂是一个[高空气球追踪硬件包](http://www.hexoc.com/wb/pages/ferret.php)。由[Adam Greig]和[Jon Sowman]创造，它使用 Arduino 从 GPS 单元收集[NMEA](http://en.wikipedia.org/wiki/NMEA)数据，将数据格式化成字符串，并通过窄带 FM 传输该字符串。这个项目只用了一个下午就完成了，是对 Arduino 提供的原型简单性的一种致敬。

该装置由四节 AA 电池供电，使用 Arduino 的板载电压调节器。这提供了一点热量，有助于寒冷的高层大气。上面的包裹被放在一个项目箱中，并连接到气球有效载荷的外部，然后用泡沫覆盖以保暖和防潮。这种跟踪比我们见过的一些气球摄影设置要简单得多。它也更加通用，因为它广播 GPS 数据，这样许多人可以跟踪它，而不仅仅是[记录它的位置](http://hackaday.com/2007/09/13/another-gps-logger/)。