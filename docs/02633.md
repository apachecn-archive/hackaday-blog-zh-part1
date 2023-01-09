# 如何从《时尚先生》杂志制作电子纸时钟

> 原文：<https://hackaday.com/2008/10/14/how-to-make-an-e-paper-clock-and-hack-esquire-magazine/>

![](img/a6d7df22d434b1df2c768654a5da6eeb.png "final-clock-450")

如果你从未听说过电子纸，从那块石头下爬出来，阅读索尼阅读器和 T2 亚马逊 Kindle 阅读器。电子纸是一种柔性显示器，由变色珠子制成，模仿纸上的墨水，便于白天阅读。电子纸的革命性之处在于，它被设定后，无需额外的电力就能保持原样。

这在理论上听起来很棒，但是《时尚先生》的封面是第一次每个人都有能力破解电子纸显示器。我们带着这个封面进入 Hack a Day 实验室进行记录、测试和破解。最后，我们把它回收成任何人都可以制造的有用的东西。我们已经详细了解了该显示器的工作原理，以及在您自己的项目中如何使用它。阅读下面我们的电子纸时钟黑客。

**背景**

![](img/51d4ce94f168758782fb91aa71cff4b5.png "esquire_cover")

《时尚先生》的电子版封面在网上大受欢迎，但很快就遭到了批评。NOTCOT 拥有漂亮的电路板和电子纸的[扫描。《大众科学》贴出了](http://www.notcot.com/archives/2008/09/dissecting_esqu.php)[用拨片读取代码的说明。[Slaxter]](http://www.popsci.com/diy/article/2008-09/hacking-esquire-e-ink-cover-update) [验证 PIC 芯片可以被读取](http://mybitbox.com/view.php?p=11)，并且代码保护保险丝关闭。[Matt]用[熟练的焊接和 Arduino](http://antipastohw.blogspot.com/2008/10/hacking-esquire-cover-e-ink-screen-with.html) 直接操纵电子纸电池。到目前为止，人们对改变电子纸的用途或重新编程现有的微控制器没有太多兴趣。

**电子纸面板**

![](img/f5b71e614fccd6a7f3c205715bb5679e.png "panel-bare-450")

由 E-Ink 制造的真正的电子纸面板并不令人兴奋。每个面板都有一组预定义的部分，11 个在前面板上，3 个在后面的福特广告上。这不是一个我们可以重新编程为电子阅读器的矩阵。[just_mike]有一组很棒的[超特写镜头，拍摄组成每个片段的单个珠子](http://flickr.com/photos/just_mike/2833061896/in/set-72157607133868125/)。

![](img/6bbaeccb2b2e548a83fb8513a26190ba.png "eink1")

每个电子纸段都有一个单独的连接，以及一个与面板上其他单元共享的连接。根据施加到单元上的电流方向，段变成白色或黑色。当 common 为低电平时，任何连接为高电平的段都会变暗。当 common 为高电平时，每个接地单元将清零。PCB 使用五节 3.3 伏电池中的 16 伏电压来切换电池，但[Slaxter]表明 5 伏电压对他的 Arduino 项目来说已经足够了。

*性能测试*
我们对电子纸的操作规范做了几点观察。

[https://www.youtube.com/embed/T6GTFvNjRCk?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/T6GTFvNjRCk?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

首先，完全变暗或清除一个单元需要将近 0.5 秒。在视频中，你可以看到电子纸切换过快造成的部分状态。我们不太确定最佳的更换时间，但 0.25 到 0.5 秒之间似乎是最短的。

这也提出了关于最大改变时间的问题。施加电流超过必要时间会损坏电子纸吗？只要使用电子纸，它会继续消耗电流，浪费电池吗？在代码中，我们特别注意在发生变化后将所有输出返回到地，以避免持续电流流过面板。

[https://www.youtube.com/embed/hix9-h5UuSc?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/hix9-h5UuSc?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

清除和变暗必须分开进行。完全刷新屏幕需要两次完整的操作；一个用于清除旧段，一个用于使新段变暗。一个聪明的程序员会认为，当只添加或删除项目，而不是两者都做时，他们可以节省一个周期。这在某种程度上是正确的，但是连续操作一个单元格而不刷新相邻的单元格会导致颜色“蠕动”。在视频中，没有任何其他片段更新的闪烁背景会快速将非活动片段驱动到黑暗和光明之间的中间状态。

**驱动板**

![](img/938c143a76845fee203f62c8701c33fb.png "driver-board")

该驱动器由一个八针微芯片 [PIC12F629](http://www.microchip.com/wwwproducts/Devices.aspx?dDocName=en010113) 、两个 [4094](http://www.nxp.com/#/pip/pip=[pip=HEF4094B_CNV_3]|pp=[t=pip,i=HEF4094B_CNV_3]) [移位寄存器](http://en.wikipedia.org/wiki/Shift_register)和一些配套元件组成。

![](img/b52d4d8ba9fdaeed714bdf0ca8b45597.png "pin-out-illu-450")

[点击此处查看电子纸驱动板](http://hackaday.com/wp-content/uploads/2008/10/pin-out-illu.png) (PNG)的全尺寸引脚图。

*电池*

《绅士》[邀请了他们封面上的黑客](http://www.esquire.com/the-side/video/hacking-the-e-ink-cover),提出了一个相当蹩脚的更换电池的建议。这是有道理的，封面是[用冷藏集装箱](http://www.esquire.com/features/how-e-ink-was-made)运送到世界各地，以帮助延长电池寿命。即便如此，Esquire 说电池还能坚持几个月。

电池 1-5 是串联的，为电子纸提供 15-16 伏的开关电流。第六节电池为 PIC 提供 3 伏电压。目前还不知道哪种电池会先耗尽。如果你想“替换”你的电池，你需要将旧电池脱焊，并在指定点提供 5-16 伏的电子纸电源和 3 伏的微控制器电源。

![](img/52327de5cf32de936c571274c8f7c57e.png "final-clock-450-new-bat-narrow")

我们最终不得不更换我们的微控制器电池，因为我们在开发过程中滥用了它。具有 20 毫米针间距的钮扣电池座将适合现有的孔。Mouser # [534-106](http://www.mouser.com/Search/ProductDetail.aspx?qs=Q3RoVmURDolnMuconA2vXg%3d%3d) 可能会起作用，但这未经证实。

*4094 移位寄存器(IC1，IC2)*

移位寄存器在 16 伏下切换电子纸段控制。

![](img/e9564d5cb44a1e28fee32e2042680132.png "4094b1")
两个 4094 ICs 是移位寄存器，用于将数据从 IC1 级联到 IC2。这个简单的移位寄存器是我们在[涂鸦墙](http://hackaday.com/2008/10/02/how-to-networked-graffiti-wall/)中使用的 74HTC595 的一个微小变化。主要区别在于，4094 选通线通常为低电平，并短暂拉高以将新值输入输出引脚。我们注意到 4094 需要长时钟和选通脉冲。这可能是由于 PIC 和 4094 之间的懒惰驱动电路，或者仅仅是 [4000 系列](http://en.wikipedia.org/wiki/4000_series)的性质。

*4094 段输出图*

| **IC** | **输出** | **地址** | **连接** |
| 1 | Q1 | 0x01 | FRONT_BOX_SYMBOL_DNA |
| 1 | Q2 | 0x02 | FRONT_BOX_GUY |
| 1 | Q3 | 0x04 | 前台 _ 包厢 _ 焰火 |
| 1 | Q4 | 0x08 | 西海岸前沿 |
| 1 | Q5 | 0x10 | 前 _ 三 _ 小时 _ 后 |
| 1 | Q6 | 0x20 | FRONT_ESQUIRE |
| 1 | Q7 | 0x40 | FRONT_BOX_GIRL |
| 1 | Q8 | 0x80 | 前方 _ 现在 |
| 2 | Q1 | 0x100 | FRONT_BEGINS |
| 2 | Q2 | 0x200 | 前方 _ 21 世纪 _  |
| 2 | Q3 | 0x400 | 正面 _ 背景 |
| 2 | Q4 | 0x800 | FRONT_COMMON |
| 2 | Q5 | 0x1000 | BACK_COMMON |
| 2 | Q6 | 0x2000 | 背部 _ 左侧 |
| 2 | Q7 | 0x4000 | 后退 _ 居中 |
| 2 | Q8 | 0x8000 | 背部 _ 右侧 |

*12F629*

![](img/b176c205683cdac75b6f5298b9685158.png "cct-4501")

[点击此处查看全尺寸示意图](http://hackaday.com/wp-content/uploads/2008/10/cct-large1.png) (PNG)。一个 8 引脚 PIC12F629 驱动控制每个电子纸段的 4094 个移位寄存器。两个引脚未使用(GP4、GP5)。

MCLR 功能通过电阻 R8 启用。该设计不包括保护 PIC 免受 13 伏编程电流影响的二极管。Microchip 建议这样做，但没有其他敏感 IC 共享该电路，因此设计人员可能认为电阻足以提供保护。

三个引脚驱动 4094 的数据、时钟和选通线(GP0、GP1、GP2)。4094 的接口电压必须与它切换的电压相同，即 16 伏，因此 PIC 通过晶体管切换接口引脚。据我们所知，4094 控制线是用电阻拉高的。PIC 打开一个晶体管，它把线拉到地。*4094 的接口是向后的*。PIC 高电平引脚在移位寄存器处被视为低电平，低电平被视为高电平。除非反过来，否则界面不会起作用。

编程引脚被带到 PCB 顶部的一个接头上。我们将标准的. 1”引脚接头焊接到提供的孔中(Mouser # [571-41033290](http://www.mouser.com/Search/ProductDetail.aspx?R=4-103329-0virtualkey57100000virtualkey571-41033290) )。PGD 和 PGC 这两个编程引脚由驱动移位寄存器的电路共享。我们能够用 ICD2 调试器读取设备。但是我们不能重新编程，可能是因为移位寄存器驱动器的原因。有人成功了吗？无论如何，共享引脚安排使得不可能在该器件上进行在线调试。

*PIC 引脚连接*

| **销** | **名称** | **连接** |
| 1 | VDD | +3.3 伏 |
| 2 | GP5 | — |
| 3 | GP4 | — |
| 4 | GP3 | MCLR(节目 VPP) |
| 5 | GP2 | 4094 频闪 |
| 6 | GP1 | 4094 时钟(程序时钟) |
| 7 | GP0 | 4094 数据(程序数据) |
| 8 | VSS | 接地 |

**轻敲板子**

![](img/754a31eb1492ac8cf84a1d55b0c51635.png "tap-board2")

很容易接入电路板，并与您喜欢的微控制器配合使用。除了一个需要的接口信号之外，所有需要的接口信号都已经被带到头部。可以通过箭头所示的通孔分接选通线。您不希望 PIC 干扰您的新控制器，所以请通过切断电源引脚将其移除或停用。

**接口库**

![](img/a94c8d8df5e686204c510312fdcb59f8.png "debug-with-wsbc1")

我们第一次驱动电路板的努力涉及到我们基于 PIC24F 的迷你网络服务器 T3。它很方便，PIC24F 很容易使用。我们在低功耗 MSP430 上完善了我们的接口库。两个版本都在[项目档案](http://blog.mahalo.com/hackaday/howto/esquire.epaper.clock.v1.zip) (ZIP)中，但是 MSP430 版本的库更成熟。

该库包括一个软件 [bit-bang](http://en.wikipedia.org/wiki/Bit-banging) 例程、用于连接电路板的函数以及段和公共线的地址定义。esquire_eink.h 中的选项启用位爆炸延迟并设置其长度；我们发现 4094 很懒，需要很长的时钟脉冲。initBang()函数设置引脚的方向，应该根据您的微控制器进行更改。调用它，或者将您的 IO 引脚设置为在其他地方输出:

```

bangInit(); //set bitbang pins to output

```

函数的作用是:将传递的线段设置为暗(1)或明(0):

```

setSeg(FRONT_BOX_GUY+FRONT_BACKGROUND, 1); //set(dark) these segments
setSeg(FRONT_21ST_CENTURY,0);//clear (light) these segments

```

setSeg()函数包含一个由 esquire_eink.h 中的 EINK_DELAY 定义的颜色变化延迟，在延迟结束时，它会将移位寄存器引脚返回到地。我们希望避免损坏电子纸或浪费电池，尽管我们不知道这是否有必要。

关于 setSeg()我们注意到的一件事是，操作单个单元格会导致相邻的单元格向中间色倒退。我们开发了 setDisplay()函数，通过每次完全刷新显示来解决这个问题。setDisplay()包含每次变化的暂停，然后将移位寄存器输出返回到地。只需通过段排列即可获得完全刷新的显示:

```

setDisplay(FRONT_ESQUIRE+BACK_LEFT);//XX dark, everything else clear

```

您可以使用 bangIt()函数直接访问移位寄存器，但要考虑在电子纸颜色变化完成后将移位寄存器输出恢复为“0”。如果你让它开着，你可能会损坏电子纸或导致过量的电流消耗，如果那真的是“一件事”的话。

```

bangIt(0b1110000000000000);//all back panel segments on
pause();//wait for the color change
bangIt(0x0000);//return all outputs to ground

```

要将库移植到微控制器，只需检查 esquire_eink.h 中的引脚配置和 esquire_eink.c 中的引脚设置函数 bangInit()，请记住，接口晶体管会反转引脚方向。

**投入使用，一个电子纸时钟**

[https://www.youtube.com/embed/kluFFU90qnI?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/kluFFU90qnI?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

我们想用第一个廉价的消费者电子纸面板做一些有用的事情。它必须非常简单，这样很多人才能回收这项很酷的技术。我们忍不住做了很多人用旧显示技术做的事情:做一个时钟。原理图、固件和艺术模板都在[项目档案](http://blog.mahalo.com/hackaday/howto/esquire.epaper.clock.v1.zip)(。zip)。

![](img/81ddce7d4c8378ff95da16f16105bac0.png "bezel-export")

电子纸上的片段很少，我们只能部分地表示时间。六段显示时间，每一段逐渐变淡，以显示过去 10 分钟的时间。我们也在面板的非时间段上闪烁眼睛糖果。这是我们创建的定制边框。这个边框，以及一个你自己制作的模板，包含在[项目档案](http://blog.mahalo.com/hackaday/howto/esquire.epaper.clock.v1.zip) (ZIP)中。我们印刷了镜面边框，防止墨水被划伤。

*硬件*

*我们受到电子纸低功耗特性的启发，使用了[德州仪器的 MSP430 系列 16 位微控制器](http://focus.ti.com/mcu/docs/mcuprodoverview.tsp?sectionId=95&tabId=140&familyId=342)。通过正确的配置，MSP430 的功耗非常低，仅受电池寿命的限制。我们甚至可以给最初的设计者一个机会，看看我们是否能制造一个低功耗的设备。*

 *MSP430 最好的一点是，你可以只花 20 美元购买一套带有 [USB 编程器/调试器和分线板的套件。它配有](http://www.ti-estore.com/)[一个仅限于 4K](http://focus.ti.com/docs/toolsw/folders/print/iar-kickstart.html) 的免费 C 编译器，但 F2013 只有 2K 内存。这是一个完整的开发工具，不涉及焊接。在本指南中，了解更多关于[使用 MSP430 的信息。](http://www.diylife.com/2008/03/28/program-a-msp430-microcontroller/)

![](img/84a312ccc1a7d9a617259e310ac2aeca.png "msp430-cct-4501")

该原理图显示了我们如何将 MSP430 连接到电子纸驱动板。[点击此处查看全尺寸版本](http://hackaday.com/wp-content/uploads/2008/10/mps430-cct-large2.png) (PNG)。分线板上包括 47K 电阻、MSP430 和 LED(未显示)。

我们增加了一个 32.768 千赫的晶体来保持时间(Q1)。通常，我们还会添加一些电容来形成振荡器，但 MSP430 在 P2.6 和 P2.7 上内置了可调电容。

我们还在 P1.4 和 P1.2 (S1)之间增加了一个[按钮](http://hackaday.com/2008/09/15/tact-switches-for-your-next-project/)。P1.4 上的内部[上拉电阻](http://en.wikipedia.org/wiki/Pull-up_resistor)使按钮保持高电平，我们通过 P1.2 将其接地。这不是最佳安排，将 P1.2 也接地可能是明智的。

![](img/63170ba4e32ba78009b1d7bd46b2cb9f.png "msp430-connections")

我们将 MSP430 分线板滑过编程接头的电源和接地引脚。您也可以将时钟和数据引脚连接到接头，但我们决定从下方的过孔布线。记得移除 PIC，以免干扰来自 MSP430 的信号。

| **零件** | **数量** | **成本** |
| Esquire 电子纸封面 | — | — |
| MSP430 ez430 开发套件 | [USB](http://www.ti-estore.com/)T3 | $20 |
| 32.768KHz 晶体 | 815-ab26t-32.768kT3 | $0.27 |
| 按钮 | [642-mjtp1250](http://www.mouser.com/Search/ProductDetail.aspx?R=MJTP1250virtualkey64200000virtualkey642-MJTP1250) | $0.16 |

*固件*

时钟软件是用 ez430 编程器附带的 TI/IAR Kickstart C 编译器的免费演示版编写的。

MSP430 的功耗非常低。它在 1MHz 时仅使用 220uA，但在睡眠时不到 6uA。电池续航时间长的关键是尽可能让芯片休眠。我们编写时钟代码时考虑到了这一点。

我们使用 32.768khz 晶振的 timer_a 每秒产生两次中断。第一个中断触发配置要显示的段的代码，将这些值发送到电子纸，然后在接下来的 0.5 秒内休眠。当 MSP430 休眠时，所有“关闭”段都有时间清除。下一个中断通过简单的 [XOR](http://www.somacon.com/p125.php) 将公共线反向翻转，输出值，然后再休眠 0.5 秒。下一次循环将再次开始。我们不用费心将移位寄存器复位到“0”位置，因为刷新是不断变化的。段蠕动不是问题，因为我们每个周期都刷新每个段。

按下按钮触发中断，将时间推进到下一个 10 分钟。要设置时钟，请等待时间超过整点 10 分钟，然后按按钮显示正确的时间。一个小的去抖动例程确保每次按下按钮只检测到一次点击。

**更进一步**

关于电子纸面板，有一些挥之不去的问题很好回答。什么是最佳的改变时间？持续的电流会损坏分段还是浪费电池电量？为什么设计者只需要 5 伏电压，却要用整整 16 伏电压来触发面板？

构建时钟和连接 Esquire 封面所需的一切都包含在[项目档案](http://blog.mahalo.com/hackaday/howto/esquire.epaper.clock.v1.zip) (ZIP)中。应该可以使用接口库和三个 IO 引脚将任何微控制器与 Esquire 电子纸封面接口。在未来的项目中，我们计划为未使用的电子纸模块构建一个自定义驱动板。

![](img/be8ffb5dc43300ab3e36d03a04f59b4c.png "final-clock-450-old-bat")*