# FTDI Bitbang 模式介绍

> 原文：<https://hackaday.com/2009/09/22/introduction-to-ftdi-bitbang-mode/>

这个界面引发了一千次黑客攻击。对于编程来说几乎微不足道，对于有用的工作来说足够多的 I/O 线，对于大量的应用来说足够快:[自制逻辑分析仪](http://hackaday.com/2008/01/28/parallel-port-logic-analyzer/)、[芯片程序员](http://hackaday.com/2006/11/08/five-dollar-eprom-programmer/)、 [LCD 接口](http://hackaday.com/2005/11/19/hacking-an-lcd/)和 [LED 灯显示](http://hackaday.com/2009/06/08/simple-computer-controlled-lights/)等等。

今天，并行打印机端口正处于消亡的边缘(有人会说，这是一种解脱)。USB 在很大程度上被淘汰了，很少(如果有的话)新的外围设备甚至包括并行连接器，而且今天越来越小的计算机——上网本、媒体中心 PC——无论如何都没有空间容纳它。这对于整洁的桌子来说很好，但如果你喜欢传统并行端口使之成为可能的极便宜的黑客，那就不太好了。

不要害怕，因为有一个可行的 USB 替代品可以复活这些经典的黑客！如果你已经用 Arduino 做了很多工作，很有可能它已经潜伏在你的零件抽屉里了。

在最近的许多黑客攻击中，一个反复出现的元素是使用 Arduino 或其他 USB 连接的微控制器作为 PC 和外部电路之间的中介。运行在微控制器上的代码将轮询一些传感器来检测变化(例如，一个空的咖啡壶)，然后通过 USB 向主机发送消息，另一个程序随后对其进行操作(更新网页以告诉世界没有咖啡了)。这是一种合理的方法，部件价格合理，编程简单，但对于许多项目来说，我们只需要一半的代码、复杂性和费用就可以完成……有些人会很高兴听到，*没有 Arduino！*

当 Arduino 板上的微控制器通过 USB 与主机通信时，所有繁重的 USB 通信工作都由一个单独的芯片完成:FTDI FT232R USB 转串行 UART 接口。这允许主机和微控制器上的代码使用简单得多的异步串行通信。作为一种尺寸和成本削减措施，一些 Arduino 变体将该芯片放在一个单独的板上，只有在对微控制器编程时才连接，允许它在下一个项目中重复使用。

FT232R 的这种默认 USB 转串行模式通常会吸引所有的注意力，吸引所有的女孩。另一种模式是 *bitbang 模式，这种模式很少被提及，但同样有用。*这为我们提供了多达 8 条 I/O 线的独立软件控制，类似于微控制器的经典并行端口或数字 I/O 线。

## 获取硬件

如果你还没有，FT232R 分线板很容易得到。任何销售 Arduino Pro 或 LilyPad 或一些低价 Arduino 衍生产品(如 Boarduino)的商店，还将提供一条编程电缆，可连接四条 FT232R I/O 线:

![Above: The SparkFun FTDI Basic Breakout board (around $14) is surrounded by the FTDI TTL-232R converter cable (around $20). Both bring out four data lines that can be used for general-purpose I/O. There is a one pin difference in that the FTDI cable brings out the RTS pin, while the SparkFun board uses the DTR pin in the same position.](img/791eb9fedd18294d8d4ff66f96075e34.png "basic-breakout")

Above: The SparkFun FTDI Basic Breakout board (around $14) is surrounded by the FTDI TTL-232R converter cable (around $20). Both break out four data lines that can be used for general-purpose I/O. 

四条数据线可能看起来有所限制，但对于许多任务来说，这已经足够了；使用 SPI 通信、移位寄存器和端口扩展器的项目将得到很好的服务。如果您需要完整的 I/O 线路，可以使用更复杂的分线板:

![Above: just a few of the available FTDI breakout boards. Clockwise from top: SparkFun Breakout Board for FT232RL (around $15), Modern Device USB-BUB ($12), DLP Design DLP-USB232R ($18) and DLP-USB1232H ($25), and FTDI’s own FT4232HQ Mini Module ($30). The latter two are based on more capable chips, FTDI’s FT2232H and FT4232H, with additional features far exceeding the scope of this article.](img/cfed4bc0b6368cb7735f59f1b9d8ec8e.png "full-breakout")

Above: just a few of the available full breakout boards. Clockwise from top: SparkFun Breakout Board for FT232RL (around $15), Modern Device USB-BUB ($12), DLP Design DLP-USB232R ($18) and DLP-USB1232H ($25), and FTDI’s own FT4232HQ Mini Module ($30). The latter two are based on more capable chips, the FT2232H and FT4232H, backwardly compatible but with additional features far exceeding the scope of this article.

## 为发展做准备

FTDI 接口的另一个令人鼓舞的方面是跨平台软件支持；无论您使用的是 Windows、Linux 还是 Mac OS X，都可以创建相同的黑客。开始开发需要两个软件组件:一个*设备驱动程序、*，它在后台运行以处理所有低级 USB 通信，以及一个 *API 库、*，它与您自己的代码相链接，并将请求转发给驱动程序。稍微复杂一点的是，有两种不同的 API 可供选择，并且每个操作系统的设置过程都略有不同。

FTDI 自己的 API 叫做 *D2XX。这个库是私有的，并且是封闭源代码的，但是他们对它的使用不收费，即使是在商业场合。另一个 API， *libftdi，*是社区开发的完全开源的。这个库具有相似的功能，但是函数名和语法不同。两个 API 之间的转换非常简单，我们将为每个 API 提供一个例子。*

**Windows 用户:**如果你之前使用过 Arduino，那么已经安装了必要的驱动程序。否则，[从 FTDI 网站](http://www.ftdichip.com/Drivers/D2XX.htm)下载并提取最新的 Windows 驱动程序。第一次连接 FTDI 电缆或分线板时，请使用“找到新硬件向导”来查找并安装驱动程序。如果您想使用 D2XX 库，头文件和目标文件包含在驱动程序文件夹中。这是更容易的选择。如果你更喜欢开源的 libftdi，你需要下载并安装 [libusb-win32 设备驱动和源代码](http://sourceforge.net/projects/libusb-win32/files/)，然后[下载并构建 libftdi](http://www.intra2net.com/en/developer/libftdi/) 。

**Linux 用户:**大多数当前的 Linux 发行版已经将必要的驱动程序作为内核模块提供。Linux 的 D2XX 库可以从 FTDI 驱动页面上[下载，但是](http://www.ftdichip.com/Drivers/D2XX.htm) [libftdi](http://www.intra2net.com/en/developer/libftdi/) 更容易安装:只需在您最喜欢的包管理器中找到 libftdi-dev，让它在安装时处理依赖关系。在这两种情况下，Linux 的 FTDI 程序都需要以 root 用户身份运行，例如

```
sudo ./hello-ftdi
```

**Mac OS X 用户:** [从 FTDI 下载页面](http://www.ftdichip.com/Drivers/D2XX.htm)下载 D2XX 库。附带的自述文件将解释如何安装该库。如果您更喜欢使用 libftdi，请从各自的站点下载 [libusb](http://www.libusb.org/) (遗留 0.1.12 版本)和 [libftdi](http://www.intra2net.com/en/developer/libftdi/) 的源代码，然后在终端窗口中使用以下命令来构建和安装这两个库:

```
./configure
make
sudo make install
```

如果你过去使用过 Arduino，或者因为其他原因安装了 FTDI 虚拟 Com 端口(VCP)驱动程序，那么在 bitbang 模式在 Mac 上工作之前，需要将其禁用；这两者不能共存。在终端窗口中，键入:

```
sudo kextunload /System/Library/Extensions/FTDIUSBSerialDriver.kext
```

要恢复驱动程序并继续使用 Arduino 或其他 FTDI 串行设备:

```
sudo kextload /System/Library/Extensions/FTDIUSBSerialDriver.kext
```

**其他操作系统:**其他几个平台的驱动都有。详情和链接请见 [FTDI 驱动页面](http://www.ftdichip.com/FTDrivers.htm)。

大多数 FTDI 示例代码都是用 C 编写的，这就是我们在这里要使用的。FTDI 网站上提供了其他语言的绑定。

## Hello World:闪烁 LED

几乎每个微控制器的标准入门程序都是 LED 闪光器，所以让我们试一试。你需要一根 FTDI 电缆或任何分线板、一个 LED 和一个 220 欧姆的电阻。

将电阻器连接到 LED 的任一引脚，但要注意哪一引脚是正极(阳极)侧。然后将 LED/电阻器对插入 FTDI 电缆末端的插座，如下图所示，负极引线连接到 GND 线(FTDI 电缆上的黑线)，正极引线连接到 CTS 线(棕色线)。

![ftdi-hello](img/027074bb18d0c3ac5a24f00dd440e09e.png "ftdi-hello")

下面是使用 libftdi API 的 C 源代码。如果您计划使用 D2XX，请稍后查看第二个清单；功能之间的关系应该相当明显。

```
/* hello-ftdi.c: flash LED connected between CTS and GND.
   This example uses the libftdi API.
   Minimal error checking; written for brevity, not durability. */

#include <stdio.h>
#include <ftdi.h>

#define LED 0x08  /* CTS (brown wire on FTDI cable) */

int main()
{
    unsigned char c = 0;
    struct ftdi_context ftdic;

    /* Initialize context for subsequent function calls */
    ftdi_init(&ftdic);

    /* Open FTDI device based on FT232R vendor & product IDs */
    if(ftdi_usb_open(&ftdic, 0x0403, 0x6001) < 0) {
        puts("Can't open device");
        return 1;
    }

    /* Enable bitbang mode with a single output line */
    ftdi_enable_bitbang(&ftdic, LED);

    /* Endless loop: invert LED state, write output, pause 1 second */
    for(;;) {
        c ^= LED;
        ftdi_write_data(&ftdic, &c, 1);
        sleep(1);
    }
}
```

如果程序成功编译(所有必需的头文件和库都在适当的位置，并与我们自己的代码正确链接)，LED 应该会慢慢闪烁。

代码很大程度上是不言自明的，但是有几点值得强调:

*   注意 ftdi_enable_bitbang()的第二个参数。这是一个 8 位掩码，指示哪些线路应该是输出(位设置)与输入(位清零)。由于我们只使用一条输出线路(本例中为 CTS)，因此我们只设置了与该线路相对应的一个位(0x08)。对于额外的输出，我们可以将位值进行或运算。bitbang I/O 引脚映射在任一 API 的头文件中都没有定义，所以您可能会发现保留这样的头文件很有帮助:

    ```
    #define PIN_TX  0x01  /* Orange wire on FTDI cable */
    #define PIX_RX  0x02  /* Yellow */
    #define PIN_RTS 0x04  /* Green */
    #define PIN_CTS 0x08  /* Brown */
    #define PIN_DTR 0x10
    #define PIN_DSR 0x20
    #define PIN_DCD 0x40
    #define PIN_RI  0x80
    ```

*   注意，ftdi_write_data()的第二个参数是一个指向 8 位变量的*指针*。该函数通常需要一个数组(第二个例子将演示这一点)，但是对于这个简单的例子，只需要一个值。当发出这样的单个字节时，记住总是通过引用(指针)传递，而不是数字常量。该函数的最后一个参数是字节数。

传递给 ftdi_write_data()的值表示输出线路的期望状态:设置位表示逻辑高状态(3.3 或 5 伏，取决于所用的 ftdi 适配器)，清除位表示逻辑低状态(0 伏)。位到 I/O 引脚的映射与 ftdi_enable_bitbang()完全相同，因此前面的#定义在这方面可能会有所帮助。

## 更多的铃铛和哨子

有许多项目想法只是偶尔需要切换 I/O 线:当网络计数器增加时响铃，当电子邮件到达时闪烁灯光，当猫使用垃圾箱时发送 Tweet。这类任务的代码通常就像上面的例子一样简单。但是当与更复杂的设备和协议通信时，这种一次一个字节的方法变得非常低效。每次调用 ftdi_write_data()，即使是一个字节，都会发出一个 USB 事务，该事务将被填充为 64 字节的倍数，在该请求实际发送到网络之前，可能会有整整一毫秒或更长的延迟。为了有效地发送复杂的数据流，有必要将整个数组传递给 ftdi_write_data()函数。

Bitbang 模式的工作方式与芯片的默认串行 UART 模式非常不同。在串行配置中，只需调用 fwrite()向串行端口发送一个数据块，芯片就会管理传输协议的所有细节:字长、起始位、停止位和奇偶校验位，并以所需的波特率切换 TX 线路的逻辑状态。在 Bitbang 模式中，没有隐含的协议；这是对数据线的原始访问，我们必须自己小心构建一个有意义的信号，本质上是创建一个数据线随时间变化的*图像图*:

![analogy](img/264ea3cb51c24969e7d57254b802fcb7.png "analogy")

假设我们想要与使用 SPI 协议的器件通信(串行外设接口，有时也称为 Microwire、同步串行或三线或四线串行，具体取决于具体实现)。所需的输出类似于上图中的波形:一条输出线提供时钟信号，另一条表示数据位(与时钟同步)，第三条发出数据结束锁存信号。如果发送 8 位数据，我们的输出数组将需要两倍的大小(代表每个时钟周期的高和低状态)，加上两个额外的字节用于最后的锁存高/低。8 * 2 + 2 =输出阵列中的 18 个字节(如果特定器件要求在锁存信号之前有短暂的延迟，可能会有几个额外的字节)。

SPI 对于介绍性文章来说可能太深奥了；不是每个人都有合适的组件。相反，让我们做一些视觉上令人满意的东西:我们将使用脉宽调制来驱动一组 led。这是可疑的效用，但它华而不实，并暗示速度和精细控制，可能使用这个端口。

硬件设置与第一个例子类似，但重复了四次:四个 led、四个 220 欧姆电阻(我们将其限制为四个，以便与 FTDI 电缆或 SparkFun 基本分线点配合使用，但它可以轻松扩展到八个，与其他板配合使用)。负极引脚共同连接到 GND 线(FTDI 电缆上的黑线)，而正极引脚连接到 CTS、TX、RX 和 RTS(分别为棕色、橙色、黄色和绿色导线)。SparkFun 基本突破用 DTR 代替了 RTS 的最后一个 pin，但是示例代码对任何一个都是一样的……我们稍后会解释如何操作。

这是元件在试验板上的样子。请注意，跳过了+5V 线路(FTDI 电缆上的红线):

![ftdi-pwm](img/df2152c7cf00079a24e18489b22ff9c6.png "ftdi-pwm")

这是使用 D2XX API 的源代码。让它适应 libftdi 很简单；不同的语法见第一个例子。

```
/* pwmchase.c: 8-bit PWM on 4 LEDs using FTDI cable or breakout.
   This example uses the D2XX API.
   Minimal error checking; written for brevity, not durability. */

#include <stdio.h>
#include <string.h>
#include <math.h>
#include <ftd2xx.h>

#define LED1 0x08  /* CTS (brown wire on FTDI cable) */
#define LED2 0x01  /* TX  (orange) */
#define LED3 0x02  /* RX  (yellow) */
#define LED4 0x14  /* RTS (green on FTDI) + DTR (on SparkFun breakout) */

int main()
{
    int i,n;
    unsigned char data[255 * 256];
    FT_HANDLE handle;
    DWORD bytes;

    /* Generate data for a single PWM 'throb' cycle */
    memset(data, 0, sizeof(data));
    for(i=1; i<128; i++) {
        /* Apply gamma correction to PWM brightness */
        n = (int)(pow((double)i / 127.0, 2.5) * 255.0);
        memset(&data[i * 255], LED1, n);         /* Ramp up */
        memset(&data[(256 - i) * 255], LED1, n); /* Ramp down */
    }   

    /* Copy data from first LED to others, offset as appropriate */
    n = sizeof(data) / 4;
    for(i=0; i<sizeof(data); i++)
    {
        if(data[i] & LED1) {
            data[(i + n    ) % sizeof(data)] |= LED2;
            data[(i + n * 2) % sizeof(data)] |= LED3;
            data[(i + n * 3) % sizeof(data)] |= LED4;
        }
    }   

    /* Initialize, open device, set bitbang mode w/5 outputs */
    if(FT_Open(0, &handle) != FT_OK) {
        puts("Can't open device");
        return 1;
    }
    FT_SetBitMode(handle, LED1 | LED2 | LED3 | LED4, 1);
    FT_SetBaudRate(handle, 9600);  /* Actually 9600 * 16 */

    /* Endless loop: dump precomputed PWM data to the device */
    for(;;) FT_Write(handle, &data, (DWORD)sizeof(data), &bytes);
}
```

当成功编译和运行时，led 应该在重复的“追赶”周期中缓慢脉动。与第一个示例有一些显著的不同:

*   LED4 由两位定义，即 RTS 和 DTR 的逻辑或，这两位总是一致切换。这不是一个强制性的要求，它只是使程序兼容不同的硬件:FTDI 电缆和 SparkFun 基本分线点在最后一个引脚上使用不同的信号，切换这两个位使其工作相同。
*   波特率被明确设置为 9600 bps (bitbang 模式实际上将以 16 倍的波特率运行)。因此，无论使用 libftdi 还是 D2XX，PWM 速度都是一样的。默认情况下，前一个库通常将端口初始化为 9600 波特，而后一个 API(这里使用的)以最大速度打开端口，我们需要降低速度来匹配。实际上，在最大速度下，我们每秒可以从这个端口获得大约 650，000 个 8 位样本。
*   在 Mac OS X 10.6 中，您可能会发现有必要将-m32 标志传递给 gcc，以便编译和链接 D2XX 库。而使用 Cygwin 的 Windows 程序员可能需要一些额外的头文件:

    ```
    #include <stdarg.h>
    #include <windef.h>
    #include <winnt.h>
    #include <winbase.h>
    ```

脉宽调制可以很好地直观展示速度，但不幸的是，它并不能真正投入使用。除了前面提到的 I/O 延迟，其他设备可能会共享 USB 总线，总的来说，我们不能指望这种技术的行为是确定性的，也不是实时的。带 LED 的 PWM 看起来很好…时间足够接近…但是尝试 PWM 驱动伺服是不可能的。对于 SPI 等同步串行协议，每个数据位都有一个时钟信号，这种方法非常有效，希望后续文章能够展示这一点。

## 不是万灵药

FTDI bitbang 模式对许多项目来说都很方便，但它不是所有问题的解决方案。在许多情况下，微控制器仍然是首选:

*   对于长期独立使用来说，这是显而易见的:微控制器板的成本比一顿大餐还低，使用 9 伏电池可以运行几天。只有当一个项目无论如何都要涉及一台全功能 PC 时，才应该考虑 bitbang 模式。
*   如果一项任务涉及基本的模数转换，那么使用内置 ADC 的 USB 连接微控制器几乎肯定会更好。这只是比其他选择更少的麻烦。
*   对于需要持续高速轮询传感器的任务，bitbang 模式将不必要地吞噬 USB 带宽和 CPU 周期。大多数微控制器都有一个改变时中断的特性，完全避免轮询，只在实际发生改变时才使用资源。

我们希望这篇介绍已经在您的脑海中播下了新黑客的种子，或者将为被遗忘的经典并行端口黑客注入新的活力。要深入挖掘，FTDI 网站是最好的资源。在这里你可以找到[数据手册](http://www.ftdichip.com/Documents/DataSheets.htm)、[文章](http://www.ftdichip.com/Documents/Articles.htm)，其中最有用的是[应用笔记](http://www.ftdichip.com/Documents/AppNotes.htm)。还有关于使用其他语言的[信息:Java、Perl、Python 和 Visual Basic 等等。](http://www.ftdichip.com/Projects/CodeExamples.htm)