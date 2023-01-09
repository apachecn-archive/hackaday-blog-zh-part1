# Arduino 程序员

> 原文：<https://hackaday.com/2010/01/22/arduino-programmer-for-arduino/>

[https://www.youtube.com/embed/M-sFQNIXde8?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/M-sFQNIXde8?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

哇，这个标题是 flamebait…但是给我们一个解释的机会。[George]为 Arduino 编写了一些代码，允许它对另一个 Arduino 进行编程。你可能会对自己说“这已经完成了”。在某种程度上，有了 [AVR ISP 编程盾](http://hackaday.com/2009/07/15/avr-isp-programming-via-arduino/)。但是一旦代码被上传到 Arduino，你就不需要电脑来为下一个芯片编程了。这个概念把一个 Arduino 变成了一个现场程序员。现在[他的代码](http://github.com/George1024/Arduino-Copier)只对 ATmega328 编程，虽然有点小问题，但这个概念是可靠的。一个功能齐全的独立程序员很容易想象；[George]已经奠定了基础，AVR ISP 编程固件已经证明这可以与几种不同的芯片一起工作，如果您的 AVR 有 ATmega328，应该有足够的空间来存储您计划闪存到目标微处理器的代码。这取决于你把所有的碎片放在一起。