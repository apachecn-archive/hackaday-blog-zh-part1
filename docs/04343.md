# arduino“python”集成

> 原文：<https://hackaday.com/2009/10/30/arduino-python-integration/>

![vivarium](img/99cba154052b0d055d863a7f226543c5.png "vivarium")

[网络辣妹]告诉我们她喜欢蛇。嘿，谁不是呢？她将很快收养一只可爱的球蟒，并希望密切关注这种敏感生物的环境。为此，她基于 Adafruit 的 Boarduino(一个极简的 Arduino [克隆](http://hackaday.com/2009/09/19/eduino-arduino-or-avr-breakout/))、TMP36 模拟温度传感器、Saelig 的 WIZ810MJ 以太网接口和一个普通的 LCD 屏幕组装了一个联网的动物监控系统。Arduino rig 定期向 web 服务器发布更新，然后 web 服务器可以使用一组 PHP 脚本生成信息丰富的图表(什么，没有 [Python](http://hackaday.com/2009/10/12/take-the-python-challenge/) ？).

好吧，所以我们可以用一只手来数需要奇特的爬行动物监测的读者的数量，并且仍然有剩余的手指。在无数其他应用中，这种网络传感器监控是经常需要的，所以这篇文章可能是您自己项目的一个很好的起点。在 Arduino 和 web 服务器端都有大量的源代码可以使用。零件清单显示了严肃的节俭:Boarduino，普通的 LCD，尤其是以太网接口；即使有试验板适配器，这个单元的成本也只有普通 Arduino [以太网盾](http://hackaday.com/2008/11/06/official-arduino-ethernet-shield/)的一半左右，剩下更多的资金可用于[蛇](http://hackaday.com/2008/03/05/bad-ass-modular-snake-robot/)食物预算！