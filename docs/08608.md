# ATtiny Hacks:蜜蜂！电子秤，看谁带的蜂蜜多。

> 原文：<https://hackaday.com/2011/09/20/attiny-hacks-bees-an-electronic-scale-to-see-who-brings-in-more-honey/>

[![](img/066c00cc8dc1dc3e4c450363b527c568.png "beeBanner")](http://hackaday.com/2011/09/20/attiny-hacks-bees-an-electronic-scale-to-see-who-brings-in-more-honey/beebanner/)

[MakingThingsWork]想要一种精确的方法来记录他的蜂巢的[重量，所以他决定为自己建造一台数据记录电子秤。首先，他从一台旧电子秤上取下应变仪，然后将它安装到自制的蜂箱底座上。然后，他开始设计和建造基于 Attiny 85 的控制板(如果你没从横幅上猜到的话)。仪表放大器用于放大来自应变仪的信号，然后由 Attiny 上的 ADC 读取。看起来他很难从秤中获得一致的结果，因此为了消除温度变化引起的误差，他设置了一个固定的分压器作为参考。通过这种设置，该秤可以产生+/-0.5 磅精度的结果，对于成本不到 50 美元的系统来说，听起来不错。V-usb 项目软件已用于将秤连接到他的 PC，他使用该 PC 来收集数据并绘制数据图表。总的来说，这是一个非常好的项目，看起来，一些蜜蜂非常多产。](http://makingthingswork.wordpress.com/ "main link")