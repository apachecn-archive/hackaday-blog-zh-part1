# 头戴式耳机当心:动作感应耳机

> 原文：<https://hackaday.com/2009/09/14/head-bangers-beware-motion-sensing-headphones/>

![tiltphones](img/874e9855f8aa93849a9a7653b61e271c.png "tiltphones")

iPhone 在加速度计的使用上没有垄断市场。[倾斜电话项目](http://sleepygeek.org/projects.tiltphones)将一个三轴加速度计整合到一套耳机中，将它们转变为 iPod 的遥控器。PIC16F690 从模拟传感器读取数据，将特定的动作翻译成命令，并像上周的 [Arduino iPod Remote](http://hackaday.com/2009/09/08/arduino-as-ipod-remote-control/) 一样，通过苹果配件协议将它们转发给 iPod。向左或向右快速点头可以跳过曲目，按住侧边点头可以控制音量，放下耳机可以暂停。

这个项目有点老，但我们很高兴[不久]给我们提示，因为我们以前没有见过它。似乎没有任何可用的代码或示意图，但因为[苹果配件协议是已知的](http://nuxx.net/wiki/Apple_Accessory_Protocol)，这只是一个如何解释传感器数据的问题。休息后有视频，如果你自己完成了这次黑客行动，请务必发送后续细节。

[https://www.youtube.com/embed/GyRMJqmLCTw?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/GyRMJqmLCTw?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)