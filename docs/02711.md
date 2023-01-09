# 闪烁 LED 电路

> 原文：<https://hackaday.com/2008/10/30/flickering-led-circuit/>

![](img/4f8cf9f6467cb71d374f61179c2e13ef.png "boardfinal")

这是一个简单的万圣节庆祝项目。有一天，在查看我们的万圣节装饰品盒子时，我们注意到一个南瓜灯的白炽灯泡被烧坏了。我们没有简单地更换过时的灯泡，而是决定基于[这个邪恶的疯狂科学家实验室的设计](http://www.evilmadscientist.com/article.php/darkpumpkin)用两个黄色发光二极管构建一个小型黑暗探测电路。在成功构建电路后，我们将项目向前推进了一步，集成了 Atmel ATtiny13 微控制器。该代码随机打开和关闭发光二极管，产生闪烁效果，并基于该指令产生[。下面是我们在 EAGLE 中创建的原理图和零件清单。](http://www.instructables.com/id/SUTEZKVFKD1M38Q/)

[![](img/3c8f5d4b65f8d26ca6b661beee5fb798.png "board2")](http://hackaday.com/files/2008/10/board2.jpg)

*   T2 t1:2n 3904 晶体管
*   T3: LTR-3208E 光电晶体管
*   LED1、LED 2:10 毫米漫射黄色 led
*   R1:5k 欧姆电阻器
*   R2，R3:50 欧姆电阻
*   IC1: Atmel ATtiny13
*   来源:2xAA 电池盒，带电池