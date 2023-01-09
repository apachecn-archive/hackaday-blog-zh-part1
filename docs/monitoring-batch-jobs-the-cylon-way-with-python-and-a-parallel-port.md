# 使用 Python 和并行端口以 Cylon 方式监控批处理作业

> 原文：<https://hackaday.com/2011/11/18/monitoring-batch-jobs-the-cylon-way-with-python-and-a-parallel-port/>

![parallel-port-trigger](img/3b8fe204391e351024a14d574b8e3019.png "parallel-port-trigger")

如果你碰巧做了大量的视频编码，你知道在这个过程中你的电脑真的会很慢。我们自己的[Mike Szczys] [经常在家对视频进行转码](http://jumptuck.com/2011/11/17/cylon-eye-conclusion/)，因为这个过程是自动化的，他并不总是知道转换是否在后台发生。

他最近一直在摆弄拉森扫描仪，并认为通过将扫描仪用作个人电脑的“忙碌”指示器，他可以很好地利用 T2 在这一过程中学到的一切。他将扫描仪连接到电脑的并行端口，花了几分钟时间编写出一些 Python 代码，当他的电脑繁忙时，这些代码会提醒他。

每当他的 MythTV 设置准备好要转换的东西时，他就将通知脚本和 FFMPEG 一起启动。Python 脚本将并行端口上的一个引脚驱动到高电平，触发 Larson 扫描仪的动画。脚本每分钟都会检查 FFMPEG 的状态，并继续保持引脚为高电平，直到应用程序退出。一旦转换完成，扫描仪将返回睡眠状态，让[迈克]知道海岸是安全的。

继续阅读，观看他的并行端口触发器的视频。

[https://www.youtube.com/embed/8GH3wlvOin8?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/8GH3wlvOin8?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)