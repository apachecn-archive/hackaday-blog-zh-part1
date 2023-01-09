# 新的 Linux AVR 模拟器

> 原文：<https://hackaday.com/2009/12/20/new-avr-simulator-for-linux/>

![](img/0c81b24b513d2a0af88e88ff26fe7fe7.png "simavr-by-buserror")

simavr 是一款用于 avr 系列微控制器的软件模拟器。你可能会问，考虑到 AVR Studio 提供的模拟器是一个很棒的工具，为什么有人会写这种东西？嗯，很多人不运行 Windows，也不希望使用这种开发环境，即使 Wine 或 Virtualbox 可以实现这一点。

我们自己还没试过。有一个[讨论线程](http://www.avrfreaks.net/index.php?name=PNphpBB2&file=viewtopic&t=86665)正在进行，它报告了将 simavr 与 [GDB](http://www.gnu.org/software/gdb/) 和 [AVR Eclipse](http://avr-eclipse.sourceforge.net/wiki/index.php/The_AVR_Eclipse_Plugin) 一起使用的一些积极结果。这是一个新的一揽子计划，但到目前为止，它似乎已经给人留下了良好的印象。目前支持 ATtiny25/45/85、ATtiny13、ATmega48/88/168 和 ATmega164/324/644 芯片。一些常见的片内外设已经得到支持，其他外设也正在开发中。

你试过了吗？请在评论中告诉我们你的想法。

[ [IC 照片](http://www.ladyada.nimg/parts/atmega168.jpg)