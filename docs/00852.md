# 风扇控制器

> 原文：<https://hackaday.com/2006/04/09/fan-controller/>

![fan controller](img/7d82ae13b16e5f7dc161b1561b1b1570.png)

对商用风扇控制器不满意的 Jos van Eijndhoven 决定[建造自己的](http://jos.vaneijndhoven.net/fancntl/index.html)。该电路支持三个带电位计的 LM60 温度传感器，以调节开启温度。PIC 16F676 微控制器读取温度并控制三组风扇。还提供了一个电位计来控制最小风扇速度。为了防止振荡，风扇速度会随着温度下降而缓慢降低。

[感谢艾伦

*   [永久链接](http://jos.vaneijndhoven.net/fancntl/index.html)