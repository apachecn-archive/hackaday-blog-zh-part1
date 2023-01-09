# 如何从图像创建 TrueType

> 原文：<https://hackaday.com/2009/10/30/how-to-create-truetype-from-an-image/>

![making-truetype-fonts-from-images](img/51b15c73bbffaab780f2c33df740645a.png "making-truetype-fonts-from-images")

[Viacheslav]希望他的虚拟终端具有 DEC VT220 的外观。他找不到看起来合适的字体集，所以他开始制作自己的 TrueType 字体。他设法找到了 [VT220](http://en.wikipedia.org/wiki/VT220) 用作字体的字形样本图像。他使用一套免费软件将图像分割成 256 个不同的部分，调整大小并转换成一位索引图像，然后将这些图像转换成矢量图形。这是用一点 python，一个图像追踪程序，和名为 [FontForge](http://fontforge.sourceforge.net/) 的字体编辑器完成的。

花些时间尝试一下这些字体工具。有了足够的样本，你应该能够复制任何字体集。我们不会实现像印有细菌的字体那样复杂的东西，但这将是一个正确方向的开始。