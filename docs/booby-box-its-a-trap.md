# 饵盒——这是个陷阱！

> 原文：<https://hackaday.com/2011/04/12/booby-box-its-a-trap/>

这里有一个奇怪的谜题，挑战你打开盒子而不落入陷阱。它是为了分散人们对发生在[2011](http://www.scrt.ch/en/insomnihack/2011/presentation)失眠症黑客大会上更严重事件的注意力而建造的。[塞尔吉奥]和一位同事制作了一个类似定时炸弹的盒子，就像我们知道你每年夏天都期待看到的大片中的那样。该设备顶部的显示屏会倒计时 90 秒，并发出嘟嘟声来标志时间的流逝，并提高你的紧张程度。在广告之后的片段中看到它滴答滴答地走着。

两条电线在两半盒子的边缘相遇，形成一个电路，当触点断开时会发出警报。盒子底部还有一个光电管，如果你提起它并将这个传感器暴露在光线下，它就会触发警报。每个参赛者都有打开盒子的密码；那不是数字代码，而是颜色代码。三个电位计控制 RGB LED 的红色、绿色和蓝色阳极，同时由 Arduino 监控。如果你能拨入适当的颜色，盖子陷阱被禁用，盒子可以被打开。赢家会得到什么？当然，为什么是 Arduino！

[https://www.youtube.com/embed/dXjjjJ46ejA?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/dXjjjJ46ejA?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)