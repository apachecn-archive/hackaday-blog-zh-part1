# 从一个 Arduino 输出多达 768 个 PWM 信号

> 原文：<https://hackaday.com/2011/07/20/output-up-to-768-pwm-signals-from-one-arduino/>

![](img/34ffc14a5214cd61d664d77c63217aaa.png "768-pwm-from-arduino")

这是一个 Arduino 库，可以让你驱动大量的 led 灯。【Elco Jacobs】电气工程学生，本库作者。他有一份勤工俭学的工作，帮助其他人完成电气项目，他经常被要求提供控制成群发光二极管的方法。这是促使他在休息后制作视频中看到的令人眼花缭乱的 16 RGB LED 示例的动机。

他的设置没有使用昂贵的 LED 驱动器，而是利用了既普通又便宜的 [595 移位寄存器](http://hackaday.com/2011/03/14/beginner-concepts-595-shift-register-simulator/)。他计算出可以控制多达 96 个这样的移位寄存器，每个驱动 8 个发光二极管，结果相当令人满意。这要归功于他经过优化的代码，该代码能够以 1.33 MHz 的频率驱动寄存器的时钟引脚。这种优化是通过在汇编中编写每个命令来完成的，这允许他精确地计算周期。每个单独的引脚需要 12-13 个周期来寻址，当寻址最大数量的输出时，总共需要 9984 个周期。

[Elco]认为这是他能让程序运行的最快速度，但他正在请求测试方面的帮助。如果你认为你知道如何挤出几个周期，确保你加入他的论坛。

[https://www.youtube.com/embed/MDmOvbga0uA?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/MDmOvbga0uA?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)