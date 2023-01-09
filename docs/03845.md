# 枫树打败了阿杜伊诺，拿走了它的盾牌

> 原文：<https://hackaday.com/2009/08/22/maple-beats-up-arduino-takes-its-shields/>

![maple](img/b70586f5ab82308bf0435f192ae542c8.png "maple")

每个 Arduino 的核心 Atmega168 是一个非常强大的芯片；它的同类被视为作为一个基本的网络服务器工作，回放 T2 的数字音频，甚至产生 T4 的电视信号。但是随着项目越来越复杂，现实露出了它丑陋的一面:Arduino 可以很好地处理这些任务中的任何一个*,但是它经常需要压缩设备中的每一个指令周期或每一位内存。即使是 368 芯片和 Arduino Mega 也只是权宜之计。迟早，你必须升级到长裤——升级到更强大的微控制器平台——这是一个令人不安的变化，通常涉及新硬件的巨额投资和令人生畏的学习曲线。Leaf Labs 的 [Maple](http://blogs.leaflabs.com/?p=91) 旨在改变这一切……
 Maple 预计将于 10 月份上市，售价约为 40 美元，它集成了 [STM32 微控制器](http://www.st.com/stm32)，这是一款 32 位 72MHz 的芯片，具有熟悉的 Arduino 尺寸，甚至兼容库函数。用户可以直接进入，保留他们在 Arduino shields 和专有技术上的现有投资，然后通过这种更强大的处理器提供的新功能来扩展他们的技能。*

但枫叶不是第一个。Coridium Corporation 的 30 美元的 ARMite PRO(下图)是一个 60MHz 的 ARM7 板，与 Arduino Pro 的引脚和尺寸兼容。CPU 不像 STM32 那么强大，也不提供 Arduino 兼容库，但它仍然是 Atmega 的一个重大进步，今天*已经可以使用了。*

![armitepro](img/03443a5be8db61ce8cdcd3950b1416fe.png "armitepro")

同样值得一提的是 Raisonance 的 [STM32 Primer](http://www.stm32circle.com/resources/stm32primer.php) (也称为 STM32 Circle)，尽管它位于一个完全不同的方向，如下所示。这个套件与 Arduino 既不是硬件兼容，也不是软件兼容，捆绑的软件工具只适用于 Windows，但它同样负担得起(约 40 美元)，独立(没有外部程序员)，并将让你立即开始使用 STM32 芯片*。*虽然你不能带你的 Arduino shields 来参加这个派对，但 Primer 自带乐趣:彩色 LCD、3D 加速度计和可充电电池。最初的“Circle”初级读本有点难以找到，但是谷歌搜索一下会有所帮助。如果你不介意再付一半的钱，一个有更多功能的“Primer 2”已经发布了。

![stm32primer](img/366ea11d8522357ec2d498e63346cc3a.png "stm32primer")

Maple 只是 Leaf Labs 计划中几个日益强大的项目中的第一个。FPGAs 和千兆赫速度的 CPU 正在开发中。