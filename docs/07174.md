# TI 的优雅——新的 MCU IDE GUI (DNFTT)

> 原文：<https://hackaday.com/2011/03/21/tis-grace-a-new-mcu-ide-gui-dnftt/>

![](img/867184089761bd9bdde5d2e699d26950.png "GraceToolFolder (Custom)")

TI 最近一直在努力通过 MSP430 Value Line Launchpad 等产品在低成本微控制器开发平台市场中获得牵引力。为了满足快速增长的客户群的需求并吸引更广阔的市场，他们最近发布了 [Grace beta 图形外设配置工具](http://focus.ti.com/docs/toolsw/folders/print/grace.html?DCMP=Grace&HQS=Other+EM+grace "TI Grace Plugin")。Grace 是 TI 自己的 Code-Composer Studio (CCS) IDE 的插件，允许用户以图形方式控制 MSP430 开发的许多 aspecst，并与所有 MSP 430 F2 xx/G2xx MCU 兼容。

利用简单的“向导式”界面，Grace 允许用户快速高效地控制外设，如时钟、定时器、运算放大器、ADC、GPIOs、比较器，甚至更高级的功能，如串行通信或低级寄存器设置的配置。一旦一切都按要求配置好了，Grace 就会输出标准的 C 代码，可以像手写一样进行调试和处理。

虽然 Code-Composer Studio 不是免费的，但是有 30 天的全功能试用，以及其他(受限的)免费许可选项。由于 CCS 是基于 Eclipse 开源软件开发框架的，也许在不久的将来我们会看到其他类似的开发工具。虽然不是苹果对苹果的比较，但我们可以想象，这样的工具可能会为许多新手用户提供一个简单而经济的替代 Arduino IDE 的方法。

接下来的问题是:如果后来的化身将 MSP430 系列提升到“Arduino-killer”的地位，它会因此而欢欣鼓舞，还是会简单地成为那些死忠的微控制器纯粹主义者的新目标，他们喜欢在论坛上为最轻微的挑衅大喊“过度杀戮”？当然，我们希望在下面的评论中听到你的看法！