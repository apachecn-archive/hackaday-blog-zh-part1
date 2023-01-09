# 将路由器用作显示器

> 原文：<https://hackaday.com/2012/02/04/using-routers-as-displays/>

![](img/04b629f433ba705d1711f3b3947830bd.png "routers")

你见过用路由器做成的 LED 显示屏[吗？[Sean]用 8 个 Netgear 路由器做了一个 8×4 的显示屏。因为这还不够酷，一个非常小版本的康威的生活游戏被添加到构建中。](http://www.boxysean.com/projects/mesh4lyfe.html)

每台路由器都运行着一份 OpenWrt 的拷贝，这是一个针对有限硬件的 Linux 发行版。代替 802.11 协议，每个路由器运行 [B.A.T.M.A.N .高级网状协议](http://www.open-mesh.org/wiki/batman-adv)。该协议允许每台路由器与所有其它路由器通信。

不是每个路由器从主路由器接收数据，而是路由器独立计算生活游戏中的每一步。一旦路由器传达了它们的初始状态，每台路由器负责为每一代路由器显示四个 led。在休息后的视频中，你可以看到[Sean]的路由器正在计算生命板的随机游戏。可悲的是，我们没有注意到 GoL 振荡器是随机产生的，但在 4×8 的运动场中，即使是一架[滑翔机](http://en.wikipedia.org/wiki/Hacker_Emblem)也不会持续很长时间。

[https://player.vimeo.com/video/35936030](https://player.vimeo.com/video/35936030)