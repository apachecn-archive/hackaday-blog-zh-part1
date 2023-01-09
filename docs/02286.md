# 同步萤火虫 ng

> 原文：<https://hackaday.com/2008/07/28/synchronizing-fireflies-ng/>

来自 Tinkerlog 的[Alex]带着[同步萤火虫 NG](http://tinkerlog.com/2008/07/27/synchronizing-fireflies-ng/) 重访了一个老项目。他着迷于萤火虫如何以相同的速度眨眼并相互同步，于是他制作了一个数字版本。每个板都有一个 RGB LED 和一个光电晶体管或光敏电阻。乒乓球被用作扩散器。闪烁速率由 ATtiny13v 控制。板电源可以菊花链连接，但每个萤火虫微尘独立运行。微控制器有一个固定的闪光频率，并监测其他闪光。它试图通过提前闪烁来同步。LED 的颜色表示 firefly 对其当前同步的满意程度。你可以在下面看到八只萤火虫试图自我组织的视频。

*   [永久链接](http://tinkerlog.com/2008/07/27/synchronizing-fireflies-ng/)