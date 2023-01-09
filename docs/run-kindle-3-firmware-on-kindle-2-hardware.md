# 在 Kindle 2 硬件上运行 Kindle 3 固件

> 原文：<https://hackaday.com/2011/05/31/run-kindle-3-firmware-on-kindle-2-hardware/>

![](img/e8b53a1e0a08ee64b5aa3aaadb2e3176.png "kindle-3-firmware-on-kindle-2")

经过大约六周的测试，【一帆路】发布了一个稳定版的 [Kindle 3 固件，用于 Kindle 2 硬件](http://yifan.lu/tag/kindle/)。打了补丁的固件似乎一切正常。我们立即得出结论，在旧的硬件上升级一定非常慢。[Yifanlu]在他的文章中提出了这个假设。Kindle 2 硬件没有 Kindle 3 快，但听起来升级的固件并不比旧设备上的库存固件慢。

由于固件是专有的，升级方法要求您同时拥有 Kindle 2 和 Kindle 3。三个脚本将从旧硬件中提取固件映像，将其复制到新硬件并同时对其进行修补，然后将完全修补的软件包复制回旧硬件以供使用。

休息之后，你可以看到一个运行 3.1 固件的 Kindle DX 视频。还有一个到 Reddit 帖子的链接，评论者链接到预编译版本的补丁包。

[https://www.youtube.com/embed/OMFIYSGLz4M?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/OMFIYSGLz4M?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

[通过 [Reddit](http://www.reddit.com/r/kindle/comments/hmyo5/hack_to_install_kindle_3x_on_kindle_2_and_dx/) 感谢杰森]