# 用父母倒数计时器保持乐趣

> 原文：<https://hackaday.com/2011/04/06/keep-fun-in-check-with-a-parental-count-down-timer/>

游戏行业软件工程师[Pedantite]写信告诉我们他的最新努力，一个基于 AVR 的父母助理定时器:[美好时光](http://bytecruft.blogspot.com/2011/03/good-times-part-1.html)。为了寻找一个既有用又有趣的新项目，他的妻子提出了一个“暂停/时间到了的计时器”。像我们大多数人一样,[Pedantite]的孩子在拖延和恶作剧的艺术方面学得很好。在孩子的情况下，这导致暂停和休息时间横行。在这种情况下，解决方案是一个带有有趣声音的高级 DIY 鸡蛋计时器。

该计时器具有所有基本的倒计时功能，包括 4 位 7 段 LED 输出显示、停止灯式 LED 指示灯以及启动/暂停和停止倒计时的控件。倒计时时间可以通过+5 分钟、+1 分钟和+15 秒按钮输入。甚至还有一个快乐/悲伤按钮，可以在“暂停”和“休息”模式之间切换。两个 Atmel micros 为该设备供电，一个 AT Tiny 2313V 用于电容式触摸键盘，一个 AT Mega 644P 用于显示、音频和时间测量。在构建中使用了很多优秀的技术，其中一些我们已经在这里介绍过了:四个 595 移位寄存器[用于显示；用于音频输出的 4 位 r2r](http://hackaday.com/2011/03/14/beginner-concepts-595-shift-register-simulator/) [DAC](http://hackaday.com/2011/02/17/your-first-digital-to-analog-converter-build/) 。

[Pedantite]仍在撰写这个项目的多个帖子，很想知道你们都想听些什么。查看[他的博客](http://bytecruft.blogspot.com/2011/03/good-times-part-1.html)了解详情和计时器运行的快速视频！此外，如果你对电容按钮感兴趣，请查看文章的[第 2 部分](http://bytecruft.blogspot.com/2011/04/good-times-part-2.html)。