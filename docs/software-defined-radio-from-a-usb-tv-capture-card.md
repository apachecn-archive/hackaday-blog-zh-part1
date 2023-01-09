# 来自 USB 电视采集卡的软件定义无线电

> 原文：<https://hackaday.com/2012/03/20/software-defined-radio-from-a-usb-tv-capture-card/>

借助简单的数字电视 USB 采集卡，您可以构建自己的[软件定义无线电](http://hackaday.com/2011/07/19/jeri-ellsworth-builds-a-software-radio/)或频谱分析仪。虽然它可能没有[【杰里·埃尔斯沃斯】的 SDR](http://hackaday.com/2011/07/19/jeri-ellsworth-builds-a-software-radio/) 酷，但它仍然非常有用，只需要 20 美元的硬件。

该构建唯一需要的硬件是一个带有 Realtek RTL2832U 芯片组的 USB FM/DTV 采集设备。到目前为止，已经测试了两个 u 盘，最大频率范围(64-1700 MHz)的 u 盘可以直接从中国购买，价格为 20 美元。

[Antti Palosaari】](http://thread.gmane.org/gmane.linux.drivers.video-input-infrastructure/44461/focus=44461)在嗅探设备后发现了将这些廉价的捕获卡转变为软件定义的无线电和频谱分析仪。这些卡对频率进行解调，并将所有数据发送给计算机，并通过软件进行解码。如果你身边有一个这样的采集卡，你可以[抓取软件](http://sdr.osmocom.org/trac/wiki/rtl-sdr)并将其加载到你的*nix 盒子上。目前，该软件只能直接写入文件，如果写入硬盘而不是 ram，可能会丢失一些样本。小问题，但我们相信这个项目将在不久的将来加速。

via [reddit](http://www.reddit.com/r/ECE/comments/r3yqw/pretty_awesome_theres_a_project_to_turn_a_20_usb/)