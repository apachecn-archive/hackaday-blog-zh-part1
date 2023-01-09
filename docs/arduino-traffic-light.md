# Arduino 交通灯

> 原文：<https://hackaday.com/2010/01/05/arduino-traffic-light/>

![](img/f31c655afb1411c5ebf314cdf1da4b8f.png "arduino-traffic-light")

[洛克威尔]给我们发了一份关于他黑红绿灯的最新消息。忠实的读者会记得早在 2005 年就看到过这种通过并行端口控制的合法[交通信号。新的更新将旧的端口换成了 USB，并增加了几个自主功能，在休息后的剪辑中演示了这些功能。更新包括一个漂亮的用户界面和一些通知，如电子邮件，即时消息，Reddit 帖子等。](http://hackaday.com/2005/05/29/ambient-traffic-light/)

他把硬件的控制权交给了一个 Arduino。他没有将电路板构建到项目中，而是只包含了他需要的部分；一个运行 Arduino 引导程序的 AVR，一个晶体和过滤帽，以及一个用于连接的 Arduino 串行到 USB 模块。交流负载切换由三个继电器控制。他连接的继电器是 12v 额定线圈。我们认为这应该指向 5v 直流线圈，因为这是逻辑电路运行的电压。切换这些交流负载时要小心，[这个交通灯不是玩具](http://hackaday.com/2009/09/21/stop-light-for-hotwheels/)。

[https://www.youtube.com/embed/AWy8_jEEAMw?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/AWy8_jEEAMw?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)