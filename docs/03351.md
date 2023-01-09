# AXiS-49 拆卸

> 原文：<https://hackaday.com/2009/03/31/axis-49-teardown/>

![cthruteardown](img/bae2fcc79021e323317aee445f2da9dd.png "cthruteardown")

当[aris] [正在建造一个](http://hackaday.com/2008/11/29/harmonic-keyboard-controller/ "Harmonic keyboard controller  - Hack a Day")的时候，我们接触到了和声表 MIDI 控制器。[肯·拉什顿]有一个 C-Thru 的商用键盘， [AXiS-49](http://www.c-thru-music.com/cgi/?page=prod_axis-49 "The AXiS-49 USB music interface") ，[拆开这个设备展示它是如何工作的](http://musicscienceguy.vox.com/library/post/the-axis-49-reveled.html "The AXiS-49 Revealed - Vox")。一个 [PIC18F2450](http://www.microchip.com/wwwproducts/Devices.aspx?dDocName=en023497 "PIC18F2450") 微控制器提供 USB 接口，并连接到一个 [dsPIC33FJ128GP310](http://www.microchip.com/wwwproducts/Devices.aspx?dDocName=en024673 "dsPIC33FJ128GP310") 数字信号控制器，后者对按键进行解码。薄膜按钮由两个接触金触点的同心石墨盘制成。微控制器测量两点接触之间的时间，以确定按钮速度。[单体按钮克隆](http://hackaday.com/2009/02/05/sparkfun-releases-rgb-button-controller/ "SparkFun releases RGB button controller  - Hack a Day")也使用圆形接触垫，但是不能计算速度，因为它们只有一个元素。

【通过【T0 矩阵合成】