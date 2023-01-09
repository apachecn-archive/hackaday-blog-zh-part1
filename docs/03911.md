# 乐高 IPod 黑客机器人

> 原文：<https://hackaday.com/2009/08/30/lego-ipod-hacking-robot/>

![800px-Nanotron-3000-farthen-1](img/b69861de1510056b0ab348864f8e2423.png "800px-Nanotron-3000-farthen-1")

Linux4nano 项目一直致力于将 Linux 内核移植到 iPod Nano 和其他 iPod 上。虽然 [iPodLinux 项目](http://www.ipodlinux.org/)在一些旧 iPods 上运气不错，但新型号用加密保护固件更新。他们计划在设备上运行代码的方法之一是利用 notes 程序中的漏洞；它使处理器跳转到特定的指令并执行任意代码。为了利用这一点，他们首先需要弄清楚他们注入的代码在内存中的最终位置。目前，他们正在测试每一个记忆位置，通过费力地放入假钞并记录其效果。每张纸条需要大约一分钟的时间来测试，他们有数万个地址来检查几个设备。

尽管他们已经破解了 2G Nano，但他们仍有许多工作要做。为了使它更容易，他们正致力于用按下按钮的基于乐高思维风暴的机器人来自动化它。被命名为 [Nanotron 3000](http://l4n.clustur.com/index.php/Nanotron_3000) 的这一系列机器人可以按下测试 iPod 所需的 3 个按钮。理想情况下，这些机器人应该能够每天处理超过 23，000 个地址，这比手动处理效率高得多。运气好的话，他们很快就会破解。

相关: [iPhone Linux](http://hackaday.com/2008/11/28/iphone-linux/)

[通过[纽约电阻器](http://www.nycresistor.com/2009/08/28/nanotron-3000-ipod-nano-hacking-robot/)