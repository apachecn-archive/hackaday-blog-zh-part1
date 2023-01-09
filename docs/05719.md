# 200 英里射频发射器(和高空气球)

> 原文：<https://hackaday.com/2010/07/27/200-mile-rf-transmitter-and-high-altitude-balloon/>

如果有一件事是我们喜欢的，那就是一个黑客伙伴对他或她的工作如此热情，以至于他们通过包含尽可能多的细节和信息来为我们写文章。

在这两篇黑客文章中，【Scott】[在](http://www.swharden.com/blog/2010-07-14-high-altitude-balloon-transmitter/)中写道，不仅让我们了解了一所高中建造的[高空气球](http://hackaday.com/2009/09/19/high-altitude-balloons/)，还让我们了解了他价值 5 美元的远程射频发射器。前者只是 GPS 和飞行过程中记录的视频数据，但(斯科特的)专长在于后者。一个 74HC240 八进制缓冲器被用来放大来自一个 29MHz 振荡器的 ATTiny44a 的信号(莫尔斯电码)，产生一个远在 200 英里外的可用信号[。](http://swharden.com/tmp/balloon/view2.html)

它的带宽很低，但如果你在你的项目中寻找一个简单的发射机，需要一个功率更大的(和一个[更小的封装](http://hackaday.com/2010/04/25/rf-transmission-in-the-9-khz-band/))，这可能是你的不二之选。