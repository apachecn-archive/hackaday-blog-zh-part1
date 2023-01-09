# 将电视调谐器用作高速 ADC

> 原文：<https://hackaday.com/2005/11/08/using-a-tv-tuner-as-a-high-speed-adc/>

![tv tuner](img/2dd27f70be2dcac3ee9d8c3c6768b30f.png)

Bt878 芯片组在电视调谐卡上相当常见。该芯片内置模数转换器，采样率为 119kHz 至 448kHz，远高于 44kHz 的标准音频速率。由于芯片通常从调谐器接收音频，所以硬件必须被稍微改动一下才能注入信号。通过一些驱动程序破解，这个芯片可以达到每秒 896000 个样本。在 ALSA 的支持下，最近的发展使事情变得更加容易。

[谢谢 rockarolla]

*   [永久链接](http://www.domenech.org/bt878a-adc/index-e.htm)