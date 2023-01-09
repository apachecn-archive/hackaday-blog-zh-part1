# GIFAR 图像漏洞

> 原文：<https://hackaday.com/2008/08/04/the-gifar-image-vulnerability/>

NGS 软件公司的研究人员想出了一种在图片中嵌入恶意代码的方法。当被查看时，图片可能会向攻击者发送查看者的凭据。像脸书和 Myspace 这样的社交网站尤其危险，但是研究人员表示，任何包含登录信息和用户上传图片的网站都容易受到攻击。这甚至包括一些银行网站。

攻击只是一个 GIF 图片和一个 JAR (Java applet)的混搭。恶意 JAR 被编译，然后与来自 GIF 的信息相结合。GIF 部分欺骗浏览器将其作为图片打开并信任其内容。事实是，Java VM 识别 JAR 部分并自动运行它。

研究人员声称，有多种方法可以应对这一漏洞。Sun 可以限制他们的虚拟机或 web 应用程序不断检查和过滤这些混合文件，但他们表示，这确实需要作为浏览器安全问题来解决。他们认为不仅仅是图片有风险，几乎所有的浏览器内容都有风险。如何制作这些 GIFARs 的更多细节将会在本周拉斯维加斯的黑帽大会上公布。

*   [永久链接](http://www.infoworld.com/article/08/08/01/A_photo_that_can_steal_your_online_credentials_1.html)