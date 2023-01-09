# 让相框里有光

> 原文：<https://hackaday.com/2011/02/24/let-there-be-light-inside-picture-frames/>

![](img/493fb2a6b75577045a09c1cd7fd85a2a.png "lighted-picture-frame")

[Limpkin]在巴厘岛的时候捡到了一幅美丽的佛陀的画，因为他认为它在不同颜色的灯光下会有很好的反应。他的总体目标是[创造一个内置发光二极管的相框](http://www.limpkin.fr/index.php?post/2011/02/24/How-to-[use/solder/waste/be-patient-with]-576-leds!)。该项目的主要设计规范是提供一个不会照射到观众眼睛的间接光源。他开始使用 SolidWorks 为他的模型设计一个框架。最终设计有一个独立的轨道，每个二极管都有小分压器。

在数控机床上工作了大约四个小时后，是时候开始焊接了。[Limpkin]手头有 576 个 RGB LEDs。他不想单独驱动它们，只是想独立控制每种颜色。这使得焊接更容易，因为只有三个 MOSFETs 来驱动每种颜色。最终产品看起来很棒，可以显示任何颜色的光。对于 50 小时的焊接来说还不错。