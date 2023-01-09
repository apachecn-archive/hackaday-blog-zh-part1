# 添加新功能并从沙发上控制 Kinect

> 原文：<https://hackaday.com/2012/03/22/adding-new-features-and-controlling-a-kinect-from-a-couch/>

![](img/4881f6eb0e56881f609681ab607c130f.png "media center")

Kinect 发布后，微软展示了它的金童，作为用户界面技术革命的开端。骨骼和运动检测承诺了一个未来的、挥手的“少数派报告风格”界面，在那里你的整个身体控制着一台计算机。预期并没有完全实现，但[史蒂夫]和他在 Amulet Devices 的同事们已经极大地改善了 Kinect 的骨骼识别能力，因此人们[可以坐着](http://www.amuletdevices.com/index.php/Features/kinect.html)使用 Kinect。

在家庭影院中使用 Kinect 进行少数报告用户界面的一个巨大缺点是，微软的骨骼识别在坐下时不能很好地工作。[史蒂夫]没有依赖 Kinect 自带的内置骨骼识别，而是使用 [Harr 分类器](http://opencv.willowgarage.com/wiki/FaceDetection)进行了自己的骨骼检测。

检测类 Harr 特征已经用于计算机视觉技术的许多应用中；这是一种用简单的相机检测面部和身体位置的很好的、计算量不是很大的方法。该软件需要培训，而[史蒂夫]的应用花了几天时间自行编程。不过，结果是值得的:Kinect 现在可以识别躺在沙发上的史蒂夫挥舞手臂的动作。

为了不超越自己，[史蒂夫]还在他的 Kinect 家庭影院控制器中加入了语音识别功能；他的雇主做了一个语音识别遥控器。识别软件看起来工作得很好，即使是带着[史蒂夫]磨砺了一辈子的渴望的苏格兰口音。

[史蒂夫]的雇主正在分发他们改进的 Kinect 软件,该软件可以在 Xbox 和 Windows Kinects 上运行。如果你打算用 Kinect 做一些我们今天早些时候[提到的 SDK 和 API 没有提供的事情，这肯定会是一个无价的资源。](http://hackaday.com/2012/03/22/kinect-for-windows-resources/)

休息过后，你可以看看[史蒂夫]的新 Kinect 软件演示。

[https://www.youtube.com/embed/g-2izbHeN-k?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/g-2izbHeN-k?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)