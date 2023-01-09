# blok clok–抽象时间显示

> 原文：<https://hackaday.com/2009/09/21/blokclok-abstract-time-display/>

![blokclok_abstract_time_display](img/154f287380b1b56e66c06b439db5f653.png "blokclok_abstract_time_display")

由[闪烁的发光二极管](http://hackaday.com/2009/04/08/the-bulbdial-clock-comes-to-life/)制成的时钟总是有利于有趣的项目。[Earthshine]建造了一个使用 8×8 RGB LED 矩阵抽象显示时间的[时钟](http://www.instructables.com/id/The-BlokClok-Concept-Arduino-driven-RGB-A/)。插播的视频演示了如何读取时间，但要点是:一个 LED 在 LED 的外部盒子中点亮，并以顺时针方向移动大约几秒钟。在这里面，有四个象限；左上角表示小时-十位数，右上角表示小时-个位数，左下角表示分-十位数，右下角表示分-个位数。这当然是一个有趣的话题！

没有可用的原理图和代码，但这确实是我们感兴趣的概念。如果你一定要知道的话，[Earthshine]这个建筑是基于一个 Arduino 的。DS1307 [实时时钟](http://hackaday.com/2009/06/26/parts-i2c-real-time-clock-calendar-pcf8563/)保持时间，而四个 74HC595 移位寄存器用于控制三种 LED 颜色和多路复用。

[https://player.vimeo.com/video/6668031](https://player.vimeo.com/video/6668031)