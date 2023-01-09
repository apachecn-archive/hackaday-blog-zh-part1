# 用晶体管-晶体管逻辑构建的处理器

> 原文：<https://hackaday.com/2009/10/30/processor-built-with-transistor-transistor-logic/>

![cpu-built-from-ttl](img/83b467c31d2bdea84892bf3cbff678b5.png "cpu-built-from-ttl")

[Donn]想要确切地知道处理器内部发生了什么，所以很自然地[他用 TTL 组件构建了一个 CPU](http://cpuville.com/)。他之前已经基于 Z80 处理器制造了几个版本的电脑[。利用他学到的故障排除技巧和一本二手教科书，他开始使用 74LS 系列芯片工作，这些芯片使用我们在其他 cpu 项目](http://hackaday.com/2009/09/07/proto-board-z80-computer/)中熟悉的[绕线方法连接。](http://hackaday.com/2009/02/27/bmow-a-home-made-cpu/)

成品在 1.8 兆赫下运行良好，但他还包括一个 2 赫兹的时钟和一个用于调试的步进时钟。在较慢的速度下，寄存器板(见上图左侧)点亮 led，可以用来告诉 CPU 当前正在做什么。编程是通过哑终端或运行终端仿真器的 PC 来完成的。

他的文章是大约五年前的，但这并不妨碍我们在阅读时在大脑的极客中心获得模糊的感觉。它写得很好，也很全面，所以如果你对这类东西感兴趣，会有很多东西值得欣赏。

[谢谢罗利]