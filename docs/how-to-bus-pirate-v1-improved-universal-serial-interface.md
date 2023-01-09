# 如何:总线盗版 V1，改进的通用串行接口

> 原文：<https://hackaday.com/2009/01/22/how-to-bus-pirate-v1-improved-universal-serial-interface/>

![front450a](img/69f698f388c40c6278fa3d51769b7078.png "front450a")

我们使用总线盗版来连接新的芯片，而无需编写代码或设计 PCB。根据您的反馈，以及我们使用[原始总线盗版](http://hackaday.com/2008/11/19/how-to-the-bus-pirate-universal-serial-interface/)演示各种[部件](http://hackaday.com/category/parts/)的经验，我们用新功能和更便宜的组件更新了设计。

还有一个固件更新，用于两个总线盗版硬件版本，修复了错误，以及一个 PC AT 键盘解码器。查看新的 [Hack a Day Bus Pirate 页面](http://hackaday.com/the-bus-pirate-universal-serial-interface/)，并在我们的 [Google code SVN 库](http://code.google.com/p/the-bus-pirate/source/browse/)中浏览 Bus Pirate 源代码。

下面我们将介绍设计更新和数模转换器接口。

**概念概述**

**![overview-diagram1](img/814db4c942af9d257579f6e9cb29b20d.png "overview-diagram1")
**

总线盗版开始时是我们用来测试新芯片的代码片段的集合，没有无休止的编译程序运行开发周期。我们在 how-to 中发布了它，并在我们的[部分帖子](http://hackaday.com/category/parts/)中使用它来演示一系列串行接口 IC。本文介绍了一个具有新特性和大量改进的更新设计。

*   表面贴装设计
*   具有外部电压源的所有总线上的上拉电阻
*   软件可复位的 3.3 伏和 5 伏电源
*   所有电源的电压监控
*   外部电压测量探头
*   更便宜的零件

![top](img/9d9f2162dc720ef97318d47d970b5739.png "top")

**硬件**

**![cct-450](img/e8f357f95785efafd91f9438b6a92cf4.png "cct-450")**

[点击查看全尺寸示意图](http://hackaday.com/files/2009/01/cct1.png) (PNG)。电路和 PCB 使用免费版的 [Cadsoft Eagle](http://www.cadsoft.de/) 设计。这个项目的所有文件都包含在本文末尾链接的项目档案中。

*微控制器*

我们在这个项目中使用了一个微芯片[pic 24 FJ 64 ga 002](http://www.microchip.com/wwwproducts/Devices.aspx?dDocName=en026374)28 引脚 SOIC 微控制器(IC1)。电源引脚有 0.1uF 旁路电容接地(C1，2)。2.5v 内部调节器需要一个 10uF 钽电容(C20)。该芯片通过一个五针接头(ICSP)进行编程。引脚 1 的 MCLR 功能需要一个 2K 上拉电阻(R1)。在我们的 [PIC24F 简介](http://hackaday.com/2008/09/18/web-server-on-a-business-card-part-1/)中阅读更多关于该芯片的信息。

*RS-232 收发器* 

一个便宜的 RS232 收发器(IC2)将 PIC 连接到 PC 串行端口。这个芯片取代了之前版本的总线海盗使用的昂贵的通孔 [MAX3223EEPP+](http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail?name=MAX3223EEPP%2B-ND) 。串行接口将与 USB- >串行适配器一起工作。

*总线上拉电阻*

*![cct-pu450](img/5132b55099e023477f96e898965a3de7.png "cct-pu450")
*

最初的 Bus Pirate 在 2 个引脚上有 3.3 伏上拉电阻，但我们的大多数测试需要额外的外部电阻。更新的设计在三个主总线信号(数据输入、数据输出、时钟)和片选(CS)引脚上有上拉电阻(R20-23)。

一排跳线(SV5)将每个电阻连接到通过 Vext 端子(X4)提供的外部电压。通孔电阻像跳线一样使用，使 PCB 更容易在家蚀刻。

我们找不到一种优雅的方式来从 3.3 伏微控制器控制任意电压上拉电阻阵列。如果你有什么想法，请在评论中分享。

*电源*

VR1 是微控制器和 RS232 收发器的 3.3 伏电源。VR2 是 5 伏电源。两者都需要两个 0.1uF 旁路电容(C3-C6)。J1 为普通 [2.1mm DC 筒形插头](http://en.wikipedia.org/wiki/DC_connector)的电源插孔。7-10 伏 DC 可能是理想的电源范围。

![cct-vr4](img/564a1df5edbc1a67c8998180953d71bf.png "cct-vr4")

最初的总线盗版有双电源，3.3 伏和 5 伏，所以大多数 IC 可以接口，无需额外的电源。一个主要的烦恼是缺少连接芯片的电源复位。如果一个错误配置的 IC 需要重启，我们必须断开一根电线。我们厌倦了这种例行程序，所以我们在更新的设计中加入了软件控制复位。

VR3(3.3 伏)和 VR4(5 伏)是带启用开关的 TI [TPS796XX](http://focus.ti.com/docs/prod/folders/print/tps79650.html) 稳压器。引脚 1 上的高电平使能调节器。下拉电阻(R13、R12)确保当 PIC 不主动驱动线路时，调节器关闭，例如在上电初始化期间。数据手册指定在输入(C23，C21)和输出(C24，C22)引脚上使用一个大电容，我们使用的是在任何地方都使用的 10uF 钽电容。一个额外的可选 0.1uF 电容(C12，C11)可以改善调节。

可切换调节器由 5 伏电源 VR2 供电。我们这样做是因为 VR3 和 VR4 的最大输入为 6 伏，使器件的电源电压范围为 5.2-6 伏。VR2 将在 10 伏以上工作，并为其他调节器提供充足的电源。

VR3(3.3 伏)有足够的裕量，可以采用 5 伏电源供电。VR4(5 伏)将损失约 0.2 伏，但 4.8 伏仍在大多数 5 伏芯片可接受的范围内。实际上，在轻负载下，VR4 的压降小于 0.1 伏。

*电压监控*

*![cct-adcin](img/4389f5dea2b7a3f44092c606a491d532.png "cct-adcin")
*

电压监控是我们非常兴奋的一项新功能。你的项目有没有因为意外短路而神秘地停止响应？总线盗版的电源配备了电压监测，可以检测到电力水平的变化。

每个监控信号通过电阻分压器连接到[模数转换器](http://en.wikipedia.org/wiki/Analog-to-digital_converter) (ADC)。两个 10K 电阻(上面的 R10、R11)将输入电压分成两半，使得 3.3 伏 PIC 微控制器可以测量高达 6.6 伏的电压。

总线盗版有四个电压监视器。监控 3.3 伏和 5 伏电源，以及馈入上拉电阻的外部电压。第四台监视器连接到输出接头的引脚 9，构成一个电压探针。

**PCB**

**![brd450alt](img/308c390952dea642058da584f2e84fe9.png "brd450alt")
**

[点击查看全尺寸摆放图](http://hackaday.com/files/2009/01/brd.png) (PNG)。该板是一个准单面设计，我们在实验室的单面光阻 PCB 上蚀刻我们的电路板。在顶部，靠近 C13，两条跳线在单个过孔处相遇；我们在电路板背面将一根跳线焊接到另一根上。

*零件清单*

| 部分 | 价值 |
| IC1 | [PIC24FJ64GA002](http://www.mouser.com/Search/ProductDetail.aspx?qs=V/yyTCAHA4D/h5r3CRQDtA==) (SOIC) |
| IC2 | MAX3232CSE (SOIC-N) |
| VR1 | [LD 1117s 33](https://www.mouser.com/Search/ProductDetail.aspx?R=LD1117S33CTRvirtualkey51120000virtualkey511-LD1117S33C)3.3 伏稳压器(SOT223) |
| VR2 | [LD 1117 s50](https://www.mouser.com/Search/ProductDetail.aspx?R=LD1117S50TRvirtualkey51120000virtualkey511-LD1117S50)5 伏稳压器(SOT223) |
| VR3 | [TPS 79633](http://www.mouser.com/Search/ProductDetail.aspx?qs=sGAEpiMZZMsGz1a6aV8DcPXeWoVS0Fnzr3zi8%252bAr99Q%3d)3.3 伏稳压器(SOT223-6) |
| VR4 | [TPS 79650](http://www.mouser.com/Search/ProductDetail.aspx?R=TPS79650DCQRvirtualkey59500000virtualkey595-TPS79650DCQR)5 伏稳压器(SOT223-6) |
| C1-13 | [0.1uF 电容器](https://www.mouser.com/Search/ProductDetail.aspx?R=C0805C104M5RACTUvirtualkey64600000virtualkey80-C0805C104M5R) (0805) |
| C20-24 | [10uF 钽电容](http://www.mouser.com/Search/ProductDetail.aspx?R=293D106X96R3A2TE3virtualkey61320000virtualkey74-293D106X96R3A2TE3) (SMC A) |
| R1 | [2000 欧姆电阻](http://www.mouser.com/Search/ProductDetail.aspx?qs=jBethxrBxZb5NLDetw123g%3d%3d) (0805) |
| R2，3 | [390 欧姆电阻](http://www.mouser.com/Search/ProductDetail.aspx?qs=2BMLUTrrT4P7Xm58YbKmPg==) (0805) |
| R4-13 | [10000 欧姆电阻](http://www.mouser.com/Search/ProductDetail.aspx?qs=sGAEpiMZZMtlubZbdhIBIADEshVnklemK%252bhrLNEuMe8%3d) (0805) |
| R20-23 | [2.2K](http://www.mouser.com/Search/ProductDetail.aspx?qs=8tsW7z%2fc78pkoLNVKn1xoQ%3d%3d)–[10K](http://www.mouser.com/Search/ProductDetail.aspx?qs=sGAEpiMZZMtMTfExsNintTsTnthYiOMx%2fND7UkWzrMM%3d)欧姆电阻(通孔) |
| LED1,2 | [LED](http://www.mouser.com/Search/ProductDetail.aspx?qs=7JStj%2fjQ2SElGv%2fp7IzKlg%3d%3d) (0805) |
| J1 | [2.1 毫米电源插孔](http://www.mouser.com/Search/ProductDetail.aspx?qs=8xMK%2bwDsXhcfMNb/YnnwLQ==) |
| X2，X4 | [螺丝夹(2 个端子)](http://www.mouser.com/Search/ProductDetail.aspx?qs=wjes1ZhMGKfGv3iS94oZ%252bQ%3d%3d)*未经测试 |
| X3 | [db9 母串口连接器](http://www.mouser.com/Search/ProductDetail.aspx?qs=nAEW9fCjKd%2fyLNwP2ItddQ%3d%3d)*未测试 |
| ICSP | [0.1 英寸直插头](http://www.mouser.com/Search/ProductDetail.aspx?R=9-146278-0virtualkey57100000virtualkey571-9-146278-0) |
| SV4 | [0.1″销头](http://www.mouser.com/Search/ProductDetail.aspx?R=9-146278-0virtualkey57100000virtualkey571-9-146278-0)或带罩头 |
| SV5 | [0.1 英寸直插头](http://www.mouser.com/Search/ProductDetail.aspx?R=9-146278-0virtualkey57100000virtualkey571-9-146278-0) |

**固件**

固件使用免费演示版的 [PIC C30 编译器](http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=1406&dDocName=en010065)用 C 编写。在我们对 PIC 24F 系列的[介绍中了解所有关于使用这张 PIC 的信息。](http://hackaday.com/2008/09/18/web-server-on-a-business-card-part-1/)

最新的固件发布在 [Hack a Day Bus 盗版页面](http://hackaday.com/the-bus-pirate-universal-serial-interface/)上。最新的来源是在我们的[谷歌代码 SVN 仓库](http://code.google.com/p/the-bus-pirate/source/checkout)。

**使用它**

**![cct-pinout450](img/8e9e99c7982e755ccaa058b4692dd504.png "cct-pinout450")
**

上图显示了总线盗版引脚排列。

我们制作了一根末端带有鳄鱼夹的电缆，并在每根电线上添加了标签，这样我们就不必在每次连接新芯片时都参考这张表。

如果你知道任何酷的连接器或电缆，请在评论中链接到它们。

![ltc2640](img/0759c059e83618305e21849fe8d3f419.png "ltc2640")

*LTC2640 SPI 数模电压转换器*

线性技术 [LTC2640-LZ8](http://www.linear.com/pc/productDetail.jsp?navId=H0,C1,C1155,C1005,C1156,P85250) 是通过 [SPI](http://en.wikipedia.org/wiki/Serial_Peripheral_Interface_Bus) 编程的 8 位[数模转换器](http://en.wikipedia.org/wiki/Digital-to-analog_converter) (DAC)。DAC 本质上是一个可编程分压器。它们对于重新创建波形(如音频信号)很有用。一个 8 位 DAC 在 0 和基准电压之间有 255 个偶数间隔，我们使用的 L 部分有一个内部 255 基准电压。

LTC2640 仅采用小型 SOT223-8 封装，因此我们制作了 DIP-8 芯片外形的试验板适配器。我们的 LTC2640 封装包含在本文末尾的项目档案中。

![ltc2640450](img/f339afc967d7e3b52767ac8be21bbcaa.png "ltc2640450")

上面的原理图显示了我们针对 LTC2640 的测试电路。它需要一个 2.7-5 伏的电源，我们用的是巴士海盗的 3.3 伏电源。C1 是电源引脚和地之间的旁路电容。引脚 8 是低电平有效复位引脚，正常工作时将其连接到高电平。引脚 7 是 DAC 输出，在此处连接总线盗版电压测量探针(ADC)。

| **公交车海盗** | **LTC2640 (pin #)** |
| MOSI | 空间数据基础设施(3) |
| 时钟 | SCK (2) |
| 特许测量员 | 政务司司长/土地发展(一) |
| 物理输出核心 | VOUT (7) |
| +3.3 伏 | CLR (8) |
| +3.3 伏 | VDD (5) |
| GND | GND (4) |

我们将 Bus Pirate 连接到 LTC2640，如下表所示。LTC2640 没有数据输出引脚，该 SPI 连接未被使用。

总线盗版的硬件 SPI 库和软件 RAW3WIRE 库与 LTC2640 的 SPI 接口兼容。我们使用了 SPI 库；如果使用 RAW3WIRE 库，请务必选择*正常引脚输出*。

> HiZ > m**<–选择模式**
> 1。HiZ
> 2。单线
> 3。UART
> 4。I2C
> 5。SPI
> 6。JTAG
> 7。拉线 2 线
> 8。RAW3WIRE
> 9。PC AT 键盘
> 模式>5**–SPI 或 raw 3 wire**900 模式设定
> 设定速度:
> 1。30KHz
> 2。125KHz
> 3。250KHz
> 4。1MHz
> 速度>1**<–低速测试**
> …
> 102 SPI 就绪
> SPI >

按 M 进入总线盗版模式菜单，选择 5 进入 SPI 模式。SPI 模块有许多配置选项，请对所有选项使用默认选项。SPI 模式就绪后，我们需要配置电源。

> SPI > p**<–电源设置**
> W/w 切换 3.3 伏电源？
> 1。没有
> 2。是
> 模式>2**<–使用 3.3 伏电源**
> W/w 切换 5 伏电源？
> 1。否
> 2。是
> 模式>1**<–不要使用 5V 电源**
> 9xx 电源配置，使用 W/w 切换
> 9xx 电压监控器:5V:0.0 | 3.3V:0.0 | VPULLUP:0.0 |
> SPI>

p 打开总线盗版电源菜单。我们使用 3.3 伏电源，而不是 5 伏电源。电压监视器验证电源是否关闭。

> SPI > W**<–大写 W ( [傻 CSS](http://www.w3.org/TR/CSS2/text.html#caps-prop) )使能电源**
> 9xx 3.3 伏电源 ON
> SPI>v**<–电压监控器**
> 9xx 电压监控器:5V:0.0 | 3.3V:3.3 | VPULLUP:0.0 |
> SPI>

大写字母“W”启用上一菜单中选择的任何电源，小写字母“W”禁用它们。v 显示电源电压监视器，它现在显示 3.3 伏电源的 3.3 伏输出。

配置完成后，我们可以通过 SPI 总线向 LTC2640 发送命令。LTC2640 具有 24 位(3 字节)接口协议。第一个字节是命令，后面是两个数据字节。LTC2640 提供 8、10 和 12 位版本；8 位版本使用第一个字节来设置 DAC 值，忽略第二个字节。

> SPI >[0b 00110000 255 0]**<–将 DAC 设为满态**
> 110 SPI CS 使能
> 120 SPI 写:0x 30**<–写 DAC 命令**
> 120 SPI 写:0x ff**<–DAC 值**
> 120 SPI 写:0x 00**<–无关**
> 140 CS

每个 SPI 命令都以使能片选引脚([)开始。第一个字节是更新 DAC 的命令(0b00110000)，后面是要输出的值(255)，第三个字节被忽略(0)。命令以禁用片选(])结束。

我们使用具有 255 个偶数电压步长的 8 位 DAC，输出设置为 255 表示 100%。我们可以使用总线盗版电压探针来测量输出。

> SPI > d**<–测量电压**
> 9xx 电压探针:2.5 伏**<–DAC 输出**
> SPI >

d 触发电压测量。DAC 输出电压为内部基准电压 2.5v 的 100% (255/255)。

> SPI >[0b 00110000 0]d
> 110 SPI CS 使能
> 120 SPI 写:0x 30**<–写 DAC 命令**
> 120 SPI 写:0x 00**<–DAC 值**
> 120 SPI 写:0x 00**<–无关**
> 140 CS 禁用
> 9xx 电压探针:0.0 伏

DAC 值为 0 的相同命令输出 2.5 伏的 0%(0/255)；0 伏特。

> SPI >[0b 00110000 128 0]d
> 110 SPI CS 使能
> 120 SPI 写:0x 30**<–写 DAC 命令**
> 120 SPI 写:0x 80**<–DAC 值**
> 120 SPI 写:0x 00**<–无关**
> 140 CS 禁用
> 9xx 电压探针:1.2v

DAC 值 128 约为基准电压 1.2 伏的 50% (128/255)。

> SPI >[0b 01000000 0]d
> 110 SPI CS 使能
> 120 SPI 写:0x 40**<–掉电命令**
> 120 SPI 写:0x 00**<–无关**
> 120 SPI 写:0x 00**<–无关**
> 140 CS 禁用
> 9xx 电压探针:0.0 伏

LTC2640 具有低功耗模式，由命令 0b01000000 和两个被忽略的字节触发。执行关断命令后，我们可以验证 DAC 是否有输出。写入任意 DAC 值以退出低功耗模式。

**更进一步**

巴士海盗的下一步是什么？我们最终将对设计进行最终更新，包括专业制作的双面 PCB 上的 USB。电源指示灯是为这个版本设计的，但没有包括在内。如果有一个 AT 键盘连接器，在没有 PC 的情况下进行调试也是很方便的。在 [Hack a Day Bus Pirate 页面](http://hackaday.com/the-bus-pirate-universal-serial-interface/)查看路线图和愿望清单。

**下载:[bus pirate . v1a . zip](http://blog.mahalo.com/hackaday/howto/buspirate.v1a.zip)**