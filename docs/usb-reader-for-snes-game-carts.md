# SNES 游戏车的 USB 读卡器

> 原文：<https://hackaday.com/2009/06/19/usb-reader-for-snes-game-carts/>

[https://www.youtube.com/embed/Pwq6vRM8U7k?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/Pwq6vRM8U7k?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

读者[Matthias_H]发来一段视频，介绍他为 SNES 游戏车设计的 USB 适配器。你所要做的就是插上 SNES 游戏卡带和 USB 线，然后游戏的 ROM 文件就会作为外部存储设备出现在你的电脑上。之后，你可以用你选择的模拟器来播放这个光盘。我们给马蒂亚斯发了电子邮件，询问更多信息，他很快回复了一篇非常好的关于黑客的文章，粘贴在下面。

更新: [[Matthias]为“snega2usb”发布了一个网站，提供了关于电路板开发的更新和常见问题解答。](http://www.snega2usb.com/)

【马提亚斯】写道:

> 零件清单:
> [Atmel AT90USBKey 评估板](http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&name=AT90USBKEY-ND)(Digikey–30 美元)
> [FCI 10046971-003LF 70-pos。双排连接器](http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&name=609-2859-ND)(Digikey–＄4.76)
> 一块小的原型板，用于将连接器焊接到
> 数千根小电线上
> 
> 我使用了以下参考文档:
> [http://www . emulatronia . com/doc tec/consolas/snes/snes kart . html](http://www.emulatronia.com/doctec/consolas/snes/sneskart.html)
> (SNES cart 引脚排列和 ROM 存储图)
> [http://www . Microsoft . com/whdc/system/platform/firmware/fatgen . mspx](http://www.microsoft.com/whdc/system/platform/firmware/fatgen.mspx)
> (FAT16/32 specs)
> 
> 有点难看的电缆解决方案是由于 USBKey 奇怪地选择了. 05”间距的端口连接器，为此我无法找到合适的引脚接头和带状电缆连接器。确切的引脚排列有点奇怪，还不值得公布，因为许多 I/O 引脚实际上是由板载外设共享的，所以我必须在可用的引脚之间分配地址和数据位。一个所有部件都在定制 PCB 上的更干净的版本正在路上，以及对 Sega Genesis 的支持(正在努力实现一体化解决方案:-))
> 
> 代码基于 Atmel USB 大容量存储示例应用程序，我在其中添加了一个用于 ROM 访问的模块和一个只读 FAT16(后者是在十六进制编辑器中硬编码的——有趣！).再说一次，开发仍处于非常早期的阶段(我在一个游戏车上测试了这一点)，到目前为止，源代码的再分发事实上是被 Atmel 的专有许可证所禁止的。
> 
> 我对数据传输速率还不太满意。到目前为止，新一代的控制台推车(N64 等)虽然完全可以读取，但却要花很长时间才能加载。该设备运行在 USB 2.0 全速(12 Mbps)，我不知道有任何廉价的解决方案提供高速 USB (480 Mbps)。
> 
> 未决问题:
> –用尽可能多的不同游戏进行测试(请随意捐赠您最不喜欢的游戏推车！:-))
> –当墨盒被移除/更换时发出刷新！USB 大容量存储协议使用 SCSI 命令集，因此设备无法向主机发送请求(“刷新目录，文件可能已更改”)。
> –优化速度
> –增加对 HiROM 游戏的兼容性
> 
> 顺便说一句，我从来没有做过这样的事情。它如此简单的事实让我有点害怕；-)
> 
> 我想这是我目前能给出的最详尽的描述了。希望你不会介意。
> 
> 马提亚斯