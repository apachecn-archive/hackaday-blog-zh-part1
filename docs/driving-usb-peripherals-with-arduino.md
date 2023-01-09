# 用 Arduino 驱动 USB 外设

> 原文：<https://hackaday.com/2009/10/22/driving-usb-peripherals-with-arduino/>

![arduino-driving-USB-keyboard](img/4ec1f984017d71f2a81312cc2e9ebc0c.png "arduino-driving-USB-keyboard")

Circuits@Home 已经设法用 Arduino 托管了一个 USB 键盘，并在字符 LCD 上显示键盘输入。这使用了我们在 8 月报道过的 [USB 主机屏蔽。该主机屏蔽包括一个 MAX3421，用于驱动字符 LCD。](http://hackaday.com/2009/08/21/arduino-usb-host-shield/)

键盘的控制代码非常简单。键盘被轮询条目。HID 输入然后被检查并转换成 ASCII 码以用于 LCD 屏幕。这可能成为嵌入式系统的优秀控制器或调试器。Arduino、shield 和 LCD 可以集成到键盘本身，并带有一个 I/O 端口，用于连接到您的项目。当按下 enter 键时，可以通过 I/O 端口输入和发送命令，并在屏幕上显示反馈。

本项目提供的示例代码展示了托管外设的框架。我们期待更多的项目和代码库利用这一新功能。