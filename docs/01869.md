# 使用 Roombas 进行游戏

> 原文：<https://hackaday.com/2008/06/04/gaming-with-roombas/>

昨天我们看了《T2》中的吃豆人 Roomba casemod 。在视频中，创作者[ Ron Tajima] 表示有兴趣看到 Roombas 参与现实生活中的游戏。所以我们做了一些调查，发现了一些用于有趣的增强现实游戏的[。来自布朗大学的这些经过改造的 Roomba Create 单元可以玩各种游戏，比如 tag，其潜在目标是开发更智能的机器人。](http://robotics.cs.brown.edu/projects/embodied_gaming/)

该设置由 Java 驱动的客户机/服务器配置组成。游戏服务器协调小型通用机器人车辆(SmURVs ),并建立一个事件数据库以备将来使用。玩家还可以通过 Java [远程呈现](http://www.mahalo.com/Telepresence)客户端控制机器人。

这些装置本身由 iRobot Create T1 组成，顶部绑着一台迷你 ITX 电脑。他们运行 Linux，通过 WiFi 与服务器和玩家交流。他们还有一个红外发射器，在游戏中用来“射击”其他单位。

游戏中，服务器充当裁判，而人类仅充当指导者。当机器人无法根据它们现有的决策政策数据库做出反应时，人类就开始发挥作用。通过客户端，玩家能够准确地看到机器人看到的 3D 叠加效果。游戏的未来计划包括移除摄像机视图，只替换为这些覆盖图。该项目的最终目标之一是创造一个 24/7/365 的游戏体验，类似于今天 MMOs 和 Xbox Live 应用程序中的体验。

*   [永久链接](http://robotics.cs.brown.edu/projects/embodied_gaming/)