# 即兴演奏巴赫，64 代海军准将风格

> 原文：<https://hackaday.com/2009/10/13/jamin-to-bach-commodore-64-style/>

[https://www.youtube.com/embed/MOhzkWZHBfM?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/MOhzkWZHBfM?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

[刷希巴]错过了准将 64 的声音，渴望听到 8 位荣耀中的大师们。为了解决这个问题，他[使用那些早已过时的系统中的原始声音接口设备](http://kaput.retroarchive.org/MIDI.html)创建了一个 midi 设备。他将 [MOS6581 SID](http://en.wikipedia.org/wiki/MOS6581) 与 Atmel AVR ATmega8 微控制器连接起来。AVR UART 的接收引脚用作 midi 输入连接，微控制器将 MIDI 数据转换为适合 SID 的声音生成规格。结果是在上面嵌入的视频中听到的[巴赫]的勃兰登堡协奏曲的 10 分钟。

我们不知道他是从哪里得到这个过时的芯片的，但是如果你想尝试一下，也许你会有运气通过使用另一个 ATmega8 来模仿 MOS6581。