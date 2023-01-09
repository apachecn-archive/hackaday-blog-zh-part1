# 任天堂 DS 音乐创作

> 原文：<https://hackaday.com/2008/05/25/nintendo-ds-music-creation/>

[https://www.youtube.com/embed/MQCZnwNr0ms?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/MQCZnwNr0ms?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)
家酿开发者【yaarglafr】最近发布了他的蛋白质 DScratch 的运行视频。你可以在这里下载一个[的演示版本](http://gorgull.googlepages.com/home2)。该程序通过直观的界面模拟 DJ 在 DS 上刮擦，非常像我们前几天讨论的触摸屏转盘。它可以很好地与任何主要的 DS 插槽设备配合使用；只要在上面运行一个 [DLDI 补丁](http://dldi.drunkencoders.com/index.php?title=Main_Page)就可以了。

除了视频中演示的内容，DScratch 还可以直接从麦克风录制和抓取音频。它还能够通过 DS 的 wifi 发送 midi 数据，从而可以用来控制外部 MIDI 应用程序。Dscratch 也有 [NDSMotion](http://ndsmotion.com/) 支持。DS slot 和 GBA slot DS 运动配件包含加速度计和陀螺仪，当 DS 摇晃、倾斜和转动时，它们会在 DScratch 中产生不同的效果。这并不是 DScratch 工作的必要条件，但它最大化了应用程序的功能。

如果你等不及完整版，你可以得到 [Korg DS-10 弹夹](http://www.aqi.co.jp/product/ds10/en/index.html)。然而，这个软件模拟的不是一个转盘，而是一个 Korg MS-10 合成器。它可以像 DScratch 一样处理音乐创作和编辑，但不能通过 WiFi 进行 midi 控制。为此，试试 DSMI，一个我们在 2006 年报道过的开源软件套件[。它由用于 DS 的软件组成，该软件控制 midi 信息并通过 WiFi 将其发送到计算机上的服务器软件，该服务器软件反过来将 MIDI 信息提供给任何正在运行的 MIDI 软件。这两个工具都不完全像 DScratch 那样工作，但是在完全发布之前，它们应该会让您很忙。](http://www.hackaday.com/2006/11/23/happy-thxgiving-dsmidiwifi/)