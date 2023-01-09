# ShmooCon 2009: Chris Paget 的 RFID 克隆演讲

> 原文：<https://hackaday.com/2009/02/16/shmoocon-2009-chris-pagets-rfid-cloning-talk/>

当我们第一次看到[【克里斯·佩吉特】的克隆视频](http://hackaday.com/2009/02/02/mobile-rfid-scanning/ "Mobile RFID scanning  - Hack a Day")时，我们的反应是相当‘咩’。我们以前见过 RFID 克隆，而 [Mifare 破解](http://hackaday.com/2008/01/01/24c3-mifare-crypto1-rfid-completely-broken/ "24C3 Mifare crypto1 RFID completely broken  - Hack a Day")可能是 RFID 最后一次真正有趣了。他的 ShmooCon 演示，嵌入上面，让我们完全措手不及。它信息量很大；我们强烈推荐它。

推销这个演讲最难的部分是，它必须使用两个超载的词:“RFID”和“护照”。美国护照卡是西半球旅游计划的一部分，它不像你所熟悉的护照本。它具有驾驶执照的外形，只能用于美国、加拿大、加勒比海地区、百慕大和墨西哥之间的陆地和海上旅行。他们今年才开始发行。

美国护照卡也使用射频识别技术，但与全球发行的电子护照使用的技术不同。您可能熟悉 125KHz 门禁卡和 13.56MHz 智能卡、MiFare 标签和电子护照。这些都是电感耦合技术。护照卡中使用的 RFID 处于 900MHz 频段，是一种电容技术。这是 EPC Class 1 Generation 2，与用于跟踪仓库中货物的技术相同。每个 EPC 都有一个 96 位的 ID 号。根据设计，它们必须至少在 30 英尺外可读。

为了开始他的研究，[Chris]从易贝购买了一个 XR400 RFID 阅读器。这是一个带有四个天线端口和 Windows CE 的工业阅读器。他得到了一笔好交易…因为它不起作用。他猜测球栅阵列(BGA)焊点已经开裂。在芯片上施加足够的压力可以让设备启动。他用热风枪回流焊料来修理电路板。他引用了一个用相同技术修复的 [Xbox 360 的视频。[邦尼]有一个去年的帖子](http://www.youtube.com/watch?v=DVttOR_uez4 "YouTube - Fix Xbox 360 with heat gun")[调查 Xbox 360 RRODs](http://www.bunniestudios.com/blog/?p=223 "bunnie’s blog  » Blog Archive   » Xbox360 RROD (Again)") 和可能的 BGA 故障。

900MHz RFID 卡不与阅读器感应耦合，因此其读取范围不受波长限制。有了美国的 HAM 执照，可以用高达 1500W 的功率进行广播。在今年的 Defcon 上，[Chris]计划创造新的阅读记录。他引用了 ThingMagic 公司在 12dbi 天线中使用 10W，并从 213 英尺处获得 100%读取可靠性的例子。通过 18dBi 天线的 1500W 的理论极限是 2.35 英里；你会受到标签能传输多远的限制。他建立了 RFIDHackers.com[的网站来帮助协调努力。](http://www.rfidhackers.com/ "RFIDHackers.com • Index page")

另一个未来的项目是使用 GNU USRP 无线电委员会对美国护照卡进行差分功率分析。这是一种强力方法，用于提取标签的 32 位 kill 和 lock 代码，然后可以用来停用卡。

[Chris]研究的目标从一开始就是表明 RFID 不适合这种安全情况。护照卡给每个持有者分配一个唯一的标识符。这个 ID 可以从远处读取，并与持有人的其他 RFID 项目(如他们的信用卡)相协调。任何一方都可以跟踪持有这些卡的人，他们不会更快地穿越边境，因为这些卡仍然需要亲自检查。

美国现在正以对沃尔玛商品同样的尊重来追踪其居民。