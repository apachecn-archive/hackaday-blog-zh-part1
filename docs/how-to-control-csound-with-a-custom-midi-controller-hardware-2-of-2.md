# 如何使用自定义 Midi 控制器控制 Csound:硬件(第 2 页，共 2 页)

> 原文：<https://hackaday.com/2005/08/30/how-to-control-csound-with-a-custom-midi-controller-hardware-2-of-2/>

在上周的文章中，我们向[展示了如何开始使用 Csound](http://www.engadget.com/entry/1234000027055663/) 。本周我们将它带入下一步，构建一个自制的 MIDI 控制器电路，并使用新设备实时控制 Csound。

你需要的东西:
一台装有 [Csound](http://www.csounds.com/) 的电脑
一个用于你电脑的 midi 适配器(usb 转 MIDI 适配器在这里很常见)
一个微控制器/试验板/微控制器编程器(在这个例子中我们将展示一些 BX24 样本代码)
一个 MIDI 母连接器(电缆或电路板安装型，也称为 5 针 din)
一个 [2N2222](http://jameco.com/webapp/wcs/stores/servlet/ProductDisplay?langId=-1&storeId=10001&catalogId=10001&productId=38236) NPN 晶体管
一些电阻(10Kohm 和 2

## 电路

首先，我们将从编写一个微控制器来获取传感器数据开始。在这种情况下，我们使用了来自 [BasicX](http://www.basicx.com/) 的 [BX24 微控制器](http://www.basicx.com/Products/BX-24/bx24main.htm)。你可以选择使用 Atmel 或 PIC 微控制器，PIC 上 MIDI 的优秀指令可以在 [Tom Igoe 的物理计算页面](http://tigoe.net/pcomp/index.shtml)找到。

根据电路图将您的微控制器连接到电源和地线。现在，您将向电路中添加 MIDI 电路。为此，你需要 2N2222 晶体管。抓住晶体管的腿，使拉环面向你，晶体管的引脚排列是:C、B、E 或集电极、基极、发射极。

![pnp](img/f287785c09cf094ef71e2f3a9c9a20b8.png)

在您的试验板上，按如下方式连接 midi 电路:集电极连接到一个 220 欧姆的电阻，该电阻连接到 MIDI 母连接器背面左起的第二个引脚(标记为引脚 5)。基极连接到 10K 欧姆电阻器，该电阻器连接到微控制器的串行数据输出引脚(我们的引脚是 1 aka TX aka 左上角的引脚)。发射极接地。现在，将母 midi 连接器上的中间引脚(引脚 2)接地。在 MIDI 母连接器的第二个引脚(引脚 4)上放置一个 220 欧姆的电阻。将 220 欧姆电阻连接到试验板上的+5V。

![circuit](img/3dcd828276fc2c9d6031db4739df2212.png)

此图显示了带有试验板和微控制器的 MIDI 电路:

![midicircuit](img/fd2abca6ab4881db98f0c66e5a26f1e0.png)

现在连接你的传感器。在我们的例子中，我们将把两个连续的控制器(想想:发送连续数据的东西，而不是发送开/关的开关)连接到我们的微控制器。在引脚 15(从右下数第三个)上，我们连接了一个电位计。在引脚 14(右下方第二个)上，我们选择放置一个弯曲传感器。请注意此图中底部的 MIDI 连接器和微控制器底部右侧的两个连续控制器:

![circuitdiagram](img/3be2c1f5875130ab229f95a05dbf7a4a.png)

这两个连续的控制器现在需要一些代码来获取它们的数据并通过 MIDI 发送。BX24 是用 Basic 编程的，使用的是 BasicX 的免费软件。打开编程环境并打开代码编辑器。下面是我们从两个连续控制器获取数据的代码:

`Option Explicit`

基本传感器到 MIDI 示例
' Fabienne Serriere
' www . engadget . com
'随意复制、调整、传递、使用和重复使用
'引脚 15 上的电位计，引脚 14 上的弯曲传感器

dim outputBuffer(1 到 13)作为字节
dim inputBuffer(1 到 10)作为字节

将音符设为字节
将音高设为字节
将力度设为字节

将电位计调整为整数
将挠性调整为整数

副总管()

启动输入输出缓冲区
调用 openQueue(outputBuffer，13)
调用 openQueue(inputBuffer，10)

调用 openCom(1，9600，inputBuffer，output buffer)
register . ubrr = 14

难道
pot = getadc(15)8
flex = getadc(14)8
从管脚 15 和 14 抓取模拟到数字数据

调试。Print " pot =CStr(pot)'取消注释以查看 bx 环境
'调试中的 pot 值。Print " flex =CStr(flex)'取消注释以在 bx 环境中查看 flex 值

note = 144 '通道 1 上音符的 MIDI 命令
pitch = cByte(pot)'从 pot 值获取音高
velocity = 64 '音符被击打的力度
调用 putQueue(outputBuffer，note，1)
调用 putQueue(outputBuffer，pitch，1)
调用 putQueue(outputBuffer，velocity，1)

“音符= 145”用于通道 2 音符的 MIDI 命令
pitch = cByte(flex)‘从 pot 值获取音高
velocity = 64’`how hard the note is struck` `call putQueue(outputBuffer, note, 1)
call putQueue(outputBuffer, pitch, 1)
call putQueue(outputBuffer, velocity, 1)`

delay(1.0)
note = 144 '用于通道 1 上音符的 MIDI 命令
pitch = cByte(pot)'来自引脚 15 上电位计的值
velocity = 0 '值为零时停止音符开始高于
call putQueue(outputBuffer，note，1)
call put queue(output buffer，pitch，1)
call put queue(output buffer，velocity，1)

note = 145 '用于通道 2 上音符的 MIDI 命令'
pitch = cByte(flex)'来自引脚 14 上的 flex 传感器的值
velocity = 0 '值为零会停止音符从上方开始
调用 putQueue(outputBuffer，note，1)
调用 putQueue(outputBuffer，pitch，1)
调用 putQueue(outputBuffer，velocity，1)

循环
结束接头

如果您想在编程环境中直接测试控制器，可以取消调试注释。通过删除行首的撇号来打印行。请注意，该代码仅适用于 BasicX 环境，如果您使用的是另一种类型的控制器，则必须对其进行修改。PIC 微控制器和 MIDI 的一个很好的资源是 Tom Igoe 的物理计算页面。

现在，使用以下命令将新电路连接到电脑上的 midi 适配器