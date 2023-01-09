# 窃听加密压缩语音

> 原文：<https://hackaday.com/2008/06/19/eavesdropping-encrypted-compressed-voice/>

约翰霍普金斯大学的一个团队发现了一种窃听加密语音流的方法。像 Skype 为其 VoIP 服务所使用的那种语音数据为不同的声音发送不同大小的加密数据包。该小组了解到，通过简单地测量数据包的大小，他们可以以很高的准确率确定正在说什么。VoIP 提供商通常使用可变比特率来更有效地使用带宽，但正是这种压缩使音频流容易被窃听。

该团队的软件仍处于早期开发阶段，还不能解析整个对话。不过，它能够找到预先确定的关键词，并根据检测到的单词推断出常用短语。它在识别长的复杂单词方面也比短的单词有更高的准确率。团队的目标不是窃听，而是揭露漏洞；团队成员[Charles Wright]指出，“我们希望在这个威胁变得太严重之前就已经发现了它。”

[via [安全上的施奈尔](http://www.schneier.com/blog/archives/2008/06/eavesdropping_o_2.html)
[图片:[替代标记](http://flickr.com/photos/altemark/304079314/)

*   [永久链接](http://technology.newscientist.com/channel/tech/dn14124-compressed-web-phone-calls-are-easy-to-bug.html)