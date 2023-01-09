# 扫描仪外壳中的 PCB 灯箱

> 原文：<https://hackaday.com/2009/11/10/pcb-light-box-in-a-scanner-shell/>

![scanner-exposure-box](img/85c7ac0a2739110097f7dbf32857c84b.png "scanner-exposure-box")

[Kizo] [将一台平板扫描仪改装成曝光箱](http://www.elektronika.ba/714/darkroom-timer-for-pcb-exposure/)用于制作印刷电路板。曝光时间由 AVR ATtiny2313 微控制器控制。该器件连接到一个单独的显示板，使用一个移位寄存器控制四个 7 段显示器。时间以十秒为增量设置，一旦启动，就会用继电器打开灯。一旦达到正确的曝光时间，灯就会关闭，压电扬声器就会发出嗡嗡声。没有提到他使用的灯泡类型，但它们看起来像紧凑型荧光灯，下面有锡箔作为反射器。

如果这些只是 CFL 灯泡，其性能与基于紫外线光源的灯箱相比如何？

[谢谢杰克]