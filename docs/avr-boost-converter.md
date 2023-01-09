# AVR 升压转换器

> 原文：<https://hackaday.com/2009/07/07/avr-boost-converter/>

![avrboost](img/168dc5ee7841f682b7054d3073ef75e7.png "avrboost")

在 SpriteMods 上，[sprite_tm]意识到一个[微控制器可以被用作升压转换器来给自己](http://spritesmods.com/?art=ucboost&f=had)供电。升压转换器通过切换线圈的输出来升高来自电池的电压。首先，它是接地的，所以磁场可以在线圈中建立。然后，它以高于输入的电压释放。通常专用芯片以令人难以置信的高频率做到这一点，但来自 AVR 的 PWM 信号足够好地工作。这可以用在低功耗的情况下[，空间是一个问题](http://hackaday.com/2009/04/08/rocket-acceleration-logger/)。

[via [EMSL](http://www.evilmadscientist.com/article.php/tgimboejlinks)