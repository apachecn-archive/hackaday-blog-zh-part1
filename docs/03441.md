# 零件:ShiftBrite RGB LED 模块(A6281)

> 原文：<https://hackaday.com/2009/06/29/parts-shiftbrite-rgb-led-module-a6281/>

![shiftbriteii](img/209ba8f79c6eda216b0cb8842e815262.png "shiftbriteii")

[Macetech 的](http://www.macetech.com/blog/) [ShiftBrite](http://macetech.com/blog/node/54) 是一个大功率 RGB LED 加上一个[快板 A6281](http://www.allegromicro.com/en/Products/Part_Numbers/6281/) 背包。A6281 使用三个 10 位[脉宽调制器](http://en.wikipedia.org/wiki/Pulse-width_modulation)，利用 RGB LED 中的红色、绿色和蓝色元素混合数百万种颜色。对于更大的项目，可以将多个模块链接在一起，如 [ShiftBrite table](http://www.youtube.com/watch?v=C7aUaMiqoIE) 。

下面我们演示一个使用总线盗版的 ShiftBrite 模块。在有限的时间内，你可以[得到你自己的巴士海盗](http://hackaday.com/2009/06/25/bus-pirate-preorders-open/)，完全组装好并运往世界各地，只需 30 美元。

![shiftbrite-over](img/daa3a7ae6b7c1845fea05ba59cb07ec1.png "shiftbrite-over")

**[ShiftBrite](http://macetech.com/blog/node/54) RGB LED 模块( [Macetech](http://macetech.com/store/index.php?main_page=product_info&cPath=1&products_id=1) ，4.99 美元)。ShiftBrite [数据表及示例代码](http://docs.macetech.com/doku.php/shiftbrite)，快板[a 6281](http://www.allegromicro.com/en/Products/Part_Numbers/6281/)数据表 (PDF)。**

ShiftBrite 模块是一个完整的 A6281 开发板。它不需要任何额外的部件，只需要一个 5-9 伏的电源。

A6281 是最完整的 RGB LED 驱动器 IC 之一，但它仅采用小型 QFN 封装。ShiftBrite 是尝试 A6281 而不焊接小芯片的好方法。

![A6281-connect.470](img/fa2cfbc5c5ef6576c26eb3d44531a044.png "A6281-connect.470")

一堆 A6281 模块可以链接在一起。每个模块在单独的输出引脚上重复所有串行输入信号，因此 A6281 可以在长电缆线路上工作。

| **公交车海盗** | **ShiftBrite** |
| MOSI | 国防情报部 |
| CLK | 海峡群岛 |
| 特许测量员 | 里 |
| 去吧 | 不，不 |
| 5 伏 | V+ |
| Vpullup | V+ |
| GND | GND |

我们使用我们的[总线盗版通用串行接口](http://www.buspirate.com)来演示 ShiftBrite，但是命令序列对于任何微控制器都是相同的。如上表所示，我们将 Bus Pirate 连接到 ShiftBrite。

我们将总线 Pirate 设置为 raw3wire 模式(M，8 ),并选择开漏输出(Hi-Z ),这样我们就可以在 5v 下连接 ShiftBrite。总线盗版不能直接输出 5 伏，所以我们启用总线上拉电阻(v2 中的菜单“p ”),并将上拉电阻电压输入引脚连接到 5 伏电源。最后，我们启用了板载电源(大写“W”)。

*接口*

LED 驱动器输出仅在使能引脚(EI)保持低电平时有效。

> raw 3 wire > A**<–大写“A”，EI 引脚高电平，输出禁用**
> AUX 高电平
> raw 3 wire>A**–小“A”，EI 引脚低电平，输出有效**
> AUX 低电平
> RAW3WIRE >

我们使用了 Bus Pirate 的辅助引脚来切换 A6281 的使能引脚，但您也可以通过将 EI 直接接地来绕过此功能。总线盗版终端中的小“a”将 AUX/EI 引脚连接拉低，使能 LED 输出。

![A6281-IO.470](img/495cc365c68499eb608c003ae2ef5be8.png "A6281-IO.470")

两个命令更新 A6281 设置。配置命令控制点校正和时钟设置。LED 脉宽调制器(PWM)命令更新设置红色、绿色和蓝色通道亮度的三个 10 位值。两个命令都是 32 位(4 字节)长，位 30 选择配置或脉宽调制器命令。请参考上图或第 7 页的数据表。

接口协议类似于 [SPI](http://en.wikipedia.org/wiki/Serial_Peripheral_Interface_Bus) ，但未使用主输入从输出引脚。数据首先从最高有效位发送，从第 31 位开始。通过将 32 位时钟输入芯片，然后切换 latch 引脚来发送命令。

在开始混色之前，我们需要设置 A628a 的内部时钟并写入点校正值。

> raw 3 wire > 0b 01000111 0b 11110001 0b 11111100 0b 01111111][
> 写:0x 47**<–写 32 位数据**写:0xF1
> 写:0xFC
> 写:0x7F
> CS 禁用**<–latch 引脚高电平**
> CS 使能**<–latch 引脚低电平**

我们用二进制写了这些值，所以很容易理解上表中的内容。请记住，首先发送的是第 31 位，因此这里显示的位的顺序与表中显示的相反。

完整的设置命令长 32 位(4 字节)。位 30 将其设置为配置命令(1)。位 7 和 8 配置时钟源，值 00 配置 800KHz 内部振荡器(数据手册第 7 页)。如果您想要校正大型阵列中不稳定的像素，三个 7 位“点校正”值可以微调 LED 颜色通道(参见上表中的寄存器位置)。我们将所有的点校正值设置为满(1111111)。几个位触发测试功能或没有目的，这些应该输入为 0。

输入 32 位后，切换 A6281 锁存引脚(][)，将数据锁定到寄存器中。既然芯片已经配置好，输出也已启用，我们终于可以开始玩 led 了。

> raw 3 wire > 0b 001111111111111 0b 11111111111 0b 11111111[
> 写:0x3F
> 写:0xFF
> 写:0xFF
> 写:0xFF
> CS 禁用
> CS 使能
> RAW3WIRE >

首先，把所有的颜色调全。位 31 (0)被忽略，位 30 (0)表示 LED 脉宽调制器更新命令，其余位将所有三个通道设置为 100%。三个 PWM 值控制每种颜色的输出强度如下:蓝色(位 29:20)、红色(位 19:10)和绿色(位 9:0)。升高和降低锁销(][)以结束命令。

接下来，分别测试每种颜色。

> raw 3 wire > 0b 00111111110000 0b 000000000 0b 00000000[
> 写:0x3F
> 写:0xF0
> 写:0x00
> 写:0x00
> CS 禁用
> CS 使能
> RAW3WIRE >

位 30 (0)发出一个 LED PWM 更新命令，随后是蓝色通道的 100%设置(111111111)以及红色和绿色通道的 0%设置。当我们切换 latch 引脚(][)时，新值被保存，LED 颜色变为蓝色。

> raw 3 wire > 0b 0000000000 0b 00001111 0b 11111100 0b 00000000[
> 写:0x00
> 写:0x0F
> 写:0xFC
> 写:0x00
> CS 禁用
> CS 使能
> RAW3WIRE >

这次我们将 LED 设置为 100%红色。位 30 (0)发出 LED PWM 更新命令，随后蓝色通道设置为 0%，红色通道设置为 100%(111111111)，绿色通道设置为 0%。当我们切换插销(][)时，LED 颜色变为红色。

> raw 3 wire > 0b 000000000 0b 0000000000 0b 00000011 0b 1111111][
> 写:0x00
> 写:0x00
> 写:0x03
> 写:0xFF
> CS 禁用
> CS 使能
> RAW3WIRE >

最后，我们将 LED 设置为 100%绿色。位 30 表示 LED PWM 更新，随后蓝色和红色通道为 0%设置，绿色通道为 100%设置(111111111)。切换插销(][)，LED 颜色变为绿色。

喜欢这个帖子？查看你可能错过的[部分帖子](http://hackaday.com/category/parts/)。想申请一个职位吗？请在评论中留下你的建议。

**黑客日回顾披露** : Macetech 在 2008 年的 Maker Faire 上给了我们几个免费的 [ShiftBrites。](http://hackaday.com/2008/05/08/maker-faire-2008-shiftbright-rgb-led-module/)