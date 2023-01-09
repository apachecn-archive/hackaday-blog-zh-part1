# 用作数字电视调制器的视频卡

> 原文：<https://hackaday.com/2006/01/10/video-card-used-as-a-digital-tv-modulator/>

![lena](img/33ece3336f5b6dab72bb67f4da0873e4.png)

DVB -T 是一种无线广播数字电视的标准，在北美以外的许多国家都有。这种黑客攻击涉及[使用视频卡生成 DVB-T 信号](http://fabrice.bellard.free.fr/dvbt/)。这个项目的灵感来自于《T4》的《伊莱扎的暴风雨》，我们最近已经报道过了。要实现这一点，您必须在 X 服务器配置中为附加屏幕添加一些自定义设置。当您启动服务器并切换到新屏幕时，它将生成正确的信号。虽然信号强度很弱，但卡必须直接连接到 DVB-T 机顶盒。该框将显示两个不同的频道，每个频道有一个测试图像。信号实际上不是直接产生的，而是 VGA 卡 DAC 谐波的产物。

[谢谢詹姆斯]

*   [永久链接](http://fabrice.bellard.free.fr/dvbt/)