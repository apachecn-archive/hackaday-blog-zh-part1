# 学习使用 V-USB (AVR USB 固件)库

> 原文：<https://hackaday.com/2012/02/09/learning-to-use-the-v-usb-avr-usb-firmware-library/>

V-USB 库是一段非常方便的代码，可以让您将 USB 连接添加到 ATtiny 微控制器(它以前被命名为 tinyUSB)。但是，如果您曾经考虑过将该库添加到您自己的项目中，您可能会被代码的复杂性所阻碍。有很多例子，但缺乏一个简明的初学者快速入门。[Joonas Pihlajamaa]一直在努力通过他的四部分 V-USB 教程系列来纠正这一不足。它不适合绝对的新手；你应该已经习惯使用 AVR 芯片，但这是我们能看到的唯一真正的先决条件。

他从硬件方面的考虑开始了这个系列。USB 提供 5V 电源轨，但数据线需要 3.3V 逻辑，因此必须考虑这一点。在试验板上建立测试平台后，他继续挑选代码，涵盖了各种用户定义的变量，您需要根据项目的需要来设置这些变量。我们将暂时搁置此事，希望[巨魔嗅探鼠](http://hackaday.com/2010/12/19/hackaday-unleashes-a-troll-sniffing-rat/)将会有所改观(尽管我们必须说最近评论变得更好了……保持下去！).

休息之后，我们嵌入了所有四个教程部分的链接。

*   [http://codeandlife . com/2012/01/22/AVR-at tiny-USB-tutorial-part-1/](http://codeandlife.com/2012/01/22/avr-attiny-usb-tutorial-part-1/)(初级读本)
*   [http://codeandlife . com/2012/01/25/AVR-at tiny-USB-tutorial-part-2/](http://codeandlife.com/2012/01/25/avr-attiny-usb-tutorial-part-2/)(硬件)
*   [http://codeandlife . com/2012/01/29/AVR-at tiny-USB-tutorial-part-3/](http://codeandlife.com/2012/01/29/avr-attiny-usb-tutorial-part-3/)(软件)
*   [http://codeandlife . com/2012/02/04/AVR-at tiny-USB-tutorial-part-4/](http://codeandlife.com/2012/02/04/avr-attiny-usb-tutorial-part-4/)(收尾)