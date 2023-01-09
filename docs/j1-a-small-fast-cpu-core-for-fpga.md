# J1:用于 FPGA 的小型快速 CPU 内核

> 原文：<https://hackaday.com/2010/12/01/j1-a-small-fast-cpu-core-for-fpga/>

Willow Garage 的[James Bowman]发表了一篇关于他的用于现场可编程门阵列的 [J1 CPU 内核的论文。这最初是为 PR2(你知道，](http://excamera.com/sphinx/fpga-j1.html)[那个昂贵得难以置信的啤酒递送系统)上的以太网摄像机开发和使用的？](http://hackaday.com/2010/07/13/rbd-robotic-beer-delivery/))机器人。它使用 16 位[冯诺依曼架构](http://en.wikipedia.org/wiki/Von_Neumann_architecture)，缺少几个你期望 CPU 拥有的处理器功能，比如中断、乘除、条件寄存器和进位标志。尽管如此，它的体积只有 200 行 Verilog 代码，可以以 80 MHz 的频率运行。[James]将 J1 与常用的三种不同的 FPGA CPU 内核进行了比较，并在他的 4 页论文中讨论了该系统是如何构建的，其中包含了您感兴趣的详细信息，但不会花一整天的时间来深入研究。