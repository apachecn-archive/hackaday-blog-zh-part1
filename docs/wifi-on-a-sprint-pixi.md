# Sprint Pixi 上的 WiFi

> 原文：<https://hackaday.com/2010/07/28/wifi-on-a-sprint-pixi/>

[https://www.youtube.com/embed/kpFYoT2lYU0?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/kpFYoT2lYU0?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

Palm Pixi 的 Sprint 版本没有 WiFi 选项，但威瑞森版本(称为 Palm Pixi Plus)有。硬件几乎是一样的，[Gitit20]想出了[如何做一些硬件交换来添加 WiFi](http://forums.precentral.net/palm-pixi/256557-added-wifi-my-sprint-pixi-works-100-a.html)。手机内部的无线电板很容易移除。对 Sprint 无线电电路板的仔细检查显示了一些 WiFi 芯片应该放在的焊盘。威瑞森版本有这种芯片，将无线电板移入 Sprint 手机将启用 WiFi。这是一个严格的硬件攻击，因为设备标识(IMEA)是与主板而不是无线电板配对的。

现在，我们希望看到有人找到 WiFi 芯片，焊接到电路板上，并在操作系统中启用它，这样我们就不需要捐赠手机来实现这一工作。

[谢谢胡安]