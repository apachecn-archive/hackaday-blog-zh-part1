# 总线盗版固件更新 V0g

> 原文：<https://hackaday.com/2009/06/25/bus-pirate-firmware-update-v0g/>

![buspiratefirmwarev0g](img/3a3690205eca73b532d41e05cfef4e72.png "buspiratefirmwarev0g")

所有[总线盗版](http://www.buspirate.com)版本的固件 v0g 现已发布。此版本中的更新包括引导加载程序、频率发生器/脉宽调制器、SPI 总线嗅探器、MIDI 库、配置报告、改进的用户界面和错误修复。v0g 也是第一个完全支持 v2 硬件分支的固件。

我们真的为这个版本感到骄傲，因为它给 Bus Pirate 的内部操作带来了一个更加一致的结构。它为未来的 CAN、LIN 和库奠定了基础，并支持本地化和翻译。固件中包含安装和升级说明。报告项目中的错误[问题跟踪器](http://code.google.com/p/the-bus-pirate/issues/list)。

休息之后，我们将记录新功能。

**引导程序**

固件 v0g 包括一个[引导程序](http://code.google.com/p/the-bus-pirate/source/browse/#svn/trunk/bootloader)。安装引导程序后，固件更新可以通过串行或 USB 连接完成，而不是使用合适的 ICSP 编程器。[安装和更新说明](http://code.google.com/p/the-bus-pirate/source/browse/v0g/firmware/v0g/README.TXT)包含在固件档案中。

**频率发生器/脉宽调制器
T2**

> 单线> g**<–频率发生器/PWM 设置命令**
> 1 KHz-4000 KHz 频率发生器/PWM (beta)
> 频率单位 KHz(50)>50**<–输入频率单位 KHz**
> 预分频器:8**<–计算的预分频器**
> PR2:39**<–计算的 PR2 值**
> 占空比单位为% (50) >50**<–输入占空比百分比**
> PWM 有效
> 单线>f**<–频率测量命令**
> PWM 有效:禁用 PWM**<–PWM 有效时不可用**
> 单线>g**<–g 再次禁用 PWM**
> PWM 禁用
> 单线>

使用菜单选项“g”可在辅助引脚上获得 1Hz-4MHz [频率发生器](http://code.google.com/p/the-bus-pirate/source/browse/trunk/source/AUXpin.c#34)/脉宽调制器功能。这个特性还在开发中，但是 v0g 已经有了基本的功能。频率发生器和频率测量功能不能同时使用。我们还解决了硬件 v1+的[频率测量](http://code.google.com/p/the-bus-pirate/source/browse/trunk/source/AUXpin.c#113)代码中的一个小错误。

**SPI 总线嗅探器**

> SPI >(1)**<–嗅探宏**
> 嗅探时间:
> 1。CS 低
> 2。CS 高电平
> 3。所有流量
> (1)>3**<–当嗅探总线**
> SPI 总线嗅探器时，按任意键退出
> 0x 10(0x 00)0xc 6(0x 00)**<–显示数据为 MOSI(MISO)**
> SPI >

PIC24F 的 SPI 从机模式使得添加一个 [SPI 总线嗅探器](http://code.google.com/p/the-bus-pirate/source/browse/trunk/source/SPI.c#167)变得很容易。它在慢速或间歇数据传输时工作良好，但它需要额外的输出缓冲以在高速时获得更好的性能。为了获得最佳性能，请将总线盗版显示模式更改为“原始输出”。

**MIDI 库**

MIDI 是一种流行的乐器接口，它只是一个 33.2K 波特/8/N/1 UART。 [MIDI](http://code.google.com/p/the-bus-pirate/source/browse/trunk/source/midi.c) 库具有与异步串行端口库相同的功能，其设置固定用于 MIDI 通信。MIDI 设备需要一个隔离收发器，我们[正在研发一个](http://code.google.com/p/the-bus-pirate/source/browse/#svn/trunk/hardware/adapters/MIDI)，但是需要一个 [MIDI 连接器的尺寸和零件号](http://code.google.com/p/the-bus-pirate/issues/detail?id=21)。

**公交海盗状态报告**

> raw 3 wire > I**<–状态报告命令**
> Hack a Day Bus Pirate v2g 0
> [http://www.buspirate.com](http://www.buspirate.com)
> 固件 v0g
> *————*
> 电源 ON
> 电压监控器:5V:5.0 | 3.3V:3.3 | VPULLUP:5.0 |
> AUX:默认设置(AUX 引脚)
> 高 Z 输出(H =输入，L=GND)
> 上拉电阻 OFF 【T

新的[终端内状态报告](http://code.google.com/p/the-bus-pirate/source/browse/trunk/source/procMenu.c#120)列出了活动协议库中可用的功能和当前设置。

**默认用户提示**

> HiZ>m
> 1。HiZ
> 2。单线
> 3。UART
> 4。I2C
> 5。SPI
> 6。JTAG
> 7。拉线 2 线
> 8。RAW3WIRE
> 9。PC 键盘
> 10。MIDI
> (1)>**<–按回车键进入默认选项(1/HiZ)**
> 模式设置
> HiZ >

[用户提示](http://code.google.com/p/the-bus-pirate/source/browse/trunk/source/baseIO.c#20)已经更新为接受多位数的值。没有任何输入的 Enter 选择提示前括号中显示的默认值。所有用户输入现在都由这个单一的用户提示函数来处理。

**用户值输入格式**

> SPI > r:0x02**<–以十六进制格式重复**
> 批量读取 0x 02 字节:
> 0x 00 0x 00
> SPI>(0b 0)**<–二进制格式的宏命令**
> 0。宏菜单
> 1。SPI 总线嗅探器
> SPI >

所有用户提示现在都支持二进制、十六进制或十进制的输入值。以前，菜单和宏提示仅支持十进制格式的输入。

**本地化，翻译**

程序中使用的大量文本已经被转移到一个[翻译文件](http://code.google.com/p/the-bus-pirate/source/browse/#svn/trunk/source/translations)，该文件在 [base.h](http://code.google.com/p/the-bus-pirate/source/browse/trunk/source/base.h#54) 中定义。

如果你做了翻译，请分享给我们。我们将在 SVN 进行翻译，并为任何感兴趣的人编译本地化的固件。

**测试 v0h beta**

如果你喜欢生活在边缘，试试 [v0h 夜生活](http://code.google.com/p/the-bus-pirate/source/browse/#svn/trunk/firmware)。这些功能已经在 v0h nightlies 中实现:

*   [I2C 嗅探器](http://code.google.com/p/the-bus-pirate/source/browse/trunk/source/I2C.c#139)，
*   HD44780 字符液晶[测试库](http://code.google.com/p/the-bus-pirate/source/browse/trunk/source/HD44780.c)。
*   [键盘库 I/O 超时](http://code.google.com/p/the-bus-pirate/source/browse/trunk/source/pc_at_keyboard.c#316)。
*   改进的[语法解析器](http://code.google.com/p/the-bus-pirate/source/browse/trunk/source/procSyntax.c#44)。
*   软件[复位命令](http://code.google.com/p/the-bus-pirate/source/browse/trunk/source/procMenu.c#93)。

检查[问题跟踪器](http://code.google.com/p/the-bus-pirate/issues/list)的未来功能，或提出功能请求。