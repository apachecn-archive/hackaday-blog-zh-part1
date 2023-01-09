# 触摸感应键盘

> 原文：<https://hackaday.com/2009/09/18/touch-sensitive-keypad/>

![capacitive_keypad](img/c277b744d722f2f1e80e235ebe59d11b.png "capacitive_keypad")

[Viacheslav]制造了一个[键盘，利用人体电容](http://sensi.org/~svo/capsensor/index.en.html)来检测按键。与关闭物理连接的普通按键不同，他的项目通过 PCB 基板检测触摸。他使用 AVR ATmega8 的模拟比较器来检测[过零](http://en.wikipedia.org/wiki/Zero_crossing)的时刻，然后测量放电所需的时间，以检测按键。

我使用模拟比较器来检测过零时刻，并通过测量时间来评估电荷。内置 AVR ADC 在这里可能不会非常有用，因为可以建立的电荷非常少。

**更新:** [Viacheslav]留下了一条评论，让我们知道我们错了。不使用 ADC，而是使用模拟比较器。上面已经做了这个改动。

[https://www.youtube.com/embed/8Ft1B62H6P0?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/8Ft1B62H6P0?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)