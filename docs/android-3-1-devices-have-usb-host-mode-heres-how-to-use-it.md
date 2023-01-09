# Android 3.1 设备有 USB 主机模式。以下是使用方法。

> 原文：<https://hackaday.com/2012/02/22/android-3-1-devices-have-usb-host-mode-heres-how-to-use-it/>

随着 Android 3.1 的到来，你终于可以选择将设备用作 USB 主机。这可能是通过 USB OTG (On-the-Go)适配器，但尽管如此，这是一个直到现在都非常想念的功能。[Manuel]整理了一份关于使用 Android 作为 USB 主机的指南。如您所见，他的示例硬件是 Arduino 板，但这几乎适用于任何设备。

该教程为 Android 设备实现了一个测试应用程序，其中一个滑块将设置 Arduino 的板载 LED 的亮度。Arduino 草图没有什么特别的，它只是读取 UART 上接收到的数据。这意味着它不关心它是否连接到 Android、PC、OSX 或 Linux 系统，它继续它的业务，直到 RX 中断更新数据变量。

这样会大大简化很多我们见过的项目，比如[这个消息滚动皮带扣](http://hackaday.com/2011/11/01/led-sexting-belt-buckle/)。这需要额外的硬件来使 Arduino 成为主机，这一步现在是必要的。