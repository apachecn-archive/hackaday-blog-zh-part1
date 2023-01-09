# 器件:LTC2631A I2C 数模转换器

> 原文：<https://hackaday.com/2009/02/09/parts-ltc2631a-i2c-digital-to-analog-converter/>

![ltc2640](img/0759c059e83618305e21849fe8d3f419.png "ltc2640")

线性科技的 [LTC2631A-LZ8](http://www.linear.com/pc/productDetail.jsp?navId=H0,C1,C1155,C1005,C1156,P85698) 是一个 8 位[数模转换器](http://en.wikipedia.org/wiki/Digital-to-analog_converter) (DAC)，带有 [I2C](http://en.wikipedia.org/wiki/I%C2%B2C) 接口。这个 DAC 可以输出 255 个不同的电压，电压间隔均匀，在 0 到 2.5 伏之间。我们之前演示了带有三线 [SPI](http://en.wikipedia.org/wiki/Serial_Peripheral_Interface_Bus) 接口的 [LTC2640](http://hackaday.com/2009/01/22/how-to-bus-pirate-v1-improved-universal-serial-interface/) ，但这个版本仅由两根信号线控制。

| **公交车海盗** | **LTC2631A (pin #)** |
| 数据 | 民主行动党(3) |
| 时钟 | SCL (2) |
| 物理输出核心 | VOUT (7) |
| — | CA0/地址 0 (1) |
| +5 伏 | CA1/地址 1 (8) |
| +5 伏 | VDD (5) |
| GND | GND (4) |
| — | 参考文献(6) |

我们使用了 [Bus Pirate 通用串行接口工具](http://hackaday.com/the-bus-pirate-universal-serial-interface/)来处理 DAC，但是相同的基本原理适用于任何定制实现。表中列出了 Bus pirate 和 LTC2631A 之间的连接。我们从总线盗版的 5 伏电源为芯片供电，但它在 3.3 伏也能正常工作

I2C 总线在两条总线上都需要[上拉电阻](http://en.wikipedia.org/wiki/Pull-up_resistor)。通过将 5v 电源与上拉电阻输入端相连，可将 5v 电压提供给上拉电阻。闭合时钟和数据线上的跳线，为上拉电阻提供外部电压。

现在，为 I2C 模式设置总线盗版并激活板载电源。

> HiZ > m**<–选择模式**
> 1。HiZ
> 2。单线
> 3。UART
> 4。I2C
> …
> 9。PC AT 键盘
> 模式>4**<–I2C 模式**
> 900 模式设置
> 202 I2C 就绪
> I2C>p**<–设置电源**
> W/w 切换 3.3 伏电源？
> 1。否
> 2。是
> 模式>1**–不使用 3.3 伏**W/W 切换 5 伏电源？
> 1。没有
> 2。是
> 模式>2**<–使用 5V 电源**
> 9xx 电源配置，使用 W/w 切换
> 9xx 电压监控器:5V:0.0 | 3.3V:0.0 | VPULLUP:0.0 |
> I2C>W**<–大写“W”激活电源**
> 9xx 电源
> I2C > v **<**

配置总线盗版后，电压监视器显示 5v 电源激活(4.9v)。此外，监视器显示 5v 连接到上拉电阻电源端子(VPULLUP)。

> I2C >(0)**<–列出可用的宏**
> 0。宏菜单
> 1.7 位地址搜索
> I2C>(1)**<–搜索 I2C 器件**
> xxx 搜索 7 位 I2C 地址空间。
> 在:
> 0x40 0xE6 **<找到设备–从这些地址**
> I2C >得到回复

根据数据手册第 22 页的表格，引脚 1 和 8 的状态决定 LTC2631A 的 I2C 地址。我们没有在数据表中查找地址，而是使用了 Bus Pirate 的 I2C 地址搜索宏来扫描整个 I2C 地址范围。DAC 响应设置地址(0X40)和全局地址(0xE6)。全局地址对于通过同一 I2C 总线同时控制多个 DAC 非常有用。

> I2C > d[0x40 0b 00110000 0x ff 0]d
> 9xx 电压探针:0.0 伏**<–输出** **为 0 伏**
> 210 I2C 起始条件**<–起始事务**
> 220 I2C 写:0x 40 得到 ACK:是**<–DAC 地址**
> 220 I2C 写:0x30 得到 ACK:是**<–是**
> 220 I2C 写:0x00 得到 ACK:是**<–不关心，多余字节**
> 240 I2C 停止条件**<–结束事务**
> 9xx 电压探针:2.5 伏**<–满输出**
> I2C >

现在，我们准备好与 DAC 接口了。初始电压测量值(d)显示 DAC 当前输出 0 伏。

I2C 启动条件([)提醒连接的 I2C 设备监听它们的地址。第一个字节是地址(0x40)，用于标识我们想要访问的设备。下一个字节是 LTC2631A 命令，用于更新 DAC 输出(0x30 或 0b00110000)，其后是输出设置(0xff 或 255，100%输出)。最后一个字节对于我们使用的 8 位 DAC 无关紧要，但对于更高分辨率版本的 DAC，它携带额外的数据位。通过发送 I2C 停止条件(])来完成交易。

将 DAC 更新至 100%后，电压测量值(d)显示输出为 2.5 伏。

> I2C > d[0x40 0x30 0]d
> 9xx 电压探针:2.5 伏**<–DAC 处于 100%**
> 210 I2C 起始条件
> 220 I2C 写:0x 40 得到 ACK:是
> 220 I2C 写:0x 30 得到 ACK:是
> 220 I2C 写:0x00 得到 ACK:是**<–将 DAC 设置为 0**
> 220 I2C 写:0x00 得到 ACK:0

类似的命令序列会将 DAC 输出置回 0。电压测量确认 DAC 输出现在为 0 伏。

有关 DAC 特性和命令代码的完整列表，请参见 [Bus Pirate version 1 how-to](http://hackaday.com/2009/01/22/how-to-bus-pirate-v1-improved-universal-serial-interface) 结尾处对 LTC2640 SPI DAC 的深入讨论。

在未来的[部分](http://hackaday.com/category/parts/)帖子中，有你想要我们连接的芯片吗？