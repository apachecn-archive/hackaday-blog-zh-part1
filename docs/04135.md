# 车库门…数据包嗅探器

> 原文：<https://hackaday.com/2009/10/03/garage-door-packet-sniffer/>

几乎每种形式的电子通信都存在某种类型的记录器或嗅探器。你的按键、电话交谈和无线网络都可能被监控。在这个令人敬畏概念验证项目中，[James]将阵列扩展到了[，包括车库门开启器](http://hackaday.com/2009/09/26/open-garage-door-indicator/)。在收到一封声称罪犯拥有记录任何远程代码并回放的技术的连锁邮件后，[James]想知道他是否能制造这样一种至少能在他的 opener 模型上工作的设备。

![img3](img/8805d5eef0727d029297e535b4731552.png "img3")

[James]从去五金店开始。他无法找到工作在他的遥控器频率上的收发器( [308MHz 时钟 MAX7042 芯片](http://datasheets.maxim-ic.com/en/ds/MAX7042.pdf))，所以至少对于这个化身(他计划建造另一个能够重放捕获信号的收发器)，只实现了一个接收器。接收器[连接到逻辑分析仪](http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=1406&dDocName=en023805)以确定其协议。由于来自接收器的信号非常微弱，[詹姆斯]必须通过缓冲区将其放大，才能被检测到。

![img1](img/8ab1fa931ba9467aee8a6225eedec351.png "img1")

一个 ATtiny26 和一个 4 行 x 20 字符背光 LCD 用于解释和显示来自接收器的信息。[James]围绕定制的 PCB 构建了嗅探器(尽管他遇到了一些布局错误，必须在后期制作时修复)。所有的固件都是用 c 语言编写的。它相当简单，但是占用了微控制器 98%的内存。该程序旨在监控引脚变化中断和定时器，以过滤无效代码和噪声。任何信息(被嗅出的门代码)都通过[的 4 位接口显示在 LCD](http://www.arduino.cc/playground/Code/LCD4BitLibrary) 上，便于记录。有了密码，人们可以配置另一个车库遥控器来开门。如果你对 V2 有什么建议，我们相信詹姆斯会看到这些评论的。

![img4](img/ad560c6bd4cb25566a3e443bb572c5c1.png "img4")

**更新:**代码和 PCB 文件(有错误)可通过以下镜像之一获得:
[filesavr.com/codegrabber](http://www.filesavr.com/codegrabber)
[filefactory.com/file/a0eb0gg/n/code_grabber_zip](http://www.filefactory.com/file/a0eb0gg/n/code_grabber_zip)
[filedropper.com/codegrabber_1](http://www.filedropper.com/codegrabber_1)
[mediafire.com/?share key = 7c 4692 DD 4 F3 ad 2 c 36 e 7203 EB 87368129 e 04 e 75 f 6 E8 ebb 871](http://www.mediafire.com/?sharekey=7c4692dd4f3ad2c36e7203eb87368129e04e75f6e8ebb871)