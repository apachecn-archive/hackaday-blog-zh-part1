# Arduino 的假雪

> 原文：<https://hackaday.com/2009/12/21/fake-snow-from-an-arduino/>

![](img/a81bdfbcc25dd586eb1941c094e8c7a6.png "hbo_01")

[【Sosolimited】](http://sosolimited.com/design_hbo.html)的团队签约为纽约的 HBO 零售店设计一个有趣的假日橱窗展示[。时代广场的展示包括一块发光二极管板和一台机器，用于将人造雪颗粒吹到围栏周围。](http://en.wikipedia.org/wiki/HBO)

控制 LED 阵列的代码是在开源 C++工具包[open framework](http://www.openframeworks.cc/)之上编写的，整个设置通过 Arduino Duelmilanove 与[接口。多个](http://hackaday.com/category/arduino-hacks/)[敏锐的红外传感器](http://www.acroname.com/robotics/info/articles/sharp/sharp.html)被连接到 Arduino 上，以检测观察者的移动，这反过来触发风扇将“雪”吹向四周。国家控制设备继电器板将重型风扇连接到 Arduino。这个视频演示向我们展示了这个项目的吸引力。