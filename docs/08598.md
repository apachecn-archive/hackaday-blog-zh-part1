# 通过红外控制可操纵的刚毛机器人

> 原文：<https://hackaday.com/2011/09/15/steerable-bristlebot-via-ir-control/>

看着这个刚毛机器人的大小，我们首先想到的是电池在哪里？我们只知道这是一个可充电的镍氢电池，它一定藏在那个小小的电路板下面。但是[纳吉·索托德]不仅仅是制造了一个在桌子上晃动的无脑装置。这个[振动机器人可以用红外遥控器](http://www.azarsayan.com/robo/)控制。它使用 ATtiny45 微控制器来监控用户输入的红外接收器。一个 RC5 兼容的电视遥控器可以让你发送命令，以比我们想象的更多的方式驱动这个小小的外形。休息后看看视频，看看两个振动马达在推动设备方面的表现如何。它们使用 PWM 信号驱动，有助于更好地控制，但看起来没有任何保护电路，这引起了对 uC 寿命的关注。

在 Hizook 的一个更大的帖子中，详细介绍了振动机器人的历史。从技术上讲，它不是刚毛机器人，因为它不骑在刷子上，但概念是一样的。你可以尝试你的微型制作技术来复制它，或者你可以[建造一个更大的版本，也是可控的](http://hackaday.com/2011/03/13/bristlebot-mod-never-rubs-you-the-wrong-way/)。

[https://www.youtube.com/embed/Izpn93gEzDQ?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/Izpn93gEzDQ?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)