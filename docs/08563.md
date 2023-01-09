# 深入挖掘 Neato 的激光雷达模块

> 原文：<https://hackaday.com/2011/09/12/digging-deep-into-the-neatos-lidar-module/>

[Hash]正在竭尽全力[了解他的 Neato XV-11 激光雷达](http://random-workshop.blogspot.com/2011/09/neato-xv-11-lidar-disassembled.html)(死链；[互联网档案馆](http://web.archive.org/web/20140212000416/http://random-workshop.blogspot.com/2011/09/neato-xv-11-lidar-disassembled.html)。我们最近看到了他在 XV-11 平台上的工作，在那里[他将真空吸尘器的垃圾箱用作模块化硬件外壳](http://hackaday.com/2011/08/30/dustbin-computer-lets-you-clean-and-prototype-with-a-neato-xv-11/)。这个黑客是一个硬件探索，旨在找出如何建立一个等价的开放硬件版本。

激光雷达模块由两大块组成；上面看到的激光和光学组件以及传感器板。[Hash]将它放在显微镜下，以便更好地观察行扫描成像仪。放大帮助他找到了模具上的公司名称，这个特殊的零件是由 Panavision 制造的。他通过计算焊线和焊线之间的像素来推测出实际的模型，从而很好地推测出分辨率。他非常确定这是一台 DLIS-2K，并在他的帖子中链接到应用笔记和数据表。传感器右侧的芯片是 TI 数字信号处理器。

将它重新组装在一起可能会很困难，因为不可能将光学元件完全重新校准——模块需要重新校准。[Hash]计划调查校准程序是如何工作的，他会发布他发现的任何东西。休息之后，看看他对视频中撕裂的描述。

[https://www.youtube.com/embed/sgRqyUUEFG8?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/sgRqyUUEFG8?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)