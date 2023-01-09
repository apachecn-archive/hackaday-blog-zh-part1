# 用肌电图检测肌肉

> 原文：<https://hackaday.com/2011/06/29/detecting-muscles-with-electromyography/>

Advancer Technologies 的人刚刚发布了一个肌肉传感器板，在 Instructables 上发布了一个很棒的[遍历](http://www.instructables.com/id/Muscle-EMG-Sensor-for-a-Microcontroller/)，描述了这个板如何使用[肌电图](http://en.wikipedia.org/wiki/Electromyography)测量肌肉的弯曲。

使用与我们之前介绍的[遥控手](http://hackaday.com/2011/06/29/possessedhand-controls-hand-with-electrical-stimuli/)相同的电极放置点，通过感测肌肉和肌腱之间的电压来测量肌肉。其结果是对输出进行了相当精细的感知——足以为项目提供一些模拟控制。

该板本身相对简单——ina 106 差分放大器用于检测肌肉是否弯曲。该信号经过放大和整流后，可以连接到您喜欢的微控制器的模拟输入端。视频演示显示电路板连接到从 Arduino 运行的处理应用程序，但这并不难适应由你的二头肌控制的[远程 Nerf 哨兵炮塔](http://hackaday.com/2010/06/18/nerf-sentry-turret/)。

休息后，请观看视频，了解肌肉传感器板的工作情况。

[https://www.youtube.com/embed/VnrsWdA6dzE?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/VnrsWdA6dzE?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)