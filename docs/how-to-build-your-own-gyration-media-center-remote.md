# 如何:构建自己的 Gyration Media Center Remote

> 原文：<https://hackaday.com/2008/10/08/how-to-build-your-own-gyration-media-center-remote/>

![](img/c0365397161a91f7fb48fe869a7fde87.png "m2010")

[Movea 刚刚发布了](http://www.engadget.com/2008/09/09/moveas-gyration-air-music-remote-doubles-as-a-wireless-mouse/)一款用于 [Windows Media Center](http://www.microsoft.com/windows/windows-vista/features/media-center.aspx) 电脑的 [Gyration 的无线遥控器](http://www.gyration.com/p-68-media-center-universal-remote-control-windows-media-center-compatible.aspx)。除了遥控器提供的无线鼠标控制之外，遥控器的一个很好的功能是能够在显示器关闭时控制 [Windows Media Player](http://www.mahalo.com/Windows_Media_Player "Windows Media Player - Mahalo") (WMP)。

遥控器通过下载数据与 WMP 互动，并使用其内置的液晶屏显示。在这里，你可以按专辑或艺术家查看歌曲，甚至访问你的播放列表。遥控器的价格从 179.99 美元到 229.99 美元不等，并附带键盘。

经过一番搜索，我们发现 Gyration 已经为[戴尔](http://www.mahalo.com/Dell "Dell Computers - Mahalo")制作了一个类似版本的遥控器，它与[戴尔 XPS M2010](http://www.dell.com/content/products/productdetails.aspx/xpsnb_m2010?c=us&cs=22&l=en&s=dfh) 打包在一起，基于此以及 AVS 论坛上【BENZONATE】[的一个帖子，我们使用以下部件组装了自己的遥控器:](http://www.avsforum.com/avs-vb/showthread.php?t=893705)

*   戴尔 M2010 高级遥控器
*   戴尔 RH515 无线网卡
*   [戴尔汤姆逊驱动](ftp://ftp.us.dell.com/video/R142872.EXE) (EXE) [](ftp://ftp.us.dell.com/video/R142872.EXE) 
*   usb 电缆

我们在易贝找到了我们的裸机遥控器，售价 19.99 美元。当我们向 Gyration 的[Greg]寻求这个项目的帮助时，他向我们解释说，由于戴尔选择编写驱动程序的方式，M2010 遥控器只能与戴尔射频模块绑定(射频连接);该遥控器不能与他们的任何标准射频接收器配合使用。如果您确实在易贝购买了遥控器，请注意该遥控器只能与 RH515 卡配合使用。

虽然找到遥控器很容易，但试图找到 RH515 却是另一回事。在网上搜索并致电戴尔的业务支持人员后，我们找到并以 10.99 美元的价格购买了 RH515 卡，包括在[戴尔商店网站](http://accessories.us.dell.com/sna/category.aspx?c=us&category_id=5188&cs=28&l=en&s=dfb)的运费。

![](img/423bbd67502c8d018bef992f5e9267da.png "rh515")

收到主板后，我们开始拆除随附连接器上的电线，并使用以下方法将其与 USB 电缆配对:

*   红色/绿色到黑色
*   黄色到绿色
*   白色到白色
*   黑色到红色

我们用绝缘胶带把裸露的电线包起来，然后在我们的电脑上安装了汤姆逊驱动程序。在将电路板插入一个开放的 [USB](http://www.mahalo.com/USB "USB - Mahalo") 插槽后，Windows 很快识别出该卡，并按照 [M2010 遥控器的指令](http://support.dell.com/support/edocs/acc/premrmt/)配对设备，给了我们一个工作的回转遥控器。

遥控器的基本媒体中心功能与任何其他遥控器一样，旋转功能允许我们在舒适的沙发上控制光标以及执行左右点击。最好的部分是:遥控器让我们能够使用内置的 LCD 屏幕选择我们的音乐。

我们在向下滚动歌曲列表时确实遇到了一些延迟，但这可能是由于我们过多的按键造成的。除了延迟之外，遥控器本身的性能非常好，而且比 Movea 遥控器的成本更低。