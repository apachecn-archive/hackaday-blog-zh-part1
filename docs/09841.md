# 多士炉回流焊综述

> 原文：<https://hackaday.com/2012/03/08/toaster-oven-reflow-soldering-roundup/>

SMD 元器件比我们父辈和祖辈焊接的通孔部件有很多优势。不过，使用这些微小的表面贴装元件需要比烙铁和绕线枪更大的投资。这是过去一两周送来的几个回流炉。

从易贝买了一个 110 伏的烤面包机。即使[拉姆齐]在英国，有 230 伏的电源，烤箱里的一切都是机械的，在更高的电压下也能正常工作。他的第一次测试没有按计划进行；焊锡膏在 120 摄氏度时不会熔化，所以他调高了温度，并了解到 FR-4 中的 FR 代表阻燃剂。没有被吓住，[ramsay]决定[建造一个控制器](http://www.dubioushacks.co.uk/oven-control-design.html)，让温度以合适的速度上升和冷却，让助焊剂和焊膏发挥作用。

焊膏有一个[温度曲线](http://www.kester.com/Portals/0/Knowledge_Base_Articles/Standard_Profile.pdf)，要求电路板在 150 到 180 摄氏度之间保持一分钟左右，然后上升到 220 摄氏度一秒钟，这样焊料就会熔化。[Nicolas]有个有趣的想法，在他的烤面包机烤箱里放了一个[USB 端口，并在他的桌面上存储加热模式。该建筑使用 MSP430 微控制器来打开和关闭为加热元件供电的继电器。[Nick]正在开发一个 C#桌面应用程序，通过他的电脑来监控和调节烤箱温度，所以我们很想看看最终的结果。](http://blog.satelinx.com/?page_id=11)

在 YouTube 上观看 SMD [自对准视频](http://www.youtube.com/watch?v=_5lksMvmqQc)比摆弄镊子、立体显微镜和极其精细的烙铁有趣得多。如果你对烤面包机/回流焊炉有更好的想法，请发送到我们的[热线](http://hackaday.com/contact-hack-a-day/)，我们会检查一下。