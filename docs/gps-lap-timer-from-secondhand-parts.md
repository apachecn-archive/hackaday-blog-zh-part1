# 二手零件的 GPS 计时圈

> 原文：<https://hackaday.com/2011/07/05/gps-lap-timer-from-secondhand-parts/>

![gps_racing_lap_timer](img/fe9ca5a74f13d56a27da4fee06780e7e.png "gps_racing_lap_timer")

Hackaday 论坛成员[nes]正在为一场耐力赛进行训练，他不想让别人口头说出他的圈速，[他想要一个可以放在车里的东西](http://forums.hackaday.com/viewtopic.php?f=3&t=921)来帮助记录他的表现。随着比赛预算的枯竭，他和他的队友需要一些便宜的东西，如果不是免费的，来完成这项工作。

他用区区 4 英镑买到了易贝上一个“坏掉的”GPS 接收器，并发现接收器可以工作，但损坏的软件阻止了该装置绘制路线。因为他不需要路由功能来记录他的圈速，他打开 GPS 接收器，开始搜寻串行比特流。经过一番探索后，他找到了他要找的东西，并将其连接到他的电脑上，看看数据中是否包含 NMEA 的句子。

他把接收器切割成必要的部分，然后开始组装计时器。计时器使用 ATMega32 来运行节目，在他从垃圾桶里捡来的 LCD 面板上显示相关的时间和位置信息。

他承认线路有点问题，但表示经过大约 7 个小时的粗略使用，一切仍然完好无损，工作正常。