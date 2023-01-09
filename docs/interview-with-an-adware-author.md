# 采访一位广告软件作者

> 原文：<https://hackaday.com/2009/01/14/interview-with-an-adware-author/>

![toolbars2](img/7baaa807de865d425eb811452cea95bd.png "toolbars2")

Philosecurity 对[Matt Knox] 进行了一次采访，Matt Knox 是 Direct Revenue 的前程序员，Direct Revenue 是一家广告软件公司，2006 年被纽约州州长埃利奥特·斯皮策起诉。采访中包含了一些关于广告软件代码如何在内部工作的有趣细节:它创建了一个浏览器助手对象，然后通过创建一个轮询器来确保浏览器助手对象保持运行，每十秒钟检查一次，如果浏览器助手对象停止运行，则重新生成浏览器助手对象。轮询器巧妙地通过利用 Windows 的创建远程线程功能将自己作为一系列线程而不是可执行文件来运行，从而部分地掩盖了自己。

采访中真正吸引人的是[诺克斯]如何挑战你最初对他是一个彻头彻尾的卑鄙小人的怀疑；他开始编写垃圾邮件过滤软件，被 Direct Revenue 雇用来进行流量分析，开始编写小代码来改进广告软件，最终陷入了代码的泥沼。[诺克斯]指出，如果你把普通人做的事情分成足够小的块，然后逐渐引入，你可以让他们做令人难以置信的令人讨厌的事情。

[via [蜡质](http://waxy.org/links/)

[图片:[xcabable](http://flickr.com/photos/xcaballe/319711606/)