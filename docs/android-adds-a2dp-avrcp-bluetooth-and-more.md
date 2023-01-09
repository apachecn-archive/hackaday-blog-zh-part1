# Android 增加了 A2DP，AVRCP 蓝牙等等

> 原文：<https://hackaday.com/2008/12/19/android-adds-a2dp-avrcp-bluetooth-and-more/>

![tmobileg1](img/50dd2c797a0c9b418c2209459ae06ff5.png "tmobileg1")

在致力于开源 Android 的同时，该团队继续在他们自己的私人开发分支中开发新功能。这些现在已经在“纸杯蛋糕”分支公开发表[。包括许多有趣的新特性和错误修复。休息之后，我们将对许多重要的新增内容进行总结。](http://source.android.com/roadmap/cupcake)

A2DP 和 AVRCP [配置文件](http://en.wikipedia.org/wiki/Bluetooth_profile "Bluetooth profile - Wikipedia, the free encyclopedia")都被添加到蓝牙堆栈中。这意味着支持立体声耳机和远程控制。没有添加拨号网络，但在 USB 小工具框架支持方面做了初步工作，这意味着未来的设备对主机设备来说可能只是一个以太网接口。

该浏览器已经升级到 11 月发布的 WebKit，带有优化的 JavaScript 引擎 [SquirrelFish](http://trac.webkit.org/wiki/SquirrelFish "SquirrelFish – WebKit") 。浏览器中的复制/粘贴和 5 倍的绘图速度也增加了。轨迹球现在加速滚动。

硬件加速的视频录制和回放，一个在最初的 T-Mobile G1 版本中经常被提及的疏忽，终于出现了。屏幕键盘和预测文本的框架正在开发中。Android 允许你运行后台进程，用户会很高兴知道现在有一个进程管理器。最后，一个新的 Linux 2.6.27 内核和最少解释的附加功能“基本 x86 支持”完善了这个分支。

虽然这里有许多好的改进，但没有迹象表明 G1 用户何时会看到它们，也没有迹象表明 Android Dev Phone 1(ADP1)的所有者何时能够自己开发这个版本。[Disconnect] [指出](http://www.gotontheinter.net/content/oooh-hidden-gem-cupcake-sources)该分支中还有一些公告中没有提到的其他亮点，比如[安装加密的 e2fs 卷](http://android.git.kernel.org/?p=platform/system/core.git;a=blob;f=mountd/ASEC.c;h=3d8e50e0ae47c6a5b7e5f6ac2ac225f867434b59;hb=cupcake)，这可以在 SD 卡上安装应用程序。

[照片: [tnkgrl](http://flickr.com/photos/tnkgrl/2963841190/in/set-72157608262752711/)

[via[GotOnTheInter.Net](http://www.gotontheinter.net/content/google-releases-updated-source-treefinally)