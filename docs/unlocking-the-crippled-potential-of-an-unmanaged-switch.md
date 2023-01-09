# 释放不受管理的交换机的潜在缺陷

> 原文：<https://hackaday.com/2010/05/26/unlocking-the-crippled-potential-of-an-unmanaged-switch/>

[Sprite_TM]超越了他在家庭网络中使用的廉价非托管 TL-SG1005D 交换机的功能。他没有购买一个新的更昂贵的开关，而是打开了一个便宜的开关，发现里面的 RTL8366SB 芯片具有更强的工作能力，但作为低端型号销售时却受到了损害。这不像我们不久前看到的[示波器固件升级](http://hackaday.com/2010/03/31/update-50mhz-to-100mhz-scope-conversion/)那么简单。他必须添加一个 AVR ATmega88 来发送 I2C 命令到交换机。原来 I2C 协议并不是标准的，在绞尽脑汁之后，他找到了一些芯片组的 Linux 驱动程序，这些驱动程序给了他足够的信息来发送他需要的配置命令。现在，他用一个微控制器和一些电线的成本，就可以实现他的 VLAN 所需的管理开关。