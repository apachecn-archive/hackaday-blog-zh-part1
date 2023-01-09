# 软件脉宽调制

> 原文：<https://hackaday.com/2009/09/17/software-pulse-width-modulation/>

![daqq_pwm_schematic](img/29c0b8280fe45cb222c6f33ba4f7e22a.png "daqq_pwm_schematic")

脉宽调制是一个容易给许多初学者带来麻烦的话题。[Daqq]，[几天前我们报道过他的谢妮等离子球](http://hackaday.com/2009/09/15/nixie-plasma-ball/)，他有一个简单但有效的 PWM 项目，你应该看看。该电路使用 9 个 led，组合成 3 组 RGB 模块，并通过一些限流电阻连接到 AVR ATtiny2313。大多数情况下，AVR 定时器的 PWM 功能将用于产生信号，但该应用需要 9 个信号，超出了该芯片所能产生的信号。解决方法是使用软件 PWM 产生信号。

确保你[熟读 PWM](http://www.netrino.com/Embedded-Systems/How-To/PWM-Pulse-Width-Modulation) 。一旦你对你要做的事情有了一个好的想法，看看[Daqq]在他的 [YALBlinkie 项目](http://www.daqq.eu/index.php?show=prj_yabled)中包含的代码。在研究项目包中的 main.c 时，请注意一个计时器正在运行，它会定期调整每个信号的占空比。同时，main 中的无限循环不断地用定时器设置的占空比值扫描输出引脚。这导致发光二极管点亮的时间慢慢改变，使它们渐亮和渐暗。

因为 ATtiny2313 非常便宜，这是一个使用 AVR 系列微处理器的好方法。你需要一个程序员，但是有办法使用 Arduino 对这些芯片编程。要了解更多关于定时器中断和这些芯片如何工作的信息，请查看 AVR freaks 的[教程部分。还可以看看 avr-libc 文档，了解如何在[Daqq 的]代码中](http://www.avrfreaks.net/index.php?name=PNphpBB2&file=viewforum&f=11&sid=dc85503b2c81a29f15b88f4041baa9bd)[修复不推荐使用的 sbi 和 cbi 命令](http://www.nongnu.org/avr-libc/user-manual/group__avr__sfr.html)。

[https://www.youtube.com/embed/YAT7-fsnA4Q?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/YAT7-fsnA4Q?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)