# 机器人安全巡逻让天网更近

> 原文：<https://hackaday.com/2009/10/06/atv-brings-skynet-closer/>

![autonomous_atv](img/aea101f46e6bbb5dbbb5bd696868fc4f.png "autonomous_atv")

俄克拉荷马大学的学生组装了一个机器人，它肯定会加入我们未来机器人霸主的行列。这种自主车辆是为了取代既无聊又危险的人工安全巡逻而生产的。为了对大多数地点进行监视，一辆全地形车被用作基地。它可以通过避障系统自行导航，并无线传输视频和音频。休息之后，我们将看看使这一工作的系统。

![autonomous_atv_steering](img/90de1191e8ae3c718e65fb98672c1536.png "autonomous_atv_steering")

该团队通过在全地形车前部安装齿轮马达来实现转向控制。这个转向马达通过链条与安装在转向柱上的齿轮相连接。底盘前部和两侧的声纳传感器有助于避障。这些传感器可以检测地面障碍物，如路缘。

![autonomous_atv_logic_diagram](img/04a0792b4d11de49be38511aed99e3df.png "autonomous_atv_logic_diagram")

车辆使用预编程和基于传感器的行为。首先，巡逻路线被输入程序。一旦释放，机器人将使用这些数据的组合，以及来自 GPS 模块、数字指南针和测距仪的输入来完成任务。所有这些组件都通过板载 [Toughbook](http://en.wikipedia.org/wiki/Toughbook) 与 16 位微控制器结合在一起。无线路由器提供传输数据的连接，如果需要，还提供基于远程操纵杆的控制。

[https://www.youtube.com/embed/P1F0RYnvQkk?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/P1F0RYnvQkk?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

项目开发者[Fares Beainy]和[Sesh Commuri] [向我们发送了他们详细介绍项目的论文](http://blog.mahalo.com/hackaday/misc/IEEE_ATV_Paper_Final.pdf) (PDF)。用来完成这个机器人的现成的、廉价的硬件很好地说明了我们在技术上已经走了多远。用不了多长时间，这种类型的硬件就会出现在你的城镇，为犯罪渣滓(或最近从加工厂逃出来的人类)扫街。