# 开源火炮

> 原文：<https://hackaday.com/2009/12/23/open-source-artillery/>

[https://www.youtube.com/embed/zPm84nxa2dk?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/zPm84nxa2dk?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

多亏了[乔希、凯尔和迈克]，现在可以和一个阿杜伊诺人进行战争了。在它周围设计的炮塔能够在重新装填之间，近距离连续发射 [6 发泡沫弹](http://en.wikipedia.org/wiki/Nerf)。这个人造武器通过 Arduino 的[板载串行链路](http://www.arduino.cc/en/Tutorial/SoftwareSerial)(通过 USB)与计算机连接。PC 上的软件向 Arduino 发送命令，Arduino 然后执行功能，如平移、倾斜、发射和旋转圆柱体。点火本身的动力来自一台 5 加仑、80 磅/平方英寸的空气压缩机。主机上的 Java 软件也能做更智能的事情，比如从炮塔的网络摄像头显示视频流，甚至执行基本的目标跟踪(成败参半)。所有构建这个机器人的代码都可以在[Josh 的]网站上找到。