# 8 位设备消除了对 IPhone 的嫉妒

> 原文：<https://hackaday.com/2009/11/03/8-bit-device-quenches-iphone-envy/>

![avr-iphone-envy](img/7a07d2ac55fb2cd55ef5d35f38051997.png "avr-iphone-envy")

[Peter]应该因为少花钱多办事而获奖。他[基于 AVR 控制器](http://rossum.posterous.com/avr-homebrew-device-with-iphone-aspirations)构建了一个手持设备，该设备具有通常与更强大的设备相关联的功能。这是它没有做到的:没有电话，没有短信，没有加速度计，最重要的是不需要应用程序的批准。它所做的是利用廉价、易得的组件，结合常见的自制开发技术，创建一个触摸敏感的手持设备。

休息后嵌入的演示视频详细描述了该设备播放视频、渲染 3D 对象以及通过触摸滚动显示图片和电子书。所有这些都以 60 fps 的速度运行，以获得流畅的画面。整个东西并不比他从一个坏掉的 MP3 播放器里抢救出来的 320×240 的液晶显示器大。Atmel AVR ATmega644 微控制器将显示器、电阻式触摸屏和用于存储的 microSD 卡连接在一起。该芯片还控制背光，锂聚合物电池，并使用 USB 连接 PC，充电，甚至鼠标或键盘接口。他自己为表面贴装元件蚀刻 PCB，并设法在底面只需要四根跳线就完成了。

这是我们看到的上一个基于 AVR 的触敏设备的一大进步。演示中看到的所有功能都是使用 4k 内存和 32k 编程空间运行的。因为[Peter 的]以 3.3v 供电，系统时钟被限制在 12MHz，但他设法使它工作。我们要求他发布代码和原理图，他没有退缩。前往 [microtouch 项目页面](http://sourceforge.net/projects/microtouch/)下载代码、Eagle CAD 文件和 PCB 插图。所有的演示文件都在那里，就等着你去利用他的辛勤工作。当你有一些正在运行的东西时，别忘了[与我们分享](http://hackaday.com/contact-hack-a-day/)！

[https://www.youtube.com/embed/EF3-U9Lb12k?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/EF3-U9Lb12k?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)