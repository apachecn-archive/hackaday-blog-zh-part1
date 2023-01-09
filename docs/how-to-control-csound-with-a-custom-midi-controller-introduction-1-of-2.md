# 如何使用自定 Midi 控制器控制 Csound:简介(第 1 页，共 2 页)

> 原文：<https://hackaday.com/2005/08/23/how-to-control-csound-with-a-custom-midi-controller-introduction-1-of-2/>

[Csound](http://www.csounds.com/) 是一种用于声音合成和处理的自由语言。它有着丰富的历史，今天仍被音乐家、作曲家和声音设计师使用，包括布赖恩·伊诺、理查德·詹姆斯(又名 Aphex Twin)、NIN、DJ ghost 等等。为什么 Csound 今天还存在？这是一种简单的语言，可以迅速转向复杂的听觉体验。这再加上快速的学习曲线，使 Csound 自 1985 年由 Barry Vercoe 在[创造以来一直是一种流行的音频合成语言。](http://www.engadget.com/entry/1234000430055334/)

这是两部分的一部分。第一部分是对 Csound 的介绍。下周的第二部分将让你建立一个物理接口来通过 Midi 控制 Csound 环境。请注意，这个介绍是宇宙中的一小抹油漆，是声音的创造。许多书籍、整个网页和课程都是在 Csound 上教授的。这篇介绍旨在让读者一窥音频创作的丰富世界，并希望能激发读者在 Csound 上投入更多的时间。

你需要一台带声卡的电脑，Mac (OS X 或 OS 9)，Windows 或 Linux 操作系统。本指南将重点介绍 Csound 的最新 Mac OS X 版本，但应该允许推断到您的操作系统。

为您选择的操作系统找到并安装 Csound:
[Mac OS X](http://www.csounds.com/matt/MacCsound1.2a5.dmg.sit)
[Mac OS 9](http://www.csounds.com/matt/MacCsound.1.0.2.sit)
[Windows](http://www.csounds.com/csoundav/index.html)
[Linux](http://sourceforge.net/project/showfiles.php?group_id=81968&package_id=84003)(此处还有)

如果你不确定应该下载哪个版本，请访问 [Csound 首页](http://www.csounds.com/)并选择“Execs ”,然后导航到你的操作系统的下载，或者访问 [sourceforge 页面查看 Csound](http://csound.sourceforge.net/) 。

启动 Csound 应用程序。注意在主窗口的顶部有“兽人”和“sco”标签。Orc 代表管弦乐队，你可以在这里定义你的乐器的声音。Sco 代表乐谱，您可以在其中定义每个乐器的音符、持续时间和参数。

![csound4](img/5693a78fae8ef4618b5e3eda1c304a2f.png)

删除“orc”窗口中的文本，剪切并粘贴该文本以替换它(或从此处下载 orc 和乐谱文件[):](http://www.engadget.com/misc/text_files.zip)

复制粘贴此行下面的文字
= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =
；法比安·塞利耶
；engadget.com
；2005 年 8 月 23 日
；随意再分配！请利用我，再利用我。

Sr = 44100
kr = 44100
ksmps = 1
nchnls = 1

instr 10
【idur = P3】【iamt = ampdb(P4)
【ifq = cpsph(P5)
【ifun = P6】
【iatk = p7】
【irel = P8】
【iatkfun = p9】
index 1 = p10】 ifun
asig2 buzz kenv，ifrq * . 99，kbuzswp+1，ifun
asig 1 pluck iamt，ifrq * . 5，ifq 0.1
amix = asig 1+asig 2+asig 3+afab
out amix * . 5
结束

仪器 30；3D 示例波浪地形

ilevl = p4 * 32767 输出电平
ipatch =(P5<10？CPS PCH(P5):P5)；音高单位为 cpspch 或 Hz
iposx 1 = P6；x 位置开始
IPOs x2 = p7；x 位置终点
IPOs y1 = P8；y 位置开始
IPOs y2 = p9；y 位置终点
iradi 1 = p10/1000；半径开始(缩放)
iradi2 = p11/1000