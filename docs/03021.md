# 零件:数字接近传感器(夏普 GP2Y0D02)

> 原文：<https://hackaday.com/2009/01/05/parts-digital-proximity-sensor-sharp-gp2y0d02/>

[https://www.youtube.com/embed/TqOzmGNBgJE?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/TqOzmGNBgJE?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

GP2Y0D02 是一个红外[接近传感器](http://en.wikipedia.org/wiki/Proximity_sensor)，其探测范围延伸至 80 厘米。这种类型的传感器可以用来建立机器人的防撞系统。我们将使用一个电阻和一个万用表来演示这款传感器。

![2y0d02b](img/bc76e040392eb0a3d91ecce4b21b50fb.png "2y0d02b")

**夏普 GP2Y0D02 固定式 80cm 红外接近探测器(Digikey #[425-2064-ND](http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&name=425-2064-ND)****，$14.38)。** **[数据表](http://document.sharpsma.com/files/GP2Y0D02YK-DATA-SHEET.PDF) (PDF)。**

GP2Y0D02 需要 5 伏电源(未显示)。电源与地之间的 0.1uF 旁路电容(C1)是个好主意，但我们在演示中没有使用。当没有检测到物体时，[集电极开路输出](http://en.wikipedia.org/wiki/Open_collector)(引脚 1)拉至地，当检测到物体时，12K [上拉电阻](http://en.wikipedia.org/wiki/Pull-up_resistor) (R1)保持信号为高。

在演示中，我们将传感器的输出连接到万用表。当传感器前面没有东西时，检测器保持低输出(0.40 伏)。当我们将 PCB 放在传感器前面时，输出变为高阻抗，上拉电阻(R1)保持信号为高电平(5v)。

*为什么要开集电极？*

集电极开路输出不会在高电平和地电平之间切换，而是在地电平和未连接之间切换。未连接状态也称为高阻抗，对输出没有影响，允许信号线浮动。对于大多数返回快速变化值的微控制器来说，这是一种未定义的状态，因此我们使用一个电阻(R1)来保持信号为高电平。集电极开路输出克服流过电阻的少量电流，记录低电平状态。如果没有这个电阻，输出将永远不会达到合适的高电平状态。

当多个传感器需要共享同一个微控制器引脚时，集电极开路输出非常有用。多个传感器向同一个微控制器引脚输出高电平通常被认为是一种不好的做法，可能会损坏电路的某些部分。然而，多个集电极开路输出只能切换到地；单个电阻保持信号为高电平。在多个 gp 2 y0d 02 的情况下，只有当所有连接的传感器检测到物体并切换到高阻抗状态时，信号才会为高。

喜欢这个帖子？查看您可能错过的[部分帖子](http://hackaday.com/category/parts/)。