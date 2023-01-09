# 建造一个更好的时钟让你发疯

> 原文：<https://hackaday.com/2011/10/12/building-a-better-clock-to-drive-you-insane/>

[https://www.youtube.com/embed/YpqFU4SGe1Y?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/YpqFU4SGe1Y?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

[西蒙]想出了一个改进版的维蒂纳里勋爵时钟，并请求安装在世界各地的等候室里。

上周，我们被介绍了一个现实生活中的 [Vetinari 时钟](http://hackaday.com/2011/10/06/vetinari-clock-will-drive-you-insane/)，它保持规律的时间，但不规则的间隔滴答作响。这是一个将某人的思想变成麦片粥的好方法，但是由于时钟驱动的一些限制，最初的构建在几周之后就中断了。[西蒙]建立了一个非常小的电路来解决这些问题。

就像在第一个版本中一样，微控制器每秒钟给秒针马达发送一次脉冲。至于这个构建的随机组件，微控制器将 32 个字节放入 128 个字节的数组中。该数组每秒被检查 4 次，如果该字节为 1，则秒针递增。如果字节为 0，时间会停止一点点。[西蒙]包括原理图，电路板布局和代码，如果你想自己建立一个。

这种设计有一些缺点；滴答和不滴答的模式被硬编码到微控制器中。即使 32 秒长的模式不应该被注意到，但这并不是一个完全随机的解决方案。从最初版本的评论来看，用放射性衰变来增加一秒可能有点不合适。

我们希望看到秒针在你看的时候停下来。有人要面部识别吗？