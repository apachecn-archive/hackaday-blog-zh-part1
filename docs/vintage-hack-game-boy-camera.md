# 老式黑客-游戏机相机

> 原文：<https://hackaday.com/2009/09/23/vintage-hack-game-boy-camera/>

![Screenshot](img/3bac4ce5fa7a11818a8f130c16bf1268.png "Screenshot")

早在 2005 年，一个名为[Laurent]的法国机器人团队成员写了一篇精彩的[操作指南](http://sophiateam.undrgnd.free.fr/microcontroller/camera/index.html)，我们不知何故错过了使用[游戏机摄像头](http://en.wikipedia.org/wiki/Game_Boy_Camera)作为机器人的视觉设备。上面的图片是他的项目中的真实镜头。Game Boy 相机拥有令人惊叹的 128×123 像素分辨率和华丽的 4 色灰度调色板。这种黑客最吸引人的特点可能是，在易趣上花不到 10 美元就能买到[这些相机](http://shop.ebay.com/?_from=R40&_trksid=p3907.m38.l1313&_nkw=game+boy+camera&_sacat=See-All-Categories)。

他使用数字和模拟信号的组合将相机传感器连接到 Atmel AT90S4433，然后使用微控制器将数据传回他的 PC。他撰写的文章包括传感器/微控制器的布线原理图、传感器的数据表、整个项目的 C 代码以及 GBC 连接器的易读引脚。虽然他的项目只是将图像下载到计算机，但完全有可能让微控制器对图像做出响应，或者只是记录并存储图像。用你的 [自己的](http://www.arduino.cc/) [最喜欢的](http://en.wikipedia.org/wiki/PIC_microcontroller)微控制器替换他的 Atmel 芯片也同样容易，只要它有几个数字 I/O 端口和至少一个模拟端口(或外部模数转换器)。

更新:好消息 r4v5，它需要一个 ADC，而不是一个 DAC。