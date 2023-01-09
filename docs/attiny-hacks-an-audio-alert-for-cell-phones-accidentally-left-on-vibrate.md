# ATtiny Hacks:手机意外留在振动状态的声音提示

> 原文：<https://hackaday.com/2011/09/15/attiny-hacks-an-audio-alert-for-cell-phones-accidentally-left-on-vibrate/>

![ATtiny Hacks Theme Banner](img/5f674cf2d4b94faba5f6b413d805f657.png "ATtiny Hacks Theme Banner")


[约翰·汤姆森]当他把手机放在口袋里的时候，他通常会把手机调成震动，当他把手机设置成充电状态的时候，他经常会忘记把铃声打开。这通常会同时导致大量未接电话，所以他不得不设计一种方法来抵消他的健忘。

你可能还记得去年 12 月我们举办的圣诞老人比赛中的约翰。他想在另一个比赛中一试身手，那就是 [Avnet 夏季三伏天比赛](http://hackaday.com/2011/08/25/a-design-contest-with-high-odds-of-winning/)，所以他匆忙想出了一个快速解决他的情况的方法。他根据[成龙的]设计为[“带有 8 针 IC 的简单 SD 音频播放器”](http://hackaday.com/2011/03/05/micro-audio-player-can-hide-behind-a-postage-stamp/)炮制了一个简单的电路，即使他的手机处于振动状态，也能提醒他有来电。

[John]使用了 ATtiny85，就像[ChaN]一样，增加了一个用于声音输出的扬声器和一个用于检测手机振动的压电传感器。当压电感应到一点运动时，音频播放器就会启动，发出一系列声音，肯定会引起[约翰]的注意。