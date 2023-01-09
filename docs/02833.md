# 网球捡球器

> 原文：<https://hackaday.com/2008/11/22/tennis-ball-fetcher/>

![tennisball](img/bc8b7cd9eb610c1f7d8fc48d8ed5cb1c.png "tennisball")

读者[Julian von Mendel]和他的团队为比赛制造了这个[网球抓取机器人。第一个版本使用距离传感器来定位网球，但他们改为基于](http://translate.google.com/translate?u=http%3A%2F%2Fderjulian.net%2Fprojects%2Froboking&hl=en&ie=UTF-8&sl=de&tl=en "//derjulian.net/projects/roboking")[相机的方法](http://www.cmucam.org/ "CMUcam - Trac")。该机器人有三个全方位轮，设计用于计算到达球的最短路径，而不管方向如何，因为它可以在行进时旋转。使用来自 PS/2 鼠标的旋转传感器来监控轮子。控制由 3 个通过 SPI 通信的 Atmel 微控制器提供。多处理器设计相当通用，可以重复用于不同类型的机器人。虽然他们的机器人表现相当好，但也有一些缺点。有限的存储空间意味着频繁的旅行来丢球。倾斜的桶使他们无法捡起靠在墙上的网球。此外，机器人必须拆卸电池交换。这个项目有很好的文档记录，他们已经发布了所有的控制代码。休息之后，你可以看到机器人正在捡球。

[https://www.youtube.com/embed/38ViwspGmSY?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/38ViwspGmSY?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)