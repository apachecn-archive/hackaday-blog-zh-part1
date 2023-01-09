# 路由器/Twitter/Arduino 时钟

> 原文：<https://hackaday.com/2009/09/16/routertwitterarduino-clock/>

![ledclock](img/f582856169a3e5cd9e42285f144a3bc8.png "ledclock")

[凯尔]决定为他的教堂建造[上面的 LED 钟](http://xkyle.com/category/clock/)。虽然它看起来足够令人印象深刻，但它也是隐藏了大量功能的[。[Kyle]想让时钟尽可能容易控制，所以他没有使用按钮或拨号盘来控制显示的内容，而是使用了 Twitter。时钟通过一个](http://wiki.xkyle.com/Clock) [Linksys WRT54GL](http://www.linksysbycisco.com/US/en/products/WRT54GL) 连接到互联网。路由器[遭到黑客攻击，因此](http://wiki.xkyle.com/Wrt54gl)不仅提供 Twitter 连接，还解析时钟反馈得到的所有回复[。时钟响应命令打开或关闭它，在服务前运行倒计时，在教堂的直播流中显示观众的数量，并显示一系列数字。时间从来不需要设置，因为它是从互联网](http://twitter.com/relevantclock)同步[。用于实际驱动显示器](http://en.wikipedia.org/wiki/Network_Time_Protocol)的[电路基于 PIC，但它被更改为运行 Arduino。](http://www.sparkfun.com/commerce/tutorial_info.php?tutorials_id=47&page=6|these)