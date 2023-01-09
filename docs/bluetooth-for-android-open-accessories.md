# Android 开放式配件蓝牙

> 原文：<https://hackaday.com/2011/10/29/bluetooth-for-android-open-accessories/>

![](img/020c7f3e5f7c3f1f8958b362c69b72aa.png "bluetooth")

Android 开放式配件套件 IOIO 分线板的首席开发人员[Ytai]发现了如何通过蓝牙无线控制 Android 手机上的任何东西。

当[Ytai] [首次宣布用于 Android 设备的 IOIO 分线板](http://ytai-mer.blogspot.com/2011/04/meet-ioio-io-for-android.html)时，他帖子上的一位评论者说，标准蓝牙加密狗可以代替手机和 IOIO 之间的 USB 电缆。家庭自动化项目和机器人的无线控制是一个太好的想法，不能放弃，所以[Ytai]投入到这个新的蓝牙项目中。

在从 DealExtreme 获得一个廉价的蓝牙加密狗后，[Ytai]找到了 [btstack](http://code.google.com/p/btstack/) ，这是一个轻量级的蓝牙堆栈，非常适合嵌入式环境。处理无名蓝牙适配器的 USB 驱动程序并不容易，但经过几个漫长的夜晚后，[Ytai]取得了胜利。

他还有几个问题要克服。也就是说，支持不仅仅是 IOIO 板可用的环境。[Ytai]正在考虑增加对 WiFi 加密狗的支持，这是我们希望看到的。休息之后，请查看[Ytai]的伺服系统无线控制演示。

[https://www.youtube.com/embed/cFlJm86Qtuk?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/cFlJm86Qtuk?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)