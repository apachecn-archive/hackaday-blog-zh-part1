# 在 Gmail 上运行 Linux

> 原文：<https://hackaday.com/2005/04/14/run-linux-on-gmail/>

![Linux Code](img/42cf7cf2cfe6c89fe4e9fb12f499284c.png)

是的，你没看错。可以在 gmail 上安装 linux。richard jones 写了一些 python，可以让你在 gmail 中挂载 linux。您可以使用各种 unix 命令与 gmail 通信，如 ls、rm、grep、cp 等。这是一个正在开发的项目，但它非常酷，基本上允许您使用 2gb 的虚拟驱动器。你需要准备好 [libgmail](http://libgmail.sourceforge.net/) 和 [FUSE](http://sourceforge.net/projects/avf) 才能让它正常工作。libgmail 与 gmail 通信，而 FUSE 提供文件系统。试试看，看起来进展得很顺利。

*   [永久链接](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html)