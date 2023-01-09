# 无线键盘容易被破解

> 原文：<https://hackaday.com/2007/12/02/wireless-keyboards-easily-cracked/>

当[Luis Miras] [在 Black Hat](http://homeentertainment.hackaday.com/2007/08/02/black-hat-2007-other-wireless/) 发表演讲时，我们首次报道了打破无线键盘、鼠标和演示者中使用的 27MHz 商品无线电。从那时起，Dreamlab 的人已经成功破解了微软无线光学桌面 1000 和 2000 产品(可能更多)的加密。通过分析协议，他们发现像 shift 和 ALT 这样的元键是以明文形式传输的。每次常规击键使用的“加密”包括将密钥与接收器初始同步期间确定的随机一字节值进行异或运算。所以，如果你嗅一下握手，你就可以解密击键。虽然你真的不需要这么做；只有 256 个可能的加密密钥。使用字典文件，您可以检查所有可能的按键，并在只接收 20-50 次击键后确定正确的按键。他们的[演示视频](http://www.remote-exploit.org/max/automated.html)显示他们同时嗅探三个不同键盘的击键。有人可能会制造一个无线键盘记录器，它能从办公室的每一个键盘上拾取每一次击键。你可以在[白皮书](http://www.dreamlab.net/download/articles/27_Mhz_keyboard_insecurities.pdf)中读到更多关于这次攻击的信息。

[via [午夜研究实验室](http://midnightresearch.com/pages/we-know-what-you-typed-last-summer/)

Digg _ URL = '[http://Digg . com/hardware/Wireless _ keyboard _ encryption _ easy _ broken&# 8217](http://digg.com/hardware/Wireless_keyboard_encryption_easily_broken&#8217)；；

*   [永久链接](http://www.dreamlab.net/download/articles/27_Mhz_keyboard_insecurities.pdf)