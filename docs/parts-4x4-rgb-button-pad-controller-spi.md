# 器件:4×4 RGB 按钮板控制器 SPI

> 原文：<https://hackaday.com/2009/03/09/parts-4x4-rgb-button-pad-controller-spi/>

![cover](img/c1331405e708d0361c2c3b1d97066743.png "cover")

几周前我们报道了 SparkFun 的新 [RGB 按钮板控制器](http://hackaday.com/2009/02/05/sparkfun-releases-rgb-button-controller/)。这是[单体](http://monome.org/)界面的全彩克隆；一个 4×4 的按钮网格，下面是三色 led。每个 LED 有[24 位颜色控制](http://en.wikipedia.org/wiki/Truecolor)，超过 1600 万种颜色组合。多达 10 个面板可以链接在一起，创建巨大的按钮网格，就像 [SparkFun 的俄罗斯方块表](http://www.youtube.com/watch?v=G9RPLtAvXlE)。我们之前在我们的 [RGB 密码锁](http://hackaday.com/2008/06/12/how-to-make-an-rgb-combination-door-lock-part-1/)中使用了一个较小的版本。

我们要求 SparkFun 将 SPI 版本的按钮控制器发送给我们进行测试。这是 SparkFun 内部开发的新产品，具有开源硬件和软件。请在下面阅读我们与此板交互的经验。

**4×4 RGB 按钮板控制器 SPI (SparkFun # [WIG-09022](http://www.sparkfun.com/commerce/product_info.php?products_id=9022) ，$39.95)**

按键板控制器是一个裸露的 PCB，我们还收到了一个按键板盖(SparkFun # [COM-07835](http://www.sparkfun.com/commerce/product_info.php?products_id=7835) ，9.95 美元)，以及每个挡板两个(SparkFun # [COM-08747](http://www.sparkfun.com/commerce/product_info.php?products_id=8747) ，# [COM-08746](http://www.sparkfun.com/commerce/product_info.php?products_id=8746) ，3.95 美元)。我们正在使用的 SPI 版本可以由微控制器或 USB“主机”直接驱动。USB 控制器版本有一个额外的微控制器和 FTDI USB- >串行转换器，用于 PC 连接。

当按钮板到达时，我们立即坐下来看数据手册，并尝试将电路板与我们的[总线盗版通用串行接口](http://hackaday.com/the-bus-pirate-universal-serial-interface/)连接。数据手册版本 1 中描述的协议根本不起作用。

SparkFun 开源了这个项目，所以我们从源代码中为[按钮板 SPI](http://www.sparkfun.com/Code/ButtonPadControllerSPI_v15.zip) (ZIP)和[按钮板 USB 控制器](http://www.sparkfun.com/Code/ButtonPadControllerUSB_v15.zip) (ZIP)确定了正确的接口协议。我们从源头上弄清楚了大部分协议，但仍然需要 SparkFun 工程师的帮助来发现一些未记录的、更好的电路板接口点。[数据表](http://www.sparkfun.com/datasheets/Widgets/ButtonPadControllerSPI_UserGuide_v2.pdf) (PDF)的第 2 版准确描述了接口协议。

*连接*

| **公交海盗** | **按钮垫** |
| 军事情报部门组织(Military Intelligence Service Organization) | 军事情报部门组织(Military Intelligence Service Organization) |
| MOSI | MOSI |
| 时钟 | 血清肌酸激酶 |
| 特许测量员 | 特许测量员 |
| +5 伏 | VCC |
| GND | GND |

按钮板的 SPI 信号与板载微控制器相关，这与通常的符号相反。MOSI(主机输出，从机输入)信号实际上是电路板的数据输出，MISO(主机输入，从机输出)是数据输入。

我们用总线盗版测试了按钮板，但是相同的基本原理适用于任何定制的微控制器代码。该板运行在 5 伏，所以我们从总线海盗的板载 5 伏电源供电。SPI 接口在 5 伏逻辑电平下工作，因此我们将总线盗版的[上拉电阻](http://en.wikipedia.org/wiki/Pull-up_resistor)连接到 5 伏电源，并在所有信号线上启用它们。

我们使用总线盗版的 raw3wire 库连接按钮板。Raw3wire 是一个软件 SPI 库，支持逐位操作。硬件 SPI 库仅允许全字节操作，其粒度不足以与电路板接口。我们将 Bus Pirate 置于 raw3wire 模式(菜单选项 M)，并选择 HiZ 引脚选项，因为上拉电阻会将总线保持在 5v。

> raw 3 wire > l**<–配置位顺序**
> 1。MSB 优先
> 2。LSB 优先
> 模式> 2

 **按钮板首先传输最低有效位，因此我们还配置了库以传输 LSB。最后，我们按下大写字母“W”来启用总线盗版的电源。作为通电自检的一部分，按钮板将短暂闪烁每种颜色。

*单/多按钮板设置*

![config2](img/3e9ab94de98a1d8d1e534c6ca757e25a.png "config2")

每个板都需要配置为单板或多板使用。板预编程为单板操作，但它可能是一个好主意，无论如何设置配置。电路板配置永久存储在 EEPROM 中，因此只需执行一次。

> raw 3 wire >[\ _**<–将所有信号拉低**
> CS ENABLED**<–CS ENABLED 为 0 伏**
> 时钟，0
> 数据输出，0
> RAW3WIRE >

一个特殊的序列将板置于配置模式。从所有信号线为低电平开始(]\_)。

> raw3wire>-^ 1 1**<–设置单板操作**
> 数据输出，1**<–数据高**
> 0x01 时钟滴答**<–一个时钟滴答**
> 写入:0x 01**<–配置选项 1、板数**
> 写入:0x 01**<–设置板数**
> raw 3 wire>w**<–small‘w**

要进入配置模式，将数据线拉高(-)并发送一个时钟脉冲(^)，但*保持芯片选择低电平*。现在，评估板可以接受配置设置了。

进入配置模式后发送的第一个字节告诉板要修改哪个设置。目前，只能配置板的数量(0x01)。接下来，发送连接板的数量，介于 1 和 10 之间。我们发送 1 是因为我们正在连接一个单板。重置电路板，它将根据编程的电路板数量点亮一个 LED。

*设置颜色并读取按钮状态*

现在，我们准备向电路板发送颜色数据，并读取按钮状态。首先，注意 CS(片选)信号与常规相反。通常 CS 在信号低(0 伏)时激活一个芯片，信号高(5 伏)时使其空闲；这通常用/CS、#CS 或！来表示。CS。相反，当 CS 为高电平时，按钮控制器有效。

![frames](img/4ecbc328bde36a571c98ff4fe9c1fd83.png "frames")

一个 64 字节的事务设置 LED 颜色并检索按钮状态。第一个 16 字节为每个 LED 设置红色电平，随后是 16 字节绿色，16 字节蓝色。最后，从板上读取 16 个字节，以获得每个按钮的状态。按钮数据在按下时发送为 0x00，未按下时发送为 0xff。数据手册建议在写入颜色帧和读取按钮数据之间有 400us 的延迟，但总线盗版足够慢，我们不用担心。

![inter](img/e80bfa1c9a0a48083664162cf70d872b.png "inter")

这个协议很简单，但是有一个主要的问题。时钟线 ***在提升 CS 之前必须*** 为高，否则字节流将关闭 1 位。因此，许多硬件 SPI 模块无法与该板配合使用。如果您的微控制器允许您旋转由硬件模块控制的引脚，这不是问题，但是我们与*合作的微控制器不允许这样做。*

![white](img/fb112f4bcda0ed4c02cf688da738ab86.png "white")

> raw 3 wire >/]255:16 255:16 255:16 r:16[
> CLOCK，1**<–CLOCK*必须*为高电平才能提升 CS**
> CS 禁用**<–CS 至 5v，相反正常使用**
> 批量写入 0xFF，0x10 次**<–红色 led**
> 批量写入 0xFF，0x10 次**<–绿色 0x10 次**<–蓝色 led**
> 批量读取 0x10 字节:**<–读取按钮状态**–0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff
> CS 使能**<–CS 到 0v，相反正常使用**
> RAW3WIRE >**

该命令将每个 LED 的每种颜色设置为全彩，并读回 16 个按钮状态字节。

我们首先将 clock 设为高电平(/)，然后才能将 CS 升至 5v(])并开始数据处理。255:16 是一个重复的命令，它将值 255 发送 16 次。由于每个颜色通道有 8 位强度控制，255 是 100%打开。我们总共发送了 48 次 255，每个 LED 的每种颜色一次。最后，我们检索一个 16 字节的按钮数据帧(r:16)并降低 CS 以结束事务([)。按钮值都是 0xff，表示没有按钮被按下。

![blue](img/0c70e312f2f501404eee3437908ab34c.png "blue")

> raw 3 wire >/]0:16 0:16 128:16 r:16[
> 时钟，1
> CS 禁用
> 批量写入 0x00，0x10 次
> 批量写入 0x00，0x10 次
> 批量写入 0x80，0x10 次**<–全蓝到 50%**
> 批量读取 0x10 字节:
> 0x 00 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff

这里，我们将每个 LED 的蓝色级别设置为 50% (128)，并关闭所有其他颜色。按钮输出现在显示按钮 0 被按下。

![red](img/79a371c1a5b657d053f8ad73a09b99e8.png "red")

> raw 3 wire >/]0 0 0 0 255 255 255 255 0 0 0 0 0 0:16 0:16 r:16[
> 时钟，1
> CS 禁用
> 写:0x 00**<–红色 LED 0，off**
> …**<–更多相同的**
> 写:0x 00**<–红色 LED 3，off**
> 写:0x ff【T11 100%开
> 写:0x ff**<–红色 LED 6，** **100%** **开**
> 写:0x ff**<–红色 LED 7，** **100%** **开**
> 写:0x 00**<–红色 LED 8，off**
> … **0x10 次**<–所有绿色 LED 熄灭**
> 批量写入 0x00，0x10 次**<–所有蓝色 led 熄灭**
> 批量读取 0x10 字节:**<–读取按钮状态**
> 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff 0x ff
> CS 使能
> RAW3WIRE >**

此示例显示了如何寻址单个 led。这次我们实际上写出了红色帧的所有 16 个字节。按钮 0-3 和 8-15 的红色值为 0(红色关闭)，按钮 4-7 设置为 100%红色(255)。所有绿色和蓝色发光二极管关闭(0，0%)。

*结论*

让该板正常工作确实令人沮丧，因为数据手册的第一版有太多错误。SparkFun 的工程师和支持真的很有帮助，并在几天内发布了一个更正的数据表。只要您有更新的数据手册，这是一个很容易使用的板。

我们希望看到固件更新，不再需要在提高 CS 之前保持时钟信号为高电平。这种怪癖使得该板与许多硬件 SPI 模块不兼容，使得缓慢的 bit-bang 例程成为唯一的接口选项。幸运的是，源代码是开放的，任何想做这种改变的人都可以使用。

按钮板控制器是一个非常整洁的板，我们期待在未来的项目中使用它。

**Hack a Day review disclosure** :我们要求一个免费的板子，SparkFun 发给了我们。我们花了很长时间才让它与第一版数据手册中的说明配合工作，我们在这里记录了这一经历。**