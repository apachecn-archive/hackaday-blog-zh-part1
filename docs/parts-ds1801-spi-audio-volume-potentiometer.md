# 器件:DS1801 SPI 音频音量电位计

> 原文：<https://hackaday.com/2009/03/16/parts-ds1801-spi-audio-volume-potentiometer/>

![ds1801](img/af39cb31d7b95e564f9d55c92d23fdfc.png "ds1801")

Dallas/Maxim 的 [DS1801](http://www.maxim-ic.com/quick_view2.cfm/qv_pk/2777) 是一个音量[电位器](http://en.wikipedia.org/wiki/Potentiometer)，带有简单的 [SPI](http://en.wikipedia.org/wiki/Serial_Peripheral_Interface_Bus) 接口。这种芯片有两个音量控制通道，在 DIY 音频项目中可能会很有用。我们之前研究过 [DS1807](http://hackaday.com/2009/02/16/parts-i2c-audio-volume-potentiometer-ds1807/) ，这是一款类似的器件，具有 I2C 接口。本周我们将向您展示如何使用 SPI 版本。

**[DS1801](http://www.maxim-ic.com/quick_view2.cfm/qv_pk/2777) SPI 数字音频音量电位器( [Digikey 搜索](http://search.digikey.com/scripts/DkSearch/dksus.dll?lang=en&site=US&keywords=ds1801&x=0&y=0)、 [Octopart 搜索](http://octopart.com/search?q=ds1801)、$6.50)。[数据表](http://www.maxim-ic.com/quick_view2.cfm/qv_pk/2777) (PDF)。**

| **公交海盗** | **DS1801 (pin #)** |
| GND | GND (1) |
| 去吧 | RST (3) |
| GND | ZCEN (4) |
| GND | AGND (11) |
| MOSI | D (12) |
| 时钟 | CLK (13) |
| +3.3 伏 | VCC (14) |

我们将 DS1801 连接到我们的[总线盗版通用串行接口工具](http://hackaday.com/the-bus-pirate-universal-serial-interface/)，如表中所示。我们使用了 Bus Pirate 来演示这个芯片，但是相同的基本程序适用于任何微控制器。DS1801 的电源要求非常灵活，它可以在 3.3 伏或 5 伏下工作，我们使用的是 3.3 伏电源。

DS1801 有一个 SPI 接口。数据输出引脚可以用来级联多个 DS1801s。我们使用带有默认选项的总线盗版 SPI 模式与该芯片接口。

**![1801-spi](img/efbecde055f6a253d597869cc5f9134c.png "1801-spi")**

数据手册第 4 页的图(a)描述了 DS1801 SPI 协议(如上所示)。注意，SPI 使能信号在 DS1801 上称为 RST，实际上与标准符号相反。RST 高时数据输入有效，低时无效。

每个 DS1801 有两个音频电位计，64 步音量控制。0 是全音量，63 是最低音量，位置 64 是静音。设置音量真的很简单；只需提高 RST 信号，时钟在每个电位计的音量水平，并降低 RST 颁布新的设置。

> SPI>A 64 64 a
> AUX 高**<–RST 引脚高**
> 写:0x 40**<–静音设置通道 0**
> 写:0x 40**<–静音设置通道 1**
> AUX 低**<–RST 引脚低**
> SPI >

这里，我们将两个电位计都设置为静音(64)。首先，将 rst 引脚升高到 3.3 伏(大写‘A’，[傻 CSS](http://www.w3.org/TR/CSS2/text.html#caps-prop) )。接下来，写下每个(64 64)的静音设置。最后，降低 RST 引脚制定新的设置(小' a ')。

> SPI>A 0 0 a
> AUX 高电平
> 写:0x00
> 写:0x00
> AUX 低电平
> SPI >

现在，我们通过向两个电位计分别写入 0，将两个电位计都切换到最大音量。将电阻设定为 0，即输入音量的 100%。

> SPI>A 0 64 a
> AUX 高电平
> 写:0x00
> 写:0x40
> AUX 低电平
> SPI >

最后，我们在每个电位计上设置不同的音量。电位计 0 处于最大音量(0)，电位计 1 静音(64)。

喜欢这个帖子？查看您可能错过的[部分帖子](http://hackaday.com/category/parts/)。想申请一个职位吗？请在评论中留下你的建议。