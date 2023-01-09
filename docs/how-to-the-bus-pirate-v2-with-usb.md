# 操作方法:USB 总线盗版 V2

> 原文：<https://hackaday.com/2009/06/25/how-to-the-bus-pirate-v2-with-usb/>

![buspiratev2goii450](img/470775bf17d575b77a2322e5e630f5fb.png "buspiratev2goii450")

更新，2009 年 7 月 4 日星期六:所有预订都已停止。

[总线盗版](http://www.buspirate.com)是一个通用串行接口工具，我们用它来[测试新芯片](http://hackaday.com/category/parts/)而不用写任何代码。它目前支持大多数串行协议，包括单线、I2C、SPI、JTAG、异步串行、MIDI 等。我们添加了一些我们经常需要的其他功能，如脉宽调制、频率测量、电压测量、总线嗅探器、上拉电阻以及可切换的 3.3 伏和 5 伏电源。

新的 v2 系列为迄今为止最好的总线盗版设计增加了 USB 电源和连接。我们还尽可能减少了零件数量和成本。如果你想得到一些总线盗版 USB 的好处，Seeed Studio 组装硬件的价格为 30 美元(包括全球运费)。

休息后阅读新设计。

**概念概述**

![overview450](img/4816a82f46547042d823917025320b92.png "overview450")

总线盗版连接到 PC 的 USB 端口。用户从 PC 上的串行终端向总线盗版者发送命令。命令被翻译成控制微芯片的总线协议。查看我们的[总线盗版页面](http://www.buspirate.com)获取完整文档。

最新固件支持单线、I2C、SPI、JTAG、异步串行、MIDI 和 PC 键盘。按位 2 线和 3 线库可以连接大多数专有串行协议。更多的协议一直在增加，查看我们的[谷歌代码 SVN 页面](http://code.google.com/p/the-bus-pirate/)上的源代码。

**硬件**

**![cct25450](img/67386c4e73b80eefafc18ace6d04f3d3.png "cct25450")**

[点击查看原理图](http://hackaday.com/files/2009/05/cct25a.png) (PNG)的大图。原理图和电路板布局是用免费版的 [Cadsoft Eagle](http://www.cadsoft.de) 制作的。从我们的[谷歌代码](http://code.google.com/p/the-bus-pirate/downloads/list)页面下载最新文件。

*PIC24F*

*![pic24f-highlight](img/ed14ade19c83f184588f96f0482b3034.png "pic24f-highlight")
*

微芯片 [PIC24F 系列](http://hackaday.com/2008/09/18/web-server-on-a-business-card-part-1/)微控制器生成用户界面，并将输入转化为总线通信。V2 使用与之前的巴士盗版相同的 [24FJ64GA002](http://www.microchip.com/wwwproducts/Devices.aspx?dDocName=en026374) 。它很便宜，有大量的内存，几个 5v 的输入引脚，外设引脚选择功能让我们可以在任何地方分配硬件模块。

PIC (IC1)由 3.3 伏稳压器(VR2，C23)供电。每个 PIC 电源引脚都有一个 0.1uF 旁路电容(C1，2)。内部 2.5v 调节器需要一个 10uF 钽电容(C20)。编程引脚连接到 PCB 边缘的五引脚接头(ICSP)。

*USB 接口* 

*![ftdi-450ii1](img/21b8e81326209b6512a669cb042e5eb7.png "ftdi-450ii1")*

Bus Pirate 由 USB 5v 电源供电，首先用铁氧体磁珠(L1)和 10uF 钽电容(C21)滤波。我们使用了小的，仍然不太常见的， [USB mini-b](http://en.wikipedia.org/wiki/USB#Types_of_USB_connector) 连接器(J2)。

选择铁氧体磁珠是一个常见的难题。它的目的是过滤小的功率波动，电路的所有电流都将通过它。我们可以猜测，总线盗版最差情况下的电流消耗是 525ma (3 个电源@ 150ma，FTDI 芯片@ 25ma，2 个 LEDs @最大 50ma)。为了安全起见，请使用额定电流至少为 1000 毫安的铁氧体磁珠。我们用的是[这个](http://www.mouser.com/Search/ProductDetail.aspx?R=BLM21PG331SN1Dvirtualkey64800000virtualkey81-BLM21P331SG)，额定 1500 毫安，10 分钱。

FTDI [FT232BL](http://www.ftdichip.com/Products/FT232BM.htm) USB- >串行芯片(IC2)处理 USB 连接。你可能对来自各种 [Arduino](http://hackaday.com/category/arduino-hacks/) 板卡的这款芯片比较熟悉。FTDI 拥有[广泛的驱动支持](http://www.ftdichip.com/Drivers/VCP.htm)对于大多数平台，我们使用虚拟 com 端口驱动。这是最新一代芯片，只提供小型 SSOP 和 QFN 封装。我们可以毫不费力地将它手工焊接到专业 PCB 上，但这并不适合所有人。

FT232BL 直接由经过滤波的非稳压 USB 电源供电。C4 是 FTDI232BL 电源引脚的去耦电容。单个 LED (LED4/USB)指示 USB 状态和活动。FT232BL RXLED 引脚吸收电流，因此我们通过 1.1K 电阻(R3)从 5v USB 电源为 LED 供电。

虽然 FT232BL 通过 USB 电源以 5v 电压运行，但其串行 IO 引脚具有独立的电源输入–它们可以在另一个电压下运行。由于微控制器是 3.3 伏，我们只需为 FT232BL IO 引脚提供 3.3 伏电源，并消除任何古怪的转换电路。我们使用芯片的内部 3.3 伏稳压器为 IO 引脚供电，因为这是最容易走线的。IO 引脚有自己的 0.1uF 旁路电容(C5)。

*可切换电源*

*![vreg-450ii](img/8ceb4446d75d91c44d67b6df376ce363.png "vreg-450ii")
*

Bus Pirate 具有板载 3.3 伏和 5 伏电源(VR3、VR4)，可以为测试电路供电。电源是可切换的，所以当出现问题时，我们可以通过软件重置电路。为了更加安全，在终端中激活之前，供应被推迟。

[SparkFun](http://www.sparkfun.com) 的 [Nathan Seidle](http://www.sparkfun.com/commerce/account.php?id=7185) 建议我们用一个[mic 5205-xxym 5](http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&name=576-1259-1-ND)(0.90 美元)替换[巴士海盗 v1a](http://hackaday.com/2009/01/22/how-to-bus-pirate-v1-improved-universal-serial-interface) 中使用的[TPS 796 xx](http://www.mouser.com/Search/ProductDetail.aspx?qs=sGAEpiMZZMsGz1a6aV8DcPXeWoVS0Fnzr3zi8%252bAr99Q%3d)(2.50 美元)。与 TPS796xx 的 800ma 电流相比，它们仅提供 150ma 的最大电流，但成本节约和器件数量减少是值得的。

调节器由 5v USB 电源供电。由于没有净空，5 伏调节器比最佳值低几毫伏，但它在大多数 5 伏器件规定的最低水平内。

MIC5205 需要一个大输出滤波电容(C22-24，10uF)，但不需要输入电容。BP 引脚上的一个可选小电容可以降低电源噪声，但我们没有考虑这一点，因为它在实践中没有多大作用。

*EN* 引脚上的小电压使能电源，我们使用 10K 下拉电阻(R18，未显示)来确保 PIC 初始化时电源保持关闭。带有限流电阻 R32 的 LED3/VREG 在电源激活时亮起。

*板上上拉电阻*

*![resis](img/c6933008648522cffba2f7a1bba63dd9.png "resis")
*

总线盗版 V2 有多电压，软件控制的上拉电阻通过 [4066](http://www.fairchildsemi.com/ds/CD%2FCD4066BC.pdf) (PDF)四双边开关(IC3)。启用时，4066 将四个板载总线上拉电阻(R20-23，10K)连接到 Vpullup 引脚上的任何外部信号(0 至 5v)。禁用时，输出为高阻态，对总线线路没有影响。

4066 不能切换大于电源电压的输入电压。为了给它尽可能宽的范围，我们从 USB 电源(5 伏)供电。

当在 5v 下工作时，需要 4v+来启用 4066。PIC 引脚的最大输出电压为 3.3 伏，所以我们有一个问题。我们用一个 5v 容差 PIC 引脚和一个上拉电阻来解决这个问题。我们用一个上拉电阻将 4066 接通至 5v(R19，10K)，然后通过将连接的 PIC 引脚切换至地来禁用它。

在上电瞬间，PIC 引脚为高阻态，4066 输出有效，因为上拉电阻将控制引脚保持在 5v。如果 Vpullup 输入连接到外部 5v 电源，而总线连接到 3.3v 设备，这是一个问题，短暂暴露在 5v 电压下可能会损坏设备。如果您担心这一点，请确保在给总线盗版供电之前，没有活动电源连接到 Vpullup 输入。如果使用一个板载电源作为上拉电压，这不是问题，因为它们在启动时会被禁用。

*电压监控*

*![cct-adcin](img/b6323735e854c0828c51bbb67eca46c0.png "cct-adcin")
*

四个[分压器](http://en.wikipedia.org/wiki/Voltage_divider) (R10-17，10K)，连接到[模数转换器](http://en.wikipedia.org/wiki/Analog-to-digital_converter)，允许 3.3 伏 PIC 安全测量高达 6 伏 DC。

两个电压监控器测量可切换电源输出。一个测量 Vpullup 输入电压，另一个连接到外部电压测量探针。

*指示灯 led*

*![front-back2450](img/f22de569633f141ce66f457ef57bd9b8.png "front-back2450")
*

三个指示灯分别指示电源、模式和电压调节器状态(LED1-3)。LED4/USB 显示 USB 活动。

PCB 的正面和背面有用于电阻 R30-32 和 led 1-3 的焊盘。应该只填充一个集合。我们在两侧都放置了衬垫，以便安装电路板时，指示灯 led 可以紧靠机箱顶部。

*V2a vs V2go*

*![bpv2450](img/4fbd12ce980b787f46a32129807cb479.png "bpv2450")
*

点击查看 2a 版硬件的大图[示意图](http://hackaday.com/files/2009/04/cct1.png) (PNG)和[布局图](http://hackaday.com/files/2009/04/brd.png) (PNG)。老鹰布局文件可以在我们的[谷歌代码 SVN](http://code.google.com/p/the-bus-pirate/downloads/list) 中找到。

总线盗版 V2a 是一个开发者的板。除了 V2go 的所有功能，它还包括一个用于外部电源的插孔(J1)和一个附加的 5 伏稳压器(VR1)。开关(S1)在 USB 电源和外部电源之间进行选择。

V2a 上的 FT232BL 芯片直接由 USB 电源供电，不连接外部电源。这是有用的，如果你想禁用 USB 和使用串行端口的 PC 或 PDA 总线盗版。

V2a 4066 使能上拉电阻由可切换的 5v 稳压器供电。要激活 4066，必须启用 5 伏调节器。不要忘记安装位于 v2a PCB 背面的 4066 上拉电阻(R19)。

**PCB**

![brd25450](img/c09871d9f7b2369f9d92f0c4a8dd689b.png "brd25450")

PCB 是紧凑的两层设计。我们[准备了 gerbers](http://hackaday.com/2009/01/15/how-to-prepare-your-eagle-designs-for-manufacture/) ，并让我们通常的服务 [BatchPCB](https://www.batchpcb.com/) 制作了 PCBs 美元，运往欧盟)，并尝试了由 [Seeed Studio](http://www.seeedstudio.com/wiki/index.php?title=Main_Page) 提供的新服务(32 美元，运往全球)。

Seeed 有专门针对开源硬件项目的 PCB 服务。我们花了 32 美元(包括全球运费)买了 5 块小电路板，Seeed 还额外做了几块在他们店里卖。我们喜欢有额外 PCB 可用的想法。

你可能会从 Seeed Studio 廉价的改进版 Arduino 克隆版中知道它。他们位于中国电子制造热点深圳。一群著名的博客作者最近[访问了该地区](http://www.sparkfun.com/commerce/news.php?id=236)，并写了关于[巨大的电子元件市场](http://www.sparkfun.com/commerce/news.php?id=237)的文章。

![seeed-batchpcb4501](img/71aceef269b3b8b7987c872ce7d523e5.png "seeed-batchpcb4501")

种子订单在 14 天后到达(左)，批次 PCB 订单在 30 天后到达(右)。Seeed 和 BatchPCB 都制作漂亮的 PCB。Seeed 的周转速度更快，最小走线宽度和间距更好(8 密耳对 6 密耳)。BatchPCB 有标准的绿色 PCB，Seeed 给你绿色、黑色或白色的选择；红色、蓝色和黄色是额外的 7.5 美元。

我们真的很喜欢 Seeed PCB 服务，我们订单中的额外总线盗版 [v2go](http://www.seeedstudio.com/depot/the-bus-pirate-v2-go-pcb-p-331.htmlhttp://www.seeedstudio.com/depot/the-bus-pirate-v2-go-pcb-p-331.html) 和[v2a](http://www.seeedstudio.com/depot/the-bus-pirate-v2-pcb-p-330.html)PCB 在 Seeed 商店有售。如果你想要一个单板，闭源工作，或者不介意额外的等待，BatchPCB 仍然是最便宜的原型选择。

*零件清单*

| **部分** | **值(包)** |
| IC1 | [PIC24J64GA002](http://www.mouser.com/Search/ProductDetail.aspx?qs=V/yyTCAHA4D/h5r3CRQDtA==) (SOIC) |
| IC2 | [FT232RL](http://www.sparkfun.com/commerce/product_info.php?products_id=650) (SSOP) |
| IC3 | CD4066D (SOIC-N) |
| VR2,3 | mic 5205-3.3 ym5 3.3 伏稳压器 (SOT23-5) |
| VR4 | mic 5205-5.0 ym5 5 伏稳压器 (SOT23-5) |
| C1 五号 | [0.1uF 电容器](https://www.mouser.com/Search/ProductDetail.aspx?R=C0805C104M5RACTUvirtualkey64600000virtualkey80-C0805C104M5R) (0805) |
| C20-24 | [10uF 钽电容器](http://www.mouser.com/Search/ProductDetail.aspx?R=293D106X96R3A2TE3virtualkey61320000virtualkey74-293D106X96R3A2TE3) (SMC-A) |
| 腰神经 2 | [1000ma+铁氧体磁珠](http://www.mouser.com/Search/ProductDetail.aspx?R=BLM21PG331SN1Dvirtualkey64800000virtualkey81-BLM21P331SG) (0805) |
| R1 | [2000 欧姆电阻](http://www.mouser.com/Search/ProductDetail.aspx?qs=jBethxrBxZb5NLDetw123g==) (0805) |
| R3，30 | [1100 欧姆电阻](http://www.mouser.com/Search/ProductDetail.aspx?qs=DZvKvnD5UYWyFJjgnPvJ4g%3d%3d) (0805) |
| R10-23 | [10000 欧姆电阻](http://www.mouser.com/Search/ProductDetail.aspx?qs=sGAEpiMZZMtlubZbdhIBIADEshVnklemK%252bhrLNEuMe8%3d) (0805) |
| 31.32 兰特 | [390 欧姆电阻](http://www.mouser.com/Search/ProductDetail.aspx?qs=2BMLUTrrT4P7Xm58YbKmPg==) (0805) |
| LED1-4 | [LED](http://www.mouser.com/Search/ProductDetail.aspx?qs=7JStj%2fjQ2SElGv%2fp7IzKlg%3d%3d) (0805) |
| J2 | [USB 迷你 B](http://www.sparkfun.com/commerce/product_info.php?products_id=587) (贴片) |
| 输入－输出 | [0.1″销头](http://www.mouser.com/Search/ProductDetail.aspx?R=9-146278-0virtualkey57100000virtualkey571-9-146278-0) (2×05) |
| ICSP | [0.1″销头](http://www.mouser.com/Search/ProductDetail.aspx?R=9-146278-0virtualkey57100000virtualkey571-9-146278-0) (1×05) |
| 标准时间（standard time） | [0.1″插针](http://www.mouser.com/Search/ProductDetail.aspx?R=9-146278-0virtualkey57100000virtualkey571-9-146278-0)(1×03)**未填充，可选** |
|  **** |  |

| ***可选*** | ***零件为 V2a*** |
| C6-10 | [0.1uF 电容器](https://www.mouser.com/Search/ProductDetail.aspx?R=C0805C104M5RACTUvirtualkey64600000virtualkey80-C0805C104M5R) (0805) |
| J1 | [2.1 毫米电源插孔](http://www.mouser.com/Search/ProductDetail.aspx?qs=b2tC%2fwvzm2TxaPjSsb%252bCzQ%3d%3d)(贴片) |
| LED5,6 | [LED](http://www.mouser.com/Search/ProductDetail.aspx?qs=7JStj%2fjQ2SElGv%2fp7IzKlg%3d%3d) (0805) |
| 33，34，40 | [1100 欧姆电阻](http://www.mouser.com/Search/ProductDetail.aspx?qs=DZvKvnD5UYWyFJjgnPvJ4g%3d%3d) (0805) |
| S1 | [滑动开关，SPDT，rt 角度](http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&name=679-1849-ND) |
| VR1 | [LD 1117 s50 5 伏稳压器](https://www.mouser.com/Search/ProductDetail.aspx?R=LD1117S50TRvirtualkey51120000virtualkey511-LD1117S50) (SOT223) |

**固件**

所有硬件版本的最新总线盗版固件总是可以在我们的[谷歌代码页](http://code.google.com/p/the-bus-pirate/)上获得。代码用 C 语言编写，用 [Microchip C30 演示编译器](http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=1406&dDocName=en534868&redirects=c30)编译。

*引导程序*

最新固件最大的变化是增加了一个 [bootloader](http://en.wikipedia.org/wiki/Boot_loader#Boot_loader) 。现在可以通过 USB 或串行连接更新固件。

引导程序是一个小程序，位于 PIC 程序存储器的开始。它通过 USB 或串行端口接受更新的固件，并将其保存到芯片中。

![bootload-jumper4501](img/5a461b621673ea1cbedf23751c795c13.png "bootload-jumper4501")

bootloader 来自微芯片应用笔记 [AN1157](http://en.wikipedia.org/wiki/Boot_loader#Boot_loader) 。我们修改了引导加载程序，以便在上电时检查编程时钟(PGC)和数据(PGD)引脚之间的跳线(更新，左上)。如果有连接，引导装载程序接管并等待新代码。如果没有连接，引导装载程序将退出并运行主程序。

在没有安装跳线的情况下，偶然进入引导加载程序的可能性非常小。这不会损坏总线盗版，但你需要重新连接它。您可以通过将跳线移动到接地引脚和内部编程引脚(正常，右上方)之间的一个位置来防止这种情况。

*用引导程序升级固件*

*![pic24fqp](img/58233f1d9ec414dfc6578134593aaaeb.png "pic24fqp")
*

如果你使用的是新的芯片，首先使用一个“真正的”编程器，如 [ICD2](http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=1406&dDocName=en010046) 或 [PicKit](http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=1406&dDocName=en010046) ，通过 ICSP 头文件用引导加载器固件(vxx-PIC Bootloader.hex)对其进行编程。

如果您正在升级，请遵循此过程或参考固件下载中的说明。

*   断开总线盗版从任何电源，如 USB 电缆。
*   在 ICSP 接头的编程数据和时钟引脚之间放置一根跳线。这将触发引导程序模式。
*   将 Bus Pirate 连接到 USB 端口(或者，如果适用，电源和串行电缆)。
*   启动微软视窗 P24QP.exe 编程器实用程序。您可能需要修改 P24qp.ini 中的 COM 端口(portindex=)以匹配您的系统。如果您想为非 Windows 系统编写应用程序，可以使用程序员源代码，并且在 AN1157 中记录了简单的引导加载程序协议。
*   单击连接到设备图标(#1)。该程序将连接到 PIC。
*   单击文件夹图标(#2)并打开固件更新文件(vxx-bl . hex 的固件)。
*   单击擦除设备图标(#3)擦除芯片。不要跳过这一步。如果忘记擦除芯片，编程可能不会成功。
*   单击写入设备图标(#4)对新固件进行编程。忽略 0x400 和 0xBFF 之间的任何验证错误，引导加载程序位于该区域，不会得到更新。
*   单击绿色箭头图标(#5)退出引导程序并启动程序。在警告时单击确定，我们使用跳线重新进入引导加载程序。
*   移除编程引脚上的跳线，或将其移动一个位置，以将内部 PGx 引脚接地(GND)。
*   ***重要* * *现在通过断开并重新连接 USB 电缆(或电源线)来重新启动 Bus Pirate。有些功能只有在硬件完全复位后才能工作。

**使用它**

*USB 设备驱动* 

你可能需要为你的平台安装一个 [FTDI 虚拟串口驱动](http://www.ftdichip.com/Drivers/VCP.htm)。

在 Windows 上，转到设备管理器来配置 FTDI 驱动程序或检查 COM 端口号。

*菜单和语法*

*![term450](img/10a3043c7ed847b5318aa317dbd2ceca.png "term450")
*

使用串行终端与总线盗版者通信。我们喜欢万亿术语。

当终端设置为 115200bps、8 个数据位、无奇偶校验、1 个数据位时，总线盗版效果最好。在终端中禁用本地回显，并使用 CR 来换行。有些模式还需要 Xon/Xoff 软件流量控制。

在串行终端中，按？获取帮助菜单。在[总线盗版页面](http://www.buspirate.com)上阅读更多关于总线盗版的菜单和语法。在我们最近的[部分帖子](http://hackaday.com/category/parts/)中有很多演示。

*LED 指示灯*

*![leds-450](img/78310346a81f139a3061fdb8640ef33e.png "leds-450")
*

*   **PWR** 表示总线盗版的电源。
*   当 I/O 引脚处于安全的高阻抗状态时，模式关闭。当使用总线模式时，模式被点亮，引脚可能是活动的。
*   **VREG** 表示机载可切换电源处于活动状态。
*   **UR** 是一个单 USB 活动指示灯 LED。它显示来自*的数据，从*个人电脑*到*总线盗版。你可以用 [FTDI 配置实用程序](http://www.ftdichip.com/Resources/Utilities.htm)改变这个 LED 显示的内容。

*连接*

插针位置图: [v2a](http://hackaday.com/files/2009/01/brd3.png) ， [v2g0](http://hackaday.com/files/2009/01/brd251.png) 。

| **销名&#124;
** | **描述(公交海盗是主人)** |
| MOSI | 主机数据输出、从机输入(SPI、JTAG)、串行数据(单线、I2C、KB)、TX* (UART) |
| CLK | 时钟信号(I2C、SPI、JTAG、KB) |
| 军事情报部门组织(Military Intelligence Service Organization) | 主机数据输入，从机输出(SPI，JTAG) RX (UART) |
| CS* | 片选(SPI)、TMS (JTAG) |
| 去吧 | 辅助 IO，频率探针 |
| 物理输出核心 | 电压测量探头(最大 6 伏) |
| Vpu | 板载上拉电阻的电压输入(0-5v)。 |
| +3.3v | +3.3 伏可切换电源，最大 150 毫安 |
| +5.0v | +5 伏可切换电源，最大 150 毫安 |
| GND | 接地，连接到测试电路的接地 |

注意:*在固件 v0g 中，TX 从 CS 移到了 MOSI。

10 针 I/O 模块包含连接到测试电路的数据信号和电源。每个引脚都标在 PCB 的背面，详细说明请参考上表。

V2 的引脚排列与 V1 相似，但我们将电源输出和 Vpullup 输入移至电缆束。我们还取消了第二个未使用的辅助引脚。

**结论**

如果你想要一个完整的巴士海盗或套件，这里有几个选项:

*   Seeed Studio 接受组装的 Bus Pirate v2go 硬件的预购，直到 7 月 3 日周五结束。一辆组装好的巴士海盗 v2go 30 美元，包含全球运费。
*   Seeed Studio 还有我们订单中额外的[v2g 0](http://www.seeedstudio.com/depot/the-bus-pirate-v2-go-pcb-p-331.html)(5.90 美元)和[v2a](http://www.seeedstudio.com/depot/the-bus-pirate-v2-pcb-p-330.html)(6.50 美元)PCB。
*   Fundamental Logic 出售一个[通孔套件](http://spiffie.org/kits/buspirate/)版本的总线盗版 V1a(29.50 美元)。 *****v1a 仅是串口*****

感谢所有为这个项目做出贡献的人。如果没有大量的评论反馈,“巴士海盗”就不可能出现。如果你想参与其中，加入谷歌代码的[巴士盗版项目](http://code.google.com/p/the-bus-pirate/)。

**Hack a Day review disclosure** :我们要求 Seeed Studio 免费制作我们的第一批 PCB。从那以后，我们已经下了几笔订单。

![bpv2goiii](img/5e6aabf845828620a8523a8e950dbe6c.png "bpv2goiii")