# 通过键盘仿真来破解针织机

> 原文：<https://hackaday.com/2010/12/06/knitting-machine-hack-by-keypad-emulation/>

[Travis Goodspeed]和 Hackaday 的校友[Fabienne Serriere]联手为针织机开发了一种替代界面。他们在用兄弟 KH-930E 机器。我们看到【贝基·斯特恩】[使用同样的模型](http://hackaday.com/2010/11/08/make-a-knitting-machine-print-pixel-art/)，通过操纵设备的模拟软盘驱动器上的数据。[Travis]和[Fabienne]走的是不同的路线，他们正在使用 Arduino 和一组晶体管来模拟键盘。

他们首先使用连续性测试仪对键盘矩阵进行逆向工程。一旦他们设计出列和行的布局，他们就把每一个连接到一个 NPN 晶体管上。Arduino 草图模拟按下按钮来设置每一行的编织位数，只有一个用户输入的重置按钮。这可用于从 PC 发送数据，或作为一个独立的系统。无论哪种方式，这不仅是为配套机器添加功能的好方法，也是如何在任何设备上使用键盘的好例子。