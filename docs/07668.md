# 脸书通告使用一些纸工艺品和简单的电子产品

> 原文：<https://hackaday.com/2011/05/24/facebook-notifier-uses-some-papercraft-and-simple-electronics/>

![](img/ba6f3e0ed6837906ae87e77f34d3f3b8.png "facebook-notifier")

这个周末[项目将会告诉你什么时候你的脸书页面](http://www.hackerstribe.com/2011/ecco-il-primo-facebook-notifier/) ( [翻译](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fwww.hackerstribe.com%2F2011%2Fecco-il-primo-facebook-notifier%2F))上有新的东西要看。迷你邮箱边上的黄旗会自动升起，提醒你最近在网上的受欢迎程度。

这个项目的工艺非常棒。我们喜欢它的规模、颜色，尤其是装饰底座的人造草。在邮箱里，一个 Arduino 控制着一个小的伺服电机，这个电机连接着新的邮件标志。与其他基于 Arduino 的通知程序(无论是[互联网 Furby](http://hackaday.com/2009/08/31/internet-enabled-furby/) ，还是我们自己的[巨魔嗅探鼠](http://hackaday.com/2010/12/19/hackaday-unleashes-a-troll-sniffing-rat/))一样，USB 连接使得将在线信息转换为现实世界的信号变得非常容易。客户端是一个 Python 脚本。它使用了一个我们以前不熟悉的叫做 [mechanize](http://wwwsearch.sourceforge.net/mechanize/) 的包。我们只是粗略地检查了该软件包的使用方式，但我们会记住它是我们常用的软件包的一种替代方式， [BeautifulSoup](http://www.crummy.com/software/BeautifulSoup/) ，当您只是在寻找一些基本数据时，它可能会有点令人毛骨悚然。