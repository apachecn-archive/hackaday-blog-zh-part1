# DVD 温度计

> 原文：<https://hackaday.com/2006/02/22/dvd-thermometer/>

![dvd thermometer](img/9740a154034f96ac2614609883063c9b.png)

读者【alberto ricci bitti】的 [DVD 温度计](http://www.riccibitti.com/dvd_therm/dvd_therm_article.htm)是一个温度感应红外遥控器，可以控制显示温度的 DVD。由于盒子没有从 DVD 播放器得到任何反馈，它停止并启动光盘以确保它处于已知状态。该设备的大脑是摩托罗拉 MC68HC908QT4，一个 8 引脚微控制器。与 Maxim DS1621 温度传感器 I2C 总线的通信通过软件完成。即使你不想建造一个华而不实的温度计，这篇文章也有很多有趣的信息。它涵盖了逆向工程的远程，模拟 I2C 总线，并创造一个可编程脉冲发生器，而不是位敲打。

*   [永久链接](http://www.riccibitti.com/dvd_therm/dvd_therm_article.htm)