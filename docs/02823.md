# 使用 RAM 磁盘加快浏览速度

> 原文：<https://hackaday.com/2008/11/20/faster-browsing-with-ram-disks/>

![esperancedv](img/8d319d8b8ab14315c12ba5f9bdbf13b6.png "esperancedv")

一位同事今天找到我们，想知道他们是否可以使用三星新发布的 256GB 固态硬盘来提升性能。他们的大部分工作都是在浏览器中完成的，所以我们说“不”。他们只有在读/写大文件时才会看到好处。他们的系统有足够的内存，我们决定采用不同的方法。通过在 RAM 中创建文件系统，您可以比在普通硬盘上更快地读写文件。我们决定将浏览器的文件缓存放在 RAM 中。

我们在 OSX 安装了 [Espérance DV](http://www.mparrot.net/index.php?page=downloads&lang=en) 偏好设置面板，以便于创建 RAM 磁盘。设置起来真的很简单。只需选择多少空间，你想专用于磁盘，并创建它。您可以让 Espérance DV 在启动时重新创建 RAM 磁盘，甚至让它自动从磁盘映像恢复。有一个复选框可以将 Safari 的 Web 缓存移动到 RAM 磁盘，这将创建必要的符号链接。您也可以使用它来加速 Xcode 的构建。移动 Firefox 的缓存相当简单:

`$ rm -r ~/Library/Caches/Firefox
$ ln -s /Volumes/RamDisk/Firefox ~/Library/Caches/Firefox`

由于浏览器不必在每次页面加载时都撞击硬盘，因此性能会更快。 [Xbench](http://www.xbench.com/) 说我们从 RAM 中随机读取的速度现在是 86.19 MB/秒，而不是高速缓存在硬盘上时的 0.61 MB/秒。

我们立即开始寻找将整个操作系统放入 RAM 的方法；Tin Hat 是 Linux 的一个版本，可以做到这一点。

我们对 RAM 磁盘浏览器升级的结果非常满意。如果你在 Windows 中有类似的经历，请在评论中告诉我们。