# Arduino 作为 IPod 遥控器

> 原文：<https://hackaday.com/2009/09/08/arduino-as-ipod-remote-control/>

![arduino_ipod_controller](img/4d55f951085b3eda1facf6290fae2715.png "arduino_ipod_controller")

[大卫]有一个 Arduino 在寻找一个项目。他决定使用 ipod 连接器分线板和 3.3v 至 5v 电平转换器(均来自 SparkFun)制作一个由 Arduino 供电的 iPod 遥控器。该电路建立在一个迷你试验板上，由一个 [Arduino Mini](http://arduino.cc/en/Main/ArduinoBoardNano) 控制，并装在一个 Altoids 罐中。为了与 iPod 对话，使用了[苹果配件协议](http://nuxx.net/wiki/Apple_Accessory_Protocol)。考虑到驾驶,[David]连接了一个 [Staples Easy 按钮](http://www.staples.com/Staples-Easy-Button/product_606396)作为播放/暂停按钮。这是一个如何将 Arduino 与 iPod 接口的好例子。使用[他的示例代码](http://github.com/finsprings/arduinaap/tree/master)我们希望看到更多的人致力于自制 iPod 配件。