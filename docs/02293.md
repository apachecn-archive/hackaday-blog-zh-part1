# 简单的 Xbox 360 速射模式

> 原文：<https://hackaday.com/2008/07/28/simple-xbox-360-rapid-fire-mod/>

[https://www.youtube.com/embed/Gjzm1A5-GMk?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/Gjzm1A5-GMk?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

早在五月份我们就提到过 AcidMods 的 [spitfire mod](http://www.hackaday.com/2008/04/21/modchip-your-xbox-360-controller/) 启用了速射(以及其他功能)并且 Xbox Live 检测不到。零件清单很少，只需要一个 PIC16F84A 和一些其他组件，这导致第三方在易贝出售控制器模块套件。AcidMods 团队已经想出了一种新的方法来让[只用一个瞬间开关](http://www.acidmods.com/forum/index.php?topic=17135.0)和必要的电线连接起来就能实现快速射击。你所需要做的就是在控制器 LED 的地线和触发器的中间引脚之间接入开关。唯一的警告是，因为它是硬连线到 LED，您只能在您使用控制器的特定端口上使用 mod。

如此简单的原因是因为 Xbox 360 控制器使用脉宽调制来“调暗”控制器上的 LED，从而产生快速的高/低信号。当瞬时按钮被按下时，它将这个快速高/低信号路由到控制器上的触发输入，然后输入到 Xbox 360。点击阅读链接可以看到更多解释这种攻击的视频。

虽然这种修改无法被 Xbox Live 检测到，但它确实在多人游戏中创造了不公平的优势，并可能导致您的帐户被禁止。

[通过 [Xbox-Scene](http://www.xbox-scene.com/xbox1data/sep/EkEZkyklZyReCevvlg.php)

**相关:** [Xbox 360 黑客](http://www.mahalo.com/Xbox_360_Hacks)， [Xbox 黑客](http://www.mahalo.com/Xbox_Hacks)

*   [永久链接](http://www.acidmods.com/forum/index.php?topic=17135.0)