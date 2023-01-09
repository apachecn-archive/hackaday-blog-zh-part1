# 向 Ikea DIODER 添加 HTTP

> 原文：<https://hackaday.com/2011/12/14/adding-http-to-ikea-dioder/>

![](img/9c524303e80385729cff02b9e19e4ecf.png "ikea")

[Alex]提交了一个简洁的 Ikea DIODER 版本,它通过 HTTP 请求控制 RGB LEDs 灯串。

我们已经见过宜家通过无线和通过 [USB](http://hackaday.com/2011/08/19/adding-usb-control-for-ikea-rgb-led-strips/) 控制[二极管，但通过互联网使用二极管对我们来说是全新的。在他的构建中，[Alex]使用了一个](http://hackaday.com/2011/08/25/controlling-dioder-light-strips-wirelessly/) [Nanode](http://nanode.eu/) ，一个类似 Arduino 的小型电路板，内置网络连接。

构建的硬件部分非常简单。MOSFET 控制二极管上的每个 LED 灯条。DIODER 的库存控制器被抛弃，这意味着[Alex]需要找出如何将 RGB 色彩空间转换为色调、饱和度和亮度色彩空间，“以实现超级经典的褪色。”一旦弄明白了这一点，[亚历克斯]实现了一个 1D 柏林噪声函数来混合两种颜色。

最后，伟大的 [EtherCard 库](http://jeelabs.net/projects/11/wiki/EtherCard)被用来将 HTTP 请求转化为舞动的 led。[Alex]正在考虑建立一个 JQuery 网页，这样他就不用像 192.168.1.25/hsl 那样输入命令了？i=0 & h=135 & s=90 & l=50 进入浏览器。没有一个好的网络界面，它并不像(亚历克斯)希望的那样未来，但对我们来说仍然很酷。