# 通过 CAN 总线入侵增强您的密钥卡

> 原文：<https://hackaday.com/2011/04/26/enhance-your-key-fob-via-can-bus-hacking/>

[Igor]驾驶第四代大众高尔夫，并决定他想玩一会儿 CAN 总线。知道舒适巴士是最容易接近和最安全的玩具后，[他开始四处打探，看看他能看到什么](http://secuduino.blogspot.com/2011/04/grupo-volkswagen-can-confort.html) ( [谷歌翻译](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=es&tl=en&u=http%3A%2F%2Fsecuduino.blogspot.com%2F2011%2F04%2Fgrupo-volkswagen-can-confort.html))。

他拉下一个后门的装饰，用一个 Arudino 和一个 CAN 接口模块连接到舒适的巴士上。他嗅了一会儿公交车的流量，然后决定给他的车增加一些它非常缺乏的功能。通过转动任何锁中的钥匙超过几秒钟，汽车的所有窗户都可以被摇下，但是这不能远程完成。该功能可以通过第三方模块或通过一些预装软件操纵汽车的程序来添加，但[Igor] [想亲自尝试一下](http://secuduino.blogspot.com/2011/04/hacking-vw-confort-can-bus-ii.html)。

他对阿尔杜伊诺进行编程，使其能够比正常情况下更长时间地收听遥控器上的按键。一旦它检测到他试图把车窗摇上摇下，阿尔杜伊诺就会向汽车发出适当的车窗控制指令，而他的愿望就是汽车的指令。

这是一个非常简单的过程，但是他才刚刚开始。我们期待看到[伊戈尔]在未来还能做些什么。与此同时，继续阅读，看看他的作品的快速视频。

如果你有兴趣看看你能用自己的车做些什么，看看我们不久前推出的这个 CAN 总线嗅探器。

[https://www.youtube.com/embed/_JQyTYB3ZoA?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/_JQyTYB3ZoA?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)