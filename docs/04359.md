# 计算机从井字游戏中学习

> 原文：<https://hackaday.com/2009/11/02/computer-learns-from-tic-tac-toe/>

![menace-tic-tac-toe-computer](img/c57a911db623cd0cdbcc9ac68d4c6584.png "menace-tic-tac-toe-computer")

“威胁”( that)是一个有趣的名字，是一种玩井字游戏的机器。这个概念是[Donald Mitchie]教授在 20 世纪 60 年代的工作成果，并在今年的[英国游戏大会](http://www.thisisplayful.com/)上发表的[演讲](http://shorttermmemoryloss.com/menace/)中作为一个例子。

[James Bridle]建立了这个有趣的例子，说明计算系统如何从成功和失败中学习。每个方框对应 304 种不同电路板布局中的一种。操作员使用索引表找到对应于当前状态的盒子，摇动盒子，然后查看哪个 bean 随机落入了盒子中的分区。豆子的颜色/类型对应于机器为该移动“选择”的空间。如果《威胁》赢得了游戏，那么每一个使用的盒子里都会增加一颗与该棋步相匹配的珠子。如果威胁失去，一个珠子将从使用的每个盒子中移除。这样，机器就不会犯两次完全相同的错误，更有可能重复成功的解决方案。

[詹姆斯]指出，他找不到任何证据证明这台机器实际上是以前制造的。有可能这一直是一个理论上的设备，但现在我们已经看到了一个实际的建设。我们认为这是一台计算机，因为它是根据成功的概率来计算移动的，但是你认为呢？如果你渴望更多的图片，在他发布的 Flickr 图片集中有足够多的东西可以看。

[via [BoingBoing](http://www.boingboing.net/2009/11/02/mechanical-computer.html)