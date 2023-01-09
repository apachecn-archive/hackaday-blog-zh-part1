# 用策略编写的电话/网络应用程序看起来更受欢迎

> 原文：<https://hackaday.com/2010/03/01/phonewebapp-written-in-ploy-to-appear-more-popular/>

![](img/b5b0f5b48226e9868319562a685a6a28.png "develop-uses-ploy-to-make-friends")

这个头衔对[Evan]来说并不公平，但他确实写了一个[手机俄罗斯方块游戏，如果你赢了，它会让你的手机自动给他打电话](http://www.infectmac.com/2010/02/tetris-with-twilio.html)。他使用了两个我们不太熟悉的应用程序， [Twilio](http://www.twilio.com/) 和 [Tornado](http://www.tornadoweb.org/) 。前者通过简单的 API 处理来自手机的控制输入。后者是运行实际游戏的 web 服务器和 web 框架。

如果你对他如何将两者结合起来感兴趣，你可以[在代码](http://bitbucket.org/evanlong/twilio-tetris-game/)中四处看看。如果你真的不在乎怎么做，你可能只想赢得[的游戏](http://tetris.evanlong.info/)，自动给【埃文】打电话，在这个过程中增加他的无线账单。

请发表评论，帮助我们为这篇文章增添一些价值。我们想知道 Twilio 与谷歌语音相比如何，谷歌语音似乎没有公开的 API(但在那个领域有一些工作)。我们也认为基于网络的手机互动，已经在 T2 的黑客中流行起来，刚刚开始产生一些动力。你用什么工具来使手机界面更容易、更快地实现？