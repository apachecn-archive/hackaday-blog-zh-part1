# CUIduino、Arduino，支持真正的 USB

> 原文：<https://hackaday.com/2009/01/17/cuiduino-arduino-with-true-usb-support/>

![cuiduinotop](img/0764e14616e2f15412a020beaba7284f.png "cuiduinotop")

创建 USB 接口(CUI)是加州大学圣巴巴拉分校的一个项目，大约与 T2 的 Arduino T3 同时开发。它有一个 USB 端口，一个 PIC18F4550 和一个原型制作区。它被设计成能够通过许多 A/D 输入和通用 I/O 端口与真实世界轻松接口。它本身支持 OSC 和 USB 上的 MIDI。CUI 和 Arduino 最大的区别是它的 [USB 支持](http://www.mahalo.com/USB_3.0 "USB 3.0 - Mahalo")。Arduino 使用 FTDI 芯片来创建其板载 AVR 的串行接口。CUI 的 PIC 具有对 USB 的本地支持。这意味着你可以让 CUI 看起来像你想要的任何 USB HID 设备:[键盘](http://www.mahalo.com/Keyboards "Keyboards - Mahalo")、[鼠标](http://www.mahalo.com/Computer_Mouse "Computer Mouse - Mahalo")、游戏控制器等等。

Arduino 有一个友好的开发环境和大量的追随者。CUI create [Dan Overholt]决定在他的电路板上增加一个 ATmega168，以获得两个世界的最佳效果。它可以像任何其他 Arduino 兼容设备一样进行编程，但拥有 CUI 父级意味着您的 Arduino 项目可以像本机 USB HID 小工具一样工作。

[谢谢彼得]