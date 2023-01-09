# 高压:使用封闭式继电器进行高压开关

> 原文：<https://hackaday.com/2011/08/19/using-enclosed-relays-for-hv-switching/>

![](img/9a4c525aa59a26f032724ec8b96de38e.png "High Voltage")


在看过许多使用微控制器切换电源电压的项目后，Rob Miles 决定分享他的首选方法。你在上面看到的照片是一个封闭的继电器，零件号 RIBTU1C，由 Functional Devices Inc .制造。

这本身并不是他使用的完全控制方案，但它照顾到了硬件的大部分。他使用基于 555 定时器的触发电路。[Rob]提到如果您货比三家，您可以以低于 15 美元的价格获得继电器、555 定时器和其他组件。当你考虑到你有一个处理高电压的外壳和一个可以连接电源线路的好的端子板时，这是一个非常划算的解决方案。继电器本身可以通过控制电路中的晶体管由 9V 电池触发。

注意上图中的原型板。盒子内部有足够的空间放置驱动电路，受到高压电路隔离层的保护。休息之后看看他发给我们的其他照片。

[![](img/ad71bb330c15c182f0c03ea48d68e275.png)](https://hackaday.com/wp-content/uploads/2011/08/enclosed-relay.jpg)[![](img/f50de2939adbb9874fedfe565b78ef97.png)](https://hackaday.com/wp-content/uploads/2011/08/inside-rib.jpg)[![](img/adeabd8a8928b5010b1a96c0c3a3ab12.png)](https://hackaday.com/wp-content/uploads/2011/08/outside-rib.jpg)[![](img/03ce0b466f331a4fbf39a843c7eeac95.png)](https://hackaday.com/wp-content/uploads/2011/08/ribtu1c.jpg)[![](img/93c0a805f539ec5255ea88b9b8992a32.png)](https://hackaday.com/wp-content/uploads/2011/08/high-voltage5.jpg)