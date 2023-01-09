# 使用业余爱好伺服的空调调节

> 原文：<https://hackaday.com/2011/08/04/air-conditioner-regulation-using-a-hobby-servo/>

![automatic_mechanical_ac_control](img/7ea07d573962ac3d03b27de72cbbeda9.png "automatic_mechanical_ac_control")

对于任何在大型办公楼工作的人来说，你很可能知道处理监管不力的暖通空调系统的痛苦。[Robovergne]和他的同事最近搬到了一个新地方，发现空调控制效果不佳，办公室变得像桑拿房一样热，或者像肉柜一样冷。

虽然他们在一段时间内每半小时手动开关一次空调，但这变得很累，所以[Robovergne]决定自己动手。他之前从未使用过 Arduino，并认为调节空气将是一个伟大的第一个项目。他在 A/C 遥控器的前面安装了一个小型的业余爱好伺服系统，并将 DS18B21 温度探头连接到 Arduino。一个小罐用于调节温度设定值，这些温度设定值显示在附带的 LCD 屏幕上。现在，当温度开始上升时，Arduino 会触发伺服系统，在没有人类干预的情况下打开空调。

[Robovergne]说虽然他的解决方案很难看，但效果很好。它确实完成了任务，这一点我们不能否认！

继续阅读，看看他的自动空调控制器在行动的视频。

[https://www.youtube.com/embed/Z2GPZRg92BM?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/Z2GPZRg92BM?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)