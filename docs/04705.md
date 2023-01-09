# 柯达数码相框漏洞

> 原文：<https://hackaday.com/2010/01/11/kodak-digital-frame-vulnerability/>

![](img/0bf0824ab63943083bb5425ae5f32d88.png "kodak-digital-frame-hack-w820")

柯达设法发布了一款存在巨大安全漏洞的产品。[Casey]发现柯达 W820 WiFi 数码相框[可能会被劫持用于可疑目的](http://seattlewireless.net/~casey/?p=13)。框架可以添加互联网内容作为小部件；比如脸书状态、推文和图片。问题是这些小工具是基于一个公开网站的信息。不同馈送地址的唯一区别是帧的 MAC 地址的最后两个字符。已经设置好的提要可以被查看，但是通过强行打开 RSS 链接，攻击者可以控制还没有设置好的提要，并预先加载你在启动出厂时不想看到的照片。

现在这个洞似乎已经被堵上了，但这并没有减少我们从阅读这个小缺点中获得的快乐。在 Slashdot 上运行的线程[中有一个非常有趣的讨论。](http://yro.slashdot.org/story/10/01/05/0413228/Kodak-Wireless-Picture-Frames-Open-To-Public)

[ [照片来源](http://www.digitalpictureframereview.com/2008/11/review-kodak-easyshare-w820-digital-picture-frame)