# 连接数字旋转开关

> 原文：<https://hackaday.com/2009/08/27/nterfacing-a-digital-rotary-switch/>

![digital_rotary_switch](img/2ad81fe16041160b921f2e10850ef6ea.png "digital_rotary_switch")

[hw640]整理了一份关于如何与数字旋转开关连接的详细说明。这些[数字光电编码器](http://search.digikey.com/scripts/DkSearch/dksus.dll?lang=en&site=US&WT.z_homepage_link=hp_go_button&KeyWords=61C22-01-04-02&x=0&y=0)只有两个输出，四个可能的逻辑电平(00，10，11，01)。开关的相对位置无关紧要，但重要的是旋转方向。

短路和脏污:开关的 2 个输出引脚中的每一个都连接到微控制器上的引脚变化中断。每当开关移动时，它会在两个引脚中的一个引脚上产生上升沿或下降沿；两个边沿都会导致中断。通过检查哪个引脚导致中断，然后比较中断后两个引脚的逻辑电平，我们可以确定开关旋转的方向。

虽然这种解释使用了一个 [PIC](http://www.microchip.com) 和用 [PicBasic Pro](http://www.melabs.com/products/pbp.htm) 编写的代码，但概念是抽象讨论的，很容易适用于 [AVR](http://hackaday.com/2009/01/18/attiny-breadboard-headers/) 或您选择的其他微控制器。