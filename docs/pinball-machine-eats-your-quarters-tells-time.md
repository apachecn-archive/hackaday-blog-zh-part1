# 弹球机吃你的硬币，告诉时间

> 原文：<https://hackaday.com/2011/09/24/pinball-machine-eats-your-quarters-tells-time/>

![pinball_machine_clock](img/d98d53eaf12fffbe4cd550dda0b9c990.png "pinball_machine_clock")

[alanamon]在他的地下室有一台旧弹球机，他认为把它改装成时钟会很酷。他不希望它只是一个普通的钟，但是他希望弹球机是他家里最精确的钟。

除了使用游戏的得分卷轴来显示时间，他还想确保这个版本的另外两件事——游戏在需要时正常运行，以及时钟机制不会对游戏做出永久性的改变。为了做到这一点，他在机器内部四处挖掘，并使用固定在游戏琼斯插头上的夹子而不是钻孔和焊接电线来进行所有连接。

时钟由 Arduino 驱动，Arduino 使用他随身携带的旧 GPS 接收器获取时间数据。接收器从 GPS 卫星获取时间数据，就像我们昨天展示的[这个时钟一样，](http://hackaday.com/2011/09/23/flip-off-your-alarm-clock/)每分钟更新一次比分卷轴。时钟可以被编程为每天在预定的时间打开和关闭机器，只要关闭 Arduino 就可以让你在不变的状态下玩游戏。

我们从未真正考虑过使用弹球机来显示时间，但它对我们很有用！看看他的弹球钟在跳跃后运行的视频。

[https://www.youtube.com/embed/uUnR5iLF33M?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/uUnR5iLF33M?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)