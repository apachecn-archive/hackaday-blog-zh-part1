# 器件:1K 单线 EEPROM (DS2431)

> 原文：<https://hackaday.com/2008/12/24/parts-1k-1-wire-eeprom-ds2431/>

![1keeprom-450](img/b017cccc9744f76e135310a0d2cb6bf0.png "1keeprom-450")

Maxim [DS2431 1K EEPROM](http://www.maxim-ic.com/quick_view2.cfm/qv_pk/4272) 是[单线](http://en.wikipedia.org/wiki/1-Wire)设备，使用单个微控制器引脚为项目增加存储。我们之前连接了一个[单线温度计](http://hackaday.com/2008/12/10/parts-1-wire-temperature-sensor-ds1822/)，但这个 EEPROM 略有不同，因为它直接从单线总线上获取电能。拿起[数据表](http://www.maxim-ic.com/getds.cfm/qv_pk/4272) (PDF)，跟着我们一起读写这个简单的单线存储器。

**[DS2431](http://www.maxim-ic.com/quick_view2.cfm/qv_pk/4272) 1 线 1K EEPROM(Digikey #[ds 2431+-ND](http://www.digikey.com/scripts/DkSearch/dksus.dll?Detail&name=DS2431%2B-ND)，1.67 美元)**

我们使用我们的[总线盗版通用串行接口](http://hackaday.com/2008/11/19/how-to-the-bus-pirate-universal-serial-interface/)来演示 DS2431 EEPROM，我们在[之前的单线文章](http://hackaday.com/2008/12/10/parts-1-wire-temperature-sensor-ds1822/)中介绍了正确的连接和配置选项。DS2431 只需要两个连接:接地(引脚 1)和单线/电源(引脚 2)。引脚 3 保持未连接。像上次一样，我们在 1 线总线上使用一个 2K 上拉电阻。

首先，我们使用总线盗版的搜索 ROM 命令来识别相连的单线器件。

> 1-WIRE >(240)**<–SEARCH ROM 命令宏**
> 1-WIRE ROM 命令:SEARCH (0xF0)
> 发现器件在:
> 宏 1-WIRE 地址
> 1.0 x2d 0x 54 0x D2 0x ef 0x 00 0x 00**–地址**
> * ds 2431 1K EEPROM**<–类型**
> 2.0 x2d 0x Fe 0x 8d 0x 43 0x 01 0x 00
> 宏可以使用前 10 个设备 id，参见(0)。
> 单线>

搜索 ROM 命令显示有 3 个 EEPROMs 连接到 1 线总线。总线盗版者将 64 位单线地址存储在宏中，因此我们不必每次都键入它。我们将使用由 macro (1)标识的第一个设备。

写入 DS2431 需要三个步骤:

*   将数据写入 DS2431 的 8 字节“暂存”EEPROM 缓冲器
*   验证暂存区内容并获取写访问密钥
*   将数据从暂存区复制到 EEPROM，以便永久存储。

命令 0x0f 写入暂存区。暂存区是一个 8 字节的缓冲区，在将数据永久保存到 EEPROM 之前，先保存数据。

> 单线>(85)(1)0x0f 0x 00 0x 00 0 1 2 3 4 5 6 7**<–命令**
> 1 线总线复位正常
> 1 线写入 ROM 命令:匹配(0x55) *跟随 64 位地址【T11 线地址宏 1:0x2D 0x 54 0x D2 0x ef 0x 00 0x 00 0x 00 0x2B
> 1 线写入:0x0F**<–写入暂存区**
> 1 线写入:0x 00**<–开始地址字节 1**
> 1 线写入:0x 00**<–开始地址字节 2**
> 1 线写入:0x 00**<–数据**

 **MATCH ROM 宏(85)隔离第一个器件(1)。0x0f 是写入暂存区的命令，后跟起始地址 0 0。最后，我们发送八个字节的数据保存在暂存区中。暂存区的长度为 8 个字节，所有 8 个字节将从暂存区一次复制到 EEPROM。

> 单线>(85)(1)0x aa r:3 r:8 r:2 r:2**<–命令**
> 单线总线复位正常
> 单线写 ROM 命令:匹配(0x 55)*跟随 64 位地址
> 单线地址宏 1:0x2D 0x 54 0x D2 0x ef 0x 00 0x 00 0x 00 0x 2b
> 单线写:0x aa**<–读取暂存区**
> 单线批量读取，0x03 字节:【T9 0x08 字节:**<–验证我们的数据**
> 0x 00 0x 01 0x02 0x 03 0x 04 0x 05 0x 06 0x 07
> 1 线批量读取，0x02 字节:**<–反向 CRC**
> 0x 44 0x 67
> 1 线批量读取，0x 02 字节:**<–从此处全为 1**
> 0x ff 0x ff
> 1 线>

要将数据从暂存区复制到 EEPROM，我们必须首先使用命令 0xaa 从暂存区获取一个三字节访问码。前三个字节是访问码(0x00 0x00 0x07)，其后是暂存区中包含的数据。

> 单线>(85)(1)0x 55 0x 00 0x 07
> 单线总线复位正常
> 单线写 ROM 命令:匹配(0x 55)*跟随 64 位地址
> 单线地址宏 1:0x2D 0x 54 0x D2 0x ef 0x 00 0x 00 0x 2b
> 单线写:0x 55**<–复制到 EEPROM 命令**
> 单线写:0x 00**<–访问码(3 字节)**
> ！！！**<–读取位**
> 1 线读取位:0
> 1 线读取位:1**<–位交替，完成**
> 1 线读取位:0
> 1 线读取位:1
> 1 线>

带有正确访问码的命令 0x55 会将暂存区复制到数据 EEPROM。位读取(！！！！)当复制完成时，在 0 和 1 之间交替。

> 单线>(85)(1) 0xf0 0x00 0x00 r:8 r:8
> 单线总线复位正常
> 单线写 ROM 命令:匹配(0x 55)*跟随 64 位地址
> 单线地址宏 1:0x2D 0x 54 0x D2 0x ef 0x 00 0x 00 0x 2b
> 单线写:0xf 0**<–读存储器**
> 单线写:0x 00**<–起始地址(2 字节)**
> 0x08 字节:**<–回读数据**–0x 00 0x 01 0x 02 0x 03 0x 04 0x 05 0x 06 0x 07
> 1 线批量读取，0x08 字节:**<–读取超出我们的数据**–0x 00 0x 00 0x 00 0x 00 0x 00
> 1 线>

命令 0xf0 后跟一个双字节存储器地址(0x00 0x00)开始数据读取过程。前八个字节(r:8)是我们之前写的值。读取不涉及暂存区，也没有 8 字节的限制，所以进一步的读取会继续到内存的末尾。

不要忘记补上你可能错过的任何[部分帖子](http://hackaday.com/category/parts/)。**