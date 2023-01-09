# ATmega 控制器接线升级

> 原文：<https://hackaday.com/2008/11/27/atmega-controller-wiring-upgrade/>

![avrcontroller](img/ed256b371742325286013fddd8cf7e4e.png "avrcontroller")

[jelengar]喜欢 Arduino 的易用性，但想要更多的引脚数。他着手转换 ATmega 控制器，使其与 Arduino IDE 所基于的代码 Wiring T1 一起使用。控制器中的 ATmega128 具有 53 个引脚，而 Arduino 的 ATmega168 只有 11 个引脚。你还会得到 [128kb 的内存](http://www.mahalo.com/RAM "RAM - Mahalo")。这个过程相当简单；你只需要加入适当的晶体。您还可以添加一个开关来触发引导加载程序和状态 LED。