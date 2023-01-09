# 手机控制的家庭

> 原文：<https://hackaday.com/2009/09/06/cellphone-controlled-home/>

[https://www.youtube.com/embed/exTpD0--BCo?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/exTpD0--BCo?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)
【Tixlegeek】用一个摩托罗拉 68HC705J1 开发板通过手机远程控制[他的家](http://ns7.freeheberg.com/~tixlegee/dotclear/index.php?2009/09/03/181-tixlegeek-s-workshop-telecommander-son-appart-avec-un-telephone-mobile)。上面的视频以及[Tixlegeek]的网站都是法语的，尽管视频有字幕。开发板(称为[erms 125](http://www.ermes.free.fr/kier125.pdf))由 PIC 外部控制。它有一排发光二极管，显然还有几个高压继电器。PIC 通过串行接口连接到笔记本电脑。笔记本电脑运行着一个小型网络服务器，它使用 CGI 从网页上控制图片。这个系统允许[Tixlegeek]从他的网络功能手机登录网页，点击几个按钮，并通过 PIC 控制的继电器(通过笔记本电脑的串行信号)打开或关闭电器。