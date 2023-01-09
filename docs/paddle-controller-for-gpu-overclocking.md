# 用于 GPU 超频的桨式控制器

> 原文：<https://hackaday.com/2011/08/25/paddle-controller-for-gpu-overclocking/>

![](img/99aa77f87547d95df0f1bd6a8ae366e8.png "knob-controlled-gpu-clocking")

[Fred]喜欢从他的显卡中挤出所有可能的周期。但有时将时钟速度推得太高会导致损坏。他想出了一个办法，在你的应用程序还在运行的时候，通过转动旋钮来调整时钟速度。

上面看到的致动器是[一个格里芬 Powermate 3.0](http://store.griffintechnology.com/powermate) 。这是一个 USB 外设，可以用来做任何你能想到的事情。[Fred]使用他编写的 AutoHotKey 脚本来捕获来自微调器的输入，处理这些信息，然后在后台调整 GPU 时钟速度。由于他的 ATi 镭龙 5800 上的时钟可以使用 [AMD GPU 时钟工具](http://downloads.guru3d.com/AMD-GPU-Clock-Tool-v0.9.26.0-For-HD-5870-download-2383.html)进行调整，因此这是该应用程序的一个简单选择。现在，更好的图形在他的指尖。休息后在视频里自己看吧。

当然，如果你不想花钱购买昂贵的硬件，你可以随时[打造自己的桨控制器](http://hackaday.com/2008/08/17/scratch-built-jog-wheel/)。

[https://www.youtube.com/embed/Kfb-RznGoKU?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/Kfb-RznGoKU?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)