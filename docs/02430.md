# 以神奇的方式重启 SysRq

> 原文：<https://hackaday.com/2008/08/24/rebooting-the-magic-sysrq-way/>

![](img/0c895831880675d2f5629c7af367d10d.png)
【Cory Wright】分享了如何[远程重启有故障硬盘的系统的技巧](http://www.linuxjournal.com/content/rebooting-magic-way)。神奇的 SysRq 键是一个 linux 内核特性，它允许您执行许多有趣的操作。如果您在磁盘出现故障的远程系统上工作，您将无法访问重新启动或关机命令。不过，您可以在/proc 中向神奇的 SysRq 设备发出击键命令，这样就可以直接向内核发送硬重启，而不需要访问磁盘。

维基百科条目包括一个关于如何正确地[重启一台冻结的机器](http://en.wikipedia.org/wiki/Magic_SysRq_key)的便利提示。这应该可以让你下次不用再检查了。

[图片:[约书亚·戴维斯](http://flickr.com/photos/articnomad/16153058/)

*   [永久链接](http://www.linuxjournal.com/content/rebooting-magic-way)