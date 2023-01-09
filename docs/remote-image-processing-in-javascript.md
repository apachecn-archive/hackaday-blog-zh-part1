# JavaScript 中的远程图像处理

> 原文：<https://hackaday.com/2009/03/07/remote-image-processing-in-javascript/>

[https://www.youtube.com/embed/u3_cFel26J8?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/u3_cFel26J8?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

[Tom]来信告诉我们他的运动检测 JavaScript 项目。它将我们最近讨论过的两个观点联系在一起。第一个是在浏览器中使用 Canvas()进行图像处理，我们已经看到[在验证码破解](http://hackaday.com/2009/01/23/megaupload-captcha-cracking-in-javascript/ "MegaUpload captcha cracking in JavaScript  - Hack a Day")中使用了它。第二种是将繁重的处理任务交给浏览器，我们最近在 [MapReduce 实现](http://hackaday.com/2009/03/03/distributed-computing-in-javascript/ "Distributed computing in JavaScript  - Hack a Day")中看到了这一点。[Tom]正在使用 JavaScript 比较连续的图像，以确定是否有任何运动。他这样做是作为 [MJPG-Streamer](http://mjpg-streamer.wiki.sourceforge.net/) 的一部分，这是一个从网络摄像头传输图像的程序。它可以在非常有限的硬件上运行，但图像处理可能非常密集。在浏览器中进行图像处理弥补了这一限制，意味着不必编写定制的客户端程序。你可以[在这里找到代码](http://mjpg-streamer.svn.sourceforge.net/viewvc/mjpg-streamer/mjpg-streamer/www/javascript_motiondetection.html?revision=83&view=markup&pathrev=83 "SourceForge.net Repository - [mjpg-streamer] View of /mjpg-streamer/www/javascript_motiondetection.html")和一个关于概念验证的 [PDF。](http://mjpg-streamer.wiki.sourceforge.net/space/showimage/Distributed+Computing+and+Image+Processing+in+JavaScript.pdf)