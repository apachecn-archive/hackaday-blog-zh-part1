# 操作方法:USB 遥控接收器

> 原文：<https://hackaday.com/2008/10/30/how-to-usb-remote-control-receiver/>

现在我们听 MP3，看 XVIDs 或 x264s，电脑是大多数家庭至少一个房间的娱乐中心。除非你有一个特别的 HTPC，否则你可能会被困在使用键盘来暂停、改变音量和快进烦人的《流言终结者》回顾。PC 遥控接收器的范围从古代的串口设计(谁有？)到流行软件不支持的 USB 设备。在这篇操作指南中，我们设计了一个 USB 红外接收器，它模仿了一个 Windows、Linux 和 [Mac](http://www.mahalo.com/Mac_Hacks "Mac Hacks - Mahalo") 软件支持的通用协议。我们有完整的协议指南和原理图以及零件清单。

**设计概述**

**![](img/c2b41acb140bc425a3a389d752690dcd.png "overview")
**

遥控器通过调制红外光束传输数据。红外接收器 IC 将调制光束分离成干净的 0 和 1 流。数据流由微控制器解码，并通过 USB 连接发送到计算机。软件处理代码并在计算机上触发动作。

**背景**

*电脑红外接收器*

[最古老的 PC 红外接收器设计](http://www.lirc.org/receivers.html)使用接收器 IC 来切换串行端口引脚，通常是 DCD。这种设计大概起源于[新闻组](http://en.wikipedia.org/wiki/USENET)，至今仍是网络上最流行的: [Engadget](http://www.engadget.com/2006/05/16/how-to-ir-remote-control-your-computer/) ， [Instructables](http://www.instructables.com/id/IR-Remote-Control-For-your-Computer/) 等。这些不是真正的串行设备，因为它们不向 PC 发送数据。取而代之的是，计算机程序对串行端口上的脉冲进行计时，并对信号进行解调。这是一个超级简单的设计，但它依赖于直接中断访问和定时精度，而这在 Windows 中已不再可用。Linux 或 Mac 用户可以试试这个接收器，如果你还有串口的话。我们无法让这种类型的接收器与现代 Windows XP PC 上的串行端口一起工作，也不要指望通过 USB- >串行转换器传输精确的时序。

一些更先进的红外接收器是真正的串行端口设备，在向计算机发送数据之前测量或解码红外信号。[UIR/伊尔曼](http://fly.cc.fer.hr/~mozgic/UIR/)和 [UIR2](http://users.skynet.be/sky50985/) 整合了经典的 PIC 16F84，但不提供固件和/或源代码。这些设备应该可以在现代计算机上工作，必要时可以通过 USB- >串行转换器工作。 [USBTINY](http://www.xs4all.nl/~dicks/avr/usbtiny/) 和[USB boy](http://usbirboy.sourceforge.net/)是原生 USB 设备，但缺乏广泛支持。

*接收器软件*

不管接收器类型如何，计算机都需要一个程序来监听传入的远程命令，并将它们转换成计算机上的动作。Linux 和 Mac 用户有 [LIRC](http://www.lirc.org/) ，它支持一堆不同的接收器类型。Windows 用户就没那么幸运了。 [WinLIRC](http://winlirc.sourceforge.net/) 是 LIRC 一个废弃的 Windows 端口，用于简单的基于中断的串口接收器；WinLIRC 最后一次开发是在 2003 年。[大梁](http://www.promixis.com/products.php)原本是一个免费的 PC 自动化工具，但经过 30 天的试用，已经变成了昂贵的臃肿软件。幸运的是，最后一个[免费版的大梁(3.2.9b)](http://www.oldversion.com/talk/showthread.php?t=1465) 仍然可以下载。

**使用红外遥控协议**

*解码红外信号*

远程控制将命令编码在 38KHz 载波脉冲的间隔或定时中，[San Bergmans]对所涉及的原理有一个[解释。红外接收器 IC 将数据流从载波中分离出来。我们的工作是用微控制器解码数据流。有几十种远程控制协议，但是 Phillips 的](http://www.sbprojects.com/knowledge/ir/ir.htm) [RC5](http://www.sbprojects.com/knowledge/ir/rc5.htm) 是广泛的，并且被业余爱好者普遍使用。

RC5 是 14 个等长位的流，每位时间正好为 1.778 毫秒。比特时间前半段的脉冲代表 0，后半段的脉冲代表 1。这个方案叫做[曼彻斯特编码](http://en.wikipedia.org/wiki/Manchester_coding)。

![](img/7e48cfeeb9b62e5398b2ac9220a160db.png "logic-450")

我们使用逻辑分析仪来检查 Happauge WinTV 遥控器的输出，这是一个[已知的](http://osdir.com/ml/hardware.lirc/2006-04/msg00061.html) RC5 遥控器。该图示出了两次按下 1 按钮和两次按下 2 按钮；注意，输出是相反的，曼彻斯特编码与上面的描述相反。

前两个位时间是起始位，后面是跳变位。每次按下按钮时，toggle 位都会反转，因此接收器可以区分保持和重复按下之间的区别。接下来的 5 位是地址(0b11110=0x1E)，后跟命令(0b000001=0x01，0b000010=0x02)。RC5 的向后兼容扩展使用第二个起始位作为命令位 7。

*代表计算机的远程代码*

回顾以前的设计，我们看到了三种向计算机传达远程命令的通用方法:

*   协议专用接收器解码一个协议，并将实际解码的命令发送到 PC
*   一种更通用的接收器测量每个脉冲的时间和间隔，并将完整的波形发送到 PC 进行分析。
*   一些接收器为信号创建唯一的散列，但实际上并不包括足够的数据来完全重建波形。

虽然我们更倾向于一般的哈希方法，但是我们唯一的远程使用 RC5，构建一个 RC5 专用的解码器更有意思。我们在固件部分描述了对更通用版本的修改。

*计算机接口协议*

我们不想编写自己的接收器软件或驱动程序，所以我们寻找一个现有的、成熟的通信协议来模仿。IRA 伊尔曼/艾拉/ctin fra/好莱坞+型接收机由大梁和 LIRC 支持，并使用带握手的简单串行协议:

*   该器件由串行端口的 DTS 和 DTR 引脚初始化。我们没有这些，也不在乎。
*   计算机发送“IR ”,有一个可选的延迟。设备回复“OK”。我们会在每个“R”上发送“OK”
*   遥控代码作为唯一的六字节散列发送。我们将解码一个 RC5 信号并发送实际值，但是也可以使用通用散列来代替。

这个协议是针对一个串口设备的，但是我们的 USB 接收器将作为一个虚拟的串口出现，程序不会知道其中的区别。

**硬件**

![](img/e292aeea7e3120094569a7210a2697e9.png "cct")

[点击此处查看全尺寸示意图](http://hackaday.com/files/2008/10/cct-large2.png) (png)。我们的接收器基于一个支持 USB 的 PIC [18F2455](http://www.microchip.com/wwwproducts/Devices.aspx?dDocName=en010273) 微控制器，18F2550 的更小、更便宜的版本。18F 系列可以用业余爱好者最喜欢的 [JDM 风格的程序员](http://www.instructables.com/id/Business-Card-PIC-Programmer/)编程，如果[一个二极管被用来](http://www.diylife.com/2008/02/15/program-a-pic-microcontroller/)降低 VPP 到一个安全的水平。PIC 在 [ICSP 编程头](http://www.instructables.com/id/Understanding-ICSP-for-PIC-Microcontrollers/)上有一个去耦电容(C1)、一个二极管(D1)和一个电阻(R1)。我们使用 [MAX RS232 收发器](http://www.maxim-ic.com/quick_view2.cfm/qv_pk/1369) IC 将串行端口暴露在引脚接头上，用于调试或混合 USB/串行端口版本。

USB 外设需要一个 20MHz 外部时钟(Q1 C5，6)和一个 0 . 220 uf 电容。我们使用 2 x .1uF 去耦电容(C2，3)来伪造电容。3 毫米 LED (LED1)和 330 欧姆限流电阻(R2)显示 USB 连接状态。

我们使用 TSOP-1738 红外接收器 IC，它需要一个 4.7uF 去耦电容(C4)。如果您找不到这个特定的 IC，[这里列出的任何接收器](http://www.lirc.org/receivers.html)都应该可以工作。TSOP-1738 的输出是接收信号的反相，当检测到脉冲时，它拉至地，因此当没有信号时，上拉电阻(R3)保持引脚为高电平。检查如果您使用不同的接收器，您可能需要使用下拉电阻，并在固件中反转曼彻斯特解码程序。

该电路从 USB 总线获取电源，因此我们不需要额外的电源。

*零件清单*

![](img/427285ff2b7623ed7c8004a87085272b.png "brd")

[点击此处查看全尺寸摆放图](http://hackaday.com/files/2008/10/brd-large.png) (png)。*PCB 设计 100%通孔单面。原理图和 PCB 是用 [Cadsoft Eagle](http://www.cadsoft.de) 制作的，大多数平台都有免费版本。所有文件都包含在[项目档案](http://hosted.hackaday.com/USBIRr.v1a.zip) (zip)中。*

 *| **部分** | **描述** |
| IC1 | [PIC 18f 2455](http://www.mouser.com/Search/ProductDetail.aspx?qs=W2ndVjZwIIJcNNcdKyvBpg%3d%3d) |
| — | [28 针. 300 插座](http://www.mouser.com/Search/ProductDetail.aspx?R=571-1-390261-9) |
| C1，2，3 | [0.1uF 电容](http://www.mouser.com/Search/ProductDetail.aspx?qs=9AX3phJxokWIpR5WRGtIJw%3d%3d) |
| C4 | [4.7uF 电容](http://www.mouser.com/Search/ProductDetail.aspx?qs=uVOgrT8JCzAhqeVLfh7brw==) |
| C5，6 | [27pF 电容](http://www.mouser.com/Search/ProductDetail.aspx?qs=MQgq2qvN%2feSRs7vKBDt0OA%3d%3d) ( [15pF](http://www.mouser.com/Search/ProductDetail.aspx?qs=x3u4YJAyqD7XMSE5%2fJr6lg%3d%3d) 可能更好) |
| D1 | [1N4181 二极管](http://www.mouser.com/Search/ProductDetail.aspx?qs=TNTIDjy6APqozHdyHHFUGA%3d%3d) |
| Q1 | [20MHz 晶体](http://www.mouser.com/Search/ProductDetail.aspx?R=ECS-200-S-1Xvirtualkey59070000virtualkey520-HCA2000-SX) |
| R1，3 | [10K 欧姆电阻](http://www.mouser.com/Search/ProductDetail.aspx?qs=IP4CA2YhK0BxnZulBOfonw%3d%3d) |
| R2 | [330 欧姆电阻](http://www.mouser.com/Search/ProductDetail.aspx?qs=ULgY8XwKjTmmv2gtdH4CoQ%3d%3d) |
| TSOP | TSOP1738(过时，试用 [TSOP1138](http://www.mouser.com/Search/ProductDetail.aspx?qs=oNDV51lhjEM7P54c1MlVIg%3d%3d) ) |
| USB | [USB‘B’插头，母](http://www.mouser.com/Search/ProductDetail.aspx?qs=N76qWb2E9MJwqgFT2KIWcQ%3d%3d) |
| 见 | [.1”引脚接头](http://www.mouser.com/Search/ProductDetail.aspx?R=4-103329-0virtualkey57100000virtualkey571-41033290) |
| ICSP | [.1”引脚接头](http://www.mouser.com/Search/ProductDetail.aspx?R=4-103329-0virtualkey57100000virtualkey571-41033290) |

![](img/ffce78f4ef1ca374be761e85b4f1af17.png "render")

**固件**

固件是用微芯片的免费演示 [C18 编译器](http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=1406&dDocName=en010014)用 C 写的。固件和源代码包含在[项目档案](http://hosted.hackaday.com/USBIRr.v1a.zip) (zip)中。

我们使用 Microchip 的 USB 堆栈 2.3 版本创建了一个 USB 串行端口，它使用了大多数系统上已有的默认驱动程序。USB 堆栈具有简单的功能来枚举 USB 设备并在设备和主机之间传输数据。只需更改几个引脚，CDC 演示就能在我们的定制硬件上运行。

我们对 UIR/IRMAN/IRA/ctin fra/Hollywood+协议的实现只是用“OK”来响应字母“R”。这应该满足该协议的任何实现的握手要求。

我们选择专门解码 RC5(和 RC5x ),因为它是一种广泛使用的协议，也是我们必须使用的唯一一种遥控器。大部分解码是在中断处理程序中完成的:

*   第一个信号变化触发一个中断，启动一个 889us(半位周期)定时器。
*   每次定时器中断时，曼彻斯特编码位的一半被采样。
*   每隔一个中断，测量值就会进行比较，位值被计算为 0、1 或错误。错误重置解码路由。
*   每次传输结束时，地址和命令字节被解码，并与 4 个缓冲字节(0)一起发送给主机。我们丢弃了切换位，因为它会使 PC 软件误认为每隔一次按下都是一个唯一的代码。我们将第二个起始位附加到命令位，以符合 RC5x 标准；这只是将 0x40 添加到非 RC5x 远程代码中。

通过去除曼彻斯特编码步骤(3 ),并向计算机发送 48 个样本比特(全部 6 个字节),可以得到更一般的版本。

**安装 USB 红外接收器**

大多数操作系统已经有支持虚拟串行端口设备(如接收器)的驱动程序。Windows XP 有所需的驱动程序，但需要。inf 文件来正确地将它们与我们的设备关联起来。

第一次插入接收器时，Windows 会显示新硬件对话框。选择使用自定义驱动程序并将其指向。包含在[项目档案](http://hosted.hackaday.com/USBIRr.v1a.zip) (zip)中的 inf 文件。这将设备链接到 Windows 中已经包含的驱动程序，并将接收器添加为 COM 端口。您可以在控制面板中检查 COM 端口号。

Mac 和 Linux 用户可以使用 LIRC 的接收器，但 Windows 用户将面临选择旧的免费软件梁，或新的 30 天试用版共享软件。我们使用免费版本的大梁，但希望你们能提出一个伟大的，开源的替代方案，我们忽略了。

![](img/939388b905ca89b4a61057fe500afa7b.png "girder")

无论您使用哪种计算机端控制软件，请将其配置为 UIR/IRMAN/IRA/CTInfra/Hollywood+风格的接收器，并输入分配给它的 COM 端口或串行地址。我们的接收器还兼容任何协议选项，如“快速 UIR 初始化”和“跳过 UIR 初始化检查”，缩短或消除“IR”->“OK”握手。现在测试接收器，并根据软件文档添加遥控器。

**手动终端接口和调试**

如果您对接收器有问题，或者您只是好奇，请尝试从串行终端连接它。我们真的很喜欢[大力神](http://www.hw-group.com/products/hercules/index_en.html)上的串行终端。设置正确的 COM 端口，但是速度和配置设置被 USB 串行端口驱动程序忽略。

![](img/169eb3fc241964aa240030acfa9e3dc9.png "hercu")

大写的“R”将提示接收者回复“OK”。RC5 代码作为原始字节返回，所以一定要设置您的终端显示十六进制值，而不是将其解释为 [ASCII](http://www.mahalo.com/ASCII "ASCII - Mahalo") 文本。第一个字节是 RC5 地址字节(0x1E)，随后是命令字节(0x41)，然后是四个缓冲器 0，以符合 UIR/IRman 协议。该图显示了握手，以及短按 1、2 和 3 按钮的输出。

![](img/a90097e66268f2ba9e99e3fcadc9344b.png "portmon-irman")

一个名为 [Portmon](http://technet.microsoft.com/en-us/sysinternals/bb896644.aspx) 的免费工具记录 COM 端口活动以供查看。这有助于监视现有的接收器协议，并调试我们的定制硬件和封闭/专有软件的交互。该图像显示，大梁发送初始化字符串“IR”(0x 49，0x52)，接收器回复“OK”(0x4F，0x4B)。

**更进一步**

我们的 RC5x 兼容接收机遵循广泛使用的接口协议。开源红外接收器的附加功能有很多可能性:

*   通过通用哈希生成器支持所有远程，就像最初的 UIR/伊尔曼硬件一样。
*   添加额外的远程协议解码器，如 [RC6](http://www.sbprojects.com/knowledge/ir/rc6.htm) 。
*   支持多个可配置的接口协议。
*   实现串行端口 I/O
*   在 EEPROM 中存储配置选项，包括协议、接口模式、时序选项、串口等。

![](img/ca5536ef6245f2fcc4804017e3dfc2e3.png "ird")*