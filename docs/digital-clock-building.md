# 数字时钟建筑

> 原文：<https://hackaday.com/2008/12/22/digital-clock-building/>

![clock](img/4ca992d12f53b254455d828eda10ada0.png "clock")

[punkky]一直在记录他建造数字时钟的冒险经历。他们每个人都使用六个 7 段 LED 显示屏，但他一直在逐步改变他们是如何建立的。第一个版本在每个显示器上使用了 CMOS BCD-to-7-sement 锁存器，它连接到 PIC16F627a。在下一次运行中，他[增加了多路复用](http://picnote.blogspot.com/2008/12/led-7-segment-multiplexing.html "LED 7-Segment Multiplexing | PIC Microcontroller Note")，这样他就可以只用十三个引脚驱动所有的段。他贴出了最后的原理图，包括代码和[时钟计时实际工作方式的细节](http://picnote.blogspot.com/2008/11/6-digit-led-7-segment-multiplexing.html "6 Digits LED 7-Segment Multiplexing | PIC Microcontroller Note")。