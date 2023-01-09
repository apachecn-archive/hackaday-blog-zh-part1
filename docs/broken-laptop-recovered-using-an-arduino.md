# 使用 Arduino 恢复损坏的笔记本电脑

> 原文：<https://hackaday.com/2011/01/04/broken-laptop-recovered-using-an-arduino/>

![](img/fee4e2e6ce35a8028f4ca439ea7d6566.png "arduino-laptop-rescue")

我们看到 Arduino 板在许多项目中使用，但我们从未想过将它用作 USB 交叉电缆。这基本上就是[恶魔杰克]让他坏掉的笔记本电脑运行起来的方法。当他的视频卡停止工作时，他发现自己无法访问笔记本电脑。较新的机器没有串行连接器，串行连接器本来可以用于串行终端，所以他有点不知所措，因为既没有安装 SSH，也没有安装 VNC。但是他认为他可能能够通过 USB 将 Arduino 用作串行终端连接器。他将 Arduino 插入笔记本电脑，并将台式电脑的 USB 串行转换器连接到 Arduino 的串行引脚。实际上，他只是利用 FTDI 芯片，将这些信号转换回 USB 的任何一端。一旦他启动了无头笔记本电脑，只需盲目地输入几个命令就可以让 SSH 运行，从而重新获得控制权。