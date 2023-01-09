# 对 Playstation 移动进行逆向工程

> 原文：<https://hackaday.com/2011/03/13/reverse-engineering-the-playstation-move/>

![playstation_move](img/9957f2d37d3ba2ca81622003e001e813.png "playstation_move")

[Kenn]正在为一个大学项目从头开始建造一架四轴飞行器。目前，他的主要焦点是建立一个惯性测量单元，或者更确切地说是将 PS3 Move 控制器作为他的直升机的 IMU。他之前考虑过使用 Wiimote Motion Plus，但 Move 有一个三轴磁力计，而 Wii 控制器没有。

这部分项目的最终目标是构建定制固件，在 Move 的 STM32-Cortex 微控制器上运行，使他能够从控制器的每个传感器中获取数据。在他的研究过程中，他彻底记录了他网站上的每个传感器，并从 Cortex 芯片中转储了完整的工作固件映像。最近，他甚至能够在控制器上运行任意代码，这是一个巨大的进步。

[Kenn 的]项目进展得非常顺利，并且随着他继续深入挖掘 Move 的内部工作机制，无疑将成为其他人的巨大资源。如果你正在寻找信息，或者你有什么可以贡献的，一定要去他的网站看看。