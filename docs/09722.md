# [迪克·特雷西]的手表有夜视功能

> 原文：<https://hackaday.com/2012/02/20/dick-tracys-watch-gets-night-vision/>

![](img/f826679d7a74e09a3bb8e0eaf748a599.png "watch")

在拿到一款支持安卓系统的手表后，[Paul]想测试一下他的新硬件的极限。我们将假设他对他的购买很满意，因为他完成的构建将数据从[微软 Kinect 发送到他的手表](http://www.youtube.com/watch?v=O7VT00YN6vY)，使其成为夜视间谍手表。

[保罗]的新玩具是一款 [WIMM One](http://www.wimm.com/wimm_preview.html) 安卓手表，配有 wi-fi 和安卓 2.1 版本。为了让他的手表具有夜视功能，保罗桌子上的 Kinect 使用 [OpenCV](http://opencv.willowgarage.com/wiki/) 向他的手表传输深度数据。结果是一个在黑暗中收集深度数据并将其发送到[Paul]手表的相机。

每当检测到入侵者的移动，[Paul]的手表就会震动，并显示从 Kinect 上拍摄的深度图像。如果入侵者靠近 Kinect，人脸会被采集并发送到手表。为了让闯入者离开房间，[保罗]可以点击他的表盘，打开远程警报，发出闯入者警报。这是一个非常简洁的项目，在几年前是不可想象的。