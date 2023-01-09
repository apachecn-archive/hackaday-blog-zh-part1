# 游览可用的诺基亚液晶显示屏

> 原文：<https://hackaday.com/2010/10/14/touring-the-available-nokia-lcd-screens/>

[Rossum's]看一看诺基亚的液晶显示屏,这些显示屏既丰富又能满足你的需求。很长一段时间以来，[诺基亚 6100 屏幕已经被用于许多黑客](http://hackaday.com/2009/01/08/how-to-digital-picture-frame-100-diy/)，但他想看看还有什么。他从他的手机垃圾箱中找出几部手机进行测试；诺基亚 6101 和诺基亚 2760。屏幕使用一个三线 SPI 接口，他用逻辑分析仪探测出来。开机时，手机会轮询屏幕，以确定连接的是哪种类型的 LCD 控制器。[Rossum]从逻辑分析仪获取这些命令，并使用它来确定每个屏幕使用的硬件。

他给自己做了一个漂亮的分线板，有几个不同屏幕的连接器。他正在使用的固件会检测屏幕何时连接，并切换到适用于该显示器的协议。休息之后看一下视频。

[https://www.youtube.com/embed/GZlOOvKoToE?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/GZlOOvKoToE?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)