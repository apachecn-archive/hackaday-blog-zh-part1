# 使用 Eclipse 调试 MSP430

> 原文：<https://hackaday.com/2011/02/24/debugging-msp430-using-eclipse/>

[Springuin]刚刚贴了一个关于[使用 Eclipse](http://springuin.nl/en/articles/launchpadwindows) 调试 MSP430 项目的教程。他阅读了我们关于 IAR 下的[调试的专题，IAR](http://hackaday.com/2011/02/15/learn-to-debug-msp430-chips-using-iar/)是 TI 作为代码受限的免费赠品提供给 TI Launchpad 的专有 IDE。在那篇文章中，我们想知道是否有人会使用像 DDD 和 GDB 这样的开源工具编写一个教程，让那些选择使用 Windows 以外的操作系统的人更容易调试。即使他没有直接使用那些特定的包，这应该也可以工作。

Eclipse 是许多不同语言(如 C、C++、Java 等)的流行 IDE。我们已经看到它被用于在 Linux 系统上开发 TI Evalbot。[Springuin]正在 Windows 系统上使用基于 Java 的 IDE，这是我们第一次看到在 Windows 下使用 TI Launchpad 进行编程的开源替代方法。也就是说，真正与 Windows 相关的部分是与程序员交流的必要步骤。因为这个方法使用 MSP-GCC 和 msp430-gdbproxy，所以在 Linux 下也应该很容易做到。[如果你还没有安装这些工具，使用我们的教程](http://hackaday.com/2010/08/11/how-to-launchpad-programming-with-linux/)来安装它们，然后按照这个教程在 Eclipse 环境中进行安装和调试。