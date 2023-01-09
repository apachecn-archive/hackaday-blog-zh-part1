# 无人驾驶车辆软件 OpenVulture

> 原文：<https://hackaday.com/2009/02/06/openvulture-software-for-unmanned-vehicles/>

![barbie](img/93d4e96ab280f16d2f9e8649fedfc212.png "barbie")

ShmooCon 的第一个演讲是【伊森·奥图尔】和【马特·戴维斯】展示他们的 [OpenVulture](http://www.757labs.com/projects/openvulture/ "757 Labs - OpenVulture - Multi-Platform Hardware Automation") 无人驾驶汽车软件。在最初阶段，他们只是计划为无人驾驶飞行器构建软件，但意识到通过适当的规划，它可以用于任何交通工具:飞机、汽车、船只和潜艇(或者更具体地说，他们的芭比动力轮)。该软件分为两部分。首先是一个库，可以让你与车辆的每个模块进行通信。后半部分是实际的导航软件。

他们花了很多时间采购硬件模块。他们正在寻找工作良好、不太贵、即插即用的产品。对于他们的主处理器，他们想要的不是微控制器，可以运行完整的 Linux 系统。基于 ARM 的 NSLU2 NAS 似乎是目前的领跑者。你可以在他们的网站上找到开源软件和支持模块的描述。

他们现在正在制造第一架无人驾驶飞机。一个有 12 英尺的翼展，以获得更大的升力和稳定性。我们在过去报道过基于 Arduino 的 [Ardupilot](http://hackaday.com/2008/07/03/ardupilot-arduino-based-uav-autopilot/ "arduino based UAV autopilot  - Hack a Day") 和[其他无人机](http://hackaday.com/2007/12/27/24c3-build-your-own-uav/ "24C3 Build your own UAV  - Hack a Day")。