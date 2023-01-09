# 在 Arduino 上显示 Twitter

> 原文：<https://hackaday.com/2012/02/27/display-twitter-on-an-arduino/>

![](img/f6f2f8ffe05d8e1456773832d94e0ae2.png "HaD")

如果你曾经想让自己的名字出现在互联网上，现在是你大放异彩的时候了。[克里斯]将一个 Arduino 连接到互联网上，并将[梳理推特](http://www.ustream.tv/channel/socialbot9000)的结果直播给全世界。

[Chris]称其为 SocialBot9000，是一个 Arduino Uno，连接到一个以太网屏蔽和一个 LCD 字符显示器。该固件使用 [Twitter API](https://dev.twitter.com/docs/api/1/get/search) 来搜索包含短语“socialbot9000”的最近帖子。Arduino 上的一个 PHP 脚本完成了所有繁重的工作，在伟大的 [Bildr 教程](http://bildr.org/2011/06/arduino-ethernet-client/)的帮助下，启动并运行以太网屏蔽，[克里斯]开始了比赛。

因为非常怀疑互联网上的每个人都能够在 Twitter 上输入一条消息，并被 SocialBot9000 正确解析，[Chris]在构建日志上放了一个[小表格](http://www.anzel360.com/arduino/socialbot9000-arduino-based-twitter-display/)，它将正确地生成消息，并带你到你的 Twitter 帐户进行发布。做完这一切后，[克里斯]决定找点乐子，在液晶显示器前的摄像机上设置了一个[直播画面](http://www.ustream.tv/channel/10507263)，让全世界观看。