# 自动将名人八卦从你的电视时间中剔除

> 原文：<https://hackaday.com/2011/08/16/automatically-weed-the-celebrity-gossip-out-of-your-tv-time/>

马特·理查森想出了一个绝妙的主意:使用 Arduino 来监控电视上的隐藏字幕，当屏幕上出现关于可笑的名人的新闻时，将其静音。

他用[视频实验者屏蔽](http://hackaday.com/2011/03/24/video-experimenter-shield/)来监控字幕。这种屏蔽通过复合视频连接，可用于解码二进制代码，该代码携带屏幕顶部过扫描中的字幕。当一个关键字出现时，红外 LED 会向电视机发送静音命令，然后等待 30 秒，直到最后一个关键字消失。这就像[一只嗅巨魔的老鼠](http://hackaday.com/2010/12/19/hackaday-unleashes-a-troll-sniffing-rat/)为你的电视服务！现在我们只需要弄清楚如何使用它来静音广告。

[Matt]建议我们应该想象所有我们可以通过访问隐藏字幕数据来做的很酷的事情；当他开始考虑这个建议时，我们已经在深思熟虑了。在一个没有使用电视声音的地方，这将是一个绝妙的恶作剧。你可以将 Arduino 嵌入视频，然后编程等待新闻报道中的关键词，并以有趣的方式改变它们……就像一个现场的疯狂库。

休息之后你可以看到[Matt]对这个项目的视频解释。

[https://www.youtube.com/embed/-SzB5OQUcOU?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/-SzB5OQUcOU?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)