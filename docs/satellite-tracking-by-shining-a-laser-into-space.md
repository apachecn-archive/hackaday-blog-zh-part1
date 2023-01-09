# 通过向太空发射激光进行卫星跟踪

> 原文：<https://hackaday.com/2011/06/11/satellite-tracking-by-shining-a-laser-into-space/>

[Shingo Hisakawa]提交了一份关于一个叫做 Levistone 的小巧盒子的建议，这个盒子用激光跟踪国际空间站。他的视频日志记录了这个伟大的小项目的所有步骤。

[Shingo]最初计划从 NORAD 下载轨道数据，并将其发送到带有以太网、GPS 和指南针模块的 ArduinoBT 板上。在最初的计划中，Arduino 会进行轨道计算，并使用一些伺服系统来指向激光。让 Arduino 做所有的工作并不太成功，所以 Android 手机代替了 GPS、指南针和网络连接。使用全球定位系统和轨道要素计算国际空间站位置的任务被转移到亚马逊 EC2 云上。最终产品看起来很棒，即使不可能为视频记录光束。

凭借从世界上任何一点计算国际空间站方位角和仰角的能力，[Shingo]提出了 [SightSpaceStation](http://www.sightspacestation.com/index.htm) ，这是他的数据和谷歌地图的巧妙结合。也有 iOS 和 Android 应用程序用于增强现实中的一个不错的作品。这是一个伟大的项目，将真正补充我们几天前报道的[国际空间站台灯](http://hackaday.com/2011/06/09/iss-lamp-tells-you-when-to-look-up/)。