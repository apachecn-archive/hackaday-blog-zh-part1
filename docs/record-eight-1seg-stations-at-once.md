# 一次记录八个单腿站

> 原文：<https://hackaday.com/2009/10/07/record-eight-1seg-stations-at-once/>

![multiple_tv_mpeg2_stream_capture](img/2420e1124b30da7a472c10b280453291.png "multiple_tv_mpeg2_stream_capture")

在 mobilehackerz 向我们透露了一个项目。他们为 1seg 广播站 ( [谷歌翻译](http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fmobilehackerz.jp%2Fcontents%2FOneSeg24&sl=ja&tl=en&history_state0=))建造了一个类似[的 PVR。1seg](http://mobilehackerz.jp/contents/OneSeg24) 广播标准是针对移动视频服务的，在日本和巴西等国家可以使用。他们的地面电视信号( [ISDB-T](http://en.wikipedia.org/wiki/ISDB-T#ISDB-T) )被分成每个频道 13 个片段，但高清广播只使用其中的 12 个片段。这允许在第 13 段中广播第 1 段数据。

mobilehackerz 希望录制每个电台完整的每日广播。因此，他们拿起一堆 USB 调谐器 fob，并用两个通电的 USB 集线器将它们链接在一起。视频是以一种 MPEG2 格式传送的，因此一旦从广播中提取出来，就可以直接转储到磁盘上。似乎他们已经[得到了这个系统的一些可用代码](http://code.google.com/p/perlrtmp/)，但是即使有了[翻译的页面](http://translate.google.com/translate?prev=hp&hl=en&js=y&u=http%3A%2F%2Fcode.google.com%2Fp%2Fperlrtmp%2F&sl=ja&tl=en&history_state0=)，我们也无法真正弄清楚它是做什么的。如果你的日语能力很强，请给我们留言。

每个调谐器 3000 日元(约 34 美元)，这不是我们见过的最经济的 PVR 捕捉系统。再加上 15 fps 的广播，我们不确定这有多大用处。不过话又说回来，如果非要问“是为了什么？”你忽略了黑客的本质。

[http://en.wikipedia.org/wiki/ISDB-T#ISDB-TIS](http://en.wikipedia.org/wiki/ISDB-T#ISDB-TIS)