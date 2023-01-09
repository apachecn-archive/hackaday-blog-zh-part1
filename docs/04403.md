# 电池容量测试仪

> 原文：<https://hackaday.com/2009/11/11/battery-capacity-tester/>

![battery-capacity-tester](img/075788ef0c36400d27abad123f5b6c42.png "battery-capacity-tester")

【Moris_zen】造了一个[装置，可以精确测量电池的容量](http://www.instructables.com/id/Arduino-True-Battery-Capacity-Tester-Li-IonNiMH/)。他需要对他在遥控飞机上使用的电池进行精确测量。知道放电时间使他能够在友好的天空飞行，同时避免因失去通信而坠毁。

他基于 Arduino 平台进行测试。他没有使用预先构建的 Arduino 板，而是参考了[开源原理图](http://arduino.cc/en/Main/ArduinoBoardDiecimila)，并根据自己的需求用组件构建了该设备。当电池加入电路时，他的解决方案会根据电压自动检测电池类型(锂离子电池、镍氢电池等)。然后，它使用一个 2.2 欧姆的电阻和 ADC 测量来使电池经历一个放电周期。字符显示器显示状态信息，并能够使用计算机绘制数据图表来跟踪放电信息。

除了闪烁的 LED，这是他的第一个 Arduino 项目。这是对平台的一个很好的利用，并且比我们介绍过的其他解决方案更加自动化。