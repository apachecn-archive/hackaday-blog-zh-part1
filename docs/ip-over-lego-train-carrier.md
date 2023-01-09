# IP Over LEGO 火车承运人

> 原文：<https://hackaday.com/2011/12/26/ip-over-lego-train-carrier/>

[![](img/b2cfb3bfbbb7b3ee141c2232c48b3b63.png "train")](http://hackaday.com/wp-content/uploads/2011/12/train.jpg)

[Maximilien]发送了一个用乐高火车模型制作的网络协议。不像 [IP over Avian Carrier](http://en.wikipedia.org/wiki/IP_over_Avian_Carriers) 这个系统不会被平板玻璃窗或猛禽杀死，但我们讨厌赤脚踩在【Max】的工作上。

该系统使用 USB 闪存驱动器将数据传输到不同的节点。在每一个节点，[Max]都切断了铁轨的电源，并增加了一个继电器来再次启动火车。一个机械开关检测到火车的存在，一个 Arduino 通过 USB 串行接口连接到 Linux 机器。

闪存驱动器的物理连接是用四根线和铝箔触点。为了发送数据，系统等待列车到达“车站”，安装驱动器，检查是否有数据，并发送需要发送的内容。卸下驱动装置后，电力被施加到本地轨道上，列车继续其行程。

[Max]承认他的网络延迟很糟糕，但带宽应该还不错。俗话说，“永远不要低估装满磁带的旅行车的带宽。”我们不太清楚这一点如何适用于乐高火车，但这就是你要做的。休息之后，请查看[Max]的作品集。

此幻灯片需要 JavaScript。