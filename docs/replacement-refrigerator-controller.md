# 替换冰箱控制器

> 原文：<https://hackaday.com/2009/12/26/replacement-refrigerator-controller/>

![](img/fbcef947085f54d162d32fe6e06a43b8.png "arduino-fridge-controller")

[Michael]找到了一台冰箱，他打算用来储存啤酒，但发现它一直在运转。他和他的朋友道格没有购买新的恒温器，而是着手为冰箱制造一个基于 Arduino 的控制器。

完成的项目将切换 240v，因此他们使用变压器为逻辑电路供电，使用固态继电器处理负载切换，使用 Dallas 1820 获取温度数据。因为 Arduino 提供了比普通恒温器更多的功能，他们还决定通过增加一个以太网屏蔽来挖掘其潜力。我们将 Arduino 视为原型设备，这些人也是如此。一旦他们的第一个 PCB 原型中的错误被解决，电路将使用 ATmega328 并废除 Arduino。

[via [@littlebirdceo](http://post.ly/FpQO)