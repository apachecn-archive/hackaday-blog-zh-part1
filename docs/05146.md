# VCR 磁头的螺线管马达

> 原文：<https://hackaday.com/2010/04/06/solenoid-motor-from-a-vcr-head/>

[https://www.youtube.com/embed/3nHX-66PGN0?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/3nHX-66PGN0?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

这里有一个螺线管马达，你可以用一个录像机磁头和一些普通的元件组装起来。它使用一个 LED 和一个光传感器，搭配一个 LM311 比较器来管理电机的开关。当头部转动时，LED 通过一个孔照射在传感器上，并触发 TIP120 晶体管在动力冲程期间打开电机。一旦光束中断，晶体管关闭马达，动量带动马达旋转，直到下一个动力冲程启动。

我们常说“为什么”是个错误的问题。[Bd5940]一定也有同样的感觉，因为他在结束视频时说:“这没有用，但绝对是一段对话”。是的，[我们在](http://hackaday.com/2009/12/30/simplest-most-useless-machine/)之前见过。

[谢谢詹姆斯]