# 在 FPGA 上克隆的 NES 处理器

> 原文：<https://hackaday.com/2009/10/17/nes-processor-cloned-on-a-fpga/>

![nes-on-an-fpga](img/dd321bfa47fac6603231e69e2eaa2380.png "nes-on-an-fpga")

[布拉德利]决定应对挑战，在现场可编程门阵列中重建最初的任天堂娱乐系统处理器。说什么？最初的 NES 是一个[遗留系统](http://en.wikipedia.org/wiki/Legacy_system)，仍在使用但不再生产。如果一个系统坏了，它变得越来越难以修复或找到替代零件久而久之。通过使用一个[可编程集成电路，如 CPLD](http://hackaday.com/2008/12/11/how-to-programmable-logic-devices-cpld/) 或 FPGA 来克隆原始硬件的功能，遗留系统可以在原始硬件停止运行后长期存在。

布拉德利花了大约一年的时间来完全实现 NES 处理器，这是他在布拉德利大学的硕士项目的一部分。他使用了关于处理器的知识，并在此过程中结合了一些逻辑探针的探测工作。编程是用 [VHDL](http://en.wikipedia.org/wiki/VHDL) 完成的，这些文件可以下载([点击文档](http://cegt201.bradley.edu/projgrad/proj2006/fpganes/))。

随着 [NES 仿真器在人类已知的每个设备](http://hackaday.com/2009/09/03/nes-on-zipit/)上的普遍存在，你可能不会复制这一点，除非你想要一个玩 FPGA 的理由。我们感兴趣的是这种类型的工作提供的硬件解决方案，为过时的硬件仍然服务于一个有用的目的。如果你使用 FPGA 或类似设备来保持旧系统运行，请在评论中告诉我们。