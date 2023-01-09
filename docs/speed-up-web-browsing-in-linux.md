# 加速 Linux 中的网页浏览

> 原文：<https://hackaday.com/2011/01/11/speed-up-web-browsing-in-linux/>

在现代计算机系统中，信息的最大瓶颈往往是与硬盘的通信。与 RAM 速度相比，高寻道时间和相对较慢的传输速率会很快累积起来。当 RAM 空间和成本非常昂贵时，这是一种必要的邪恶，但现在在笔记本电脑上看到 4GB 的 RAM 并不罕见，甚至在台式机上看到 12GB。对于主要使用计算机浏览互联网(无论是工作、写文章还是 lolcats)并且有一些额外 RAM 的用户来说，将浏览器缓存从硬盘移动到 RAM 无疑是提高速度的一个选择。

在 Linux 系统(特别是 Fedora 和 Ubuntu 系统)中，对于 Chrome 和 Firefox，这可以通过创建一个更大的 ramdisk，在引导后挂载 ramdisk，然后将选择的浏览器设置为使用该 ramdisk 作为缓存来实现。要做到这一点，必要的命令是[在互联网上随时可用](http://www.linuxreaders.com/2011/01/11/firefox-chrome-cache-on-ram-drive-fedora-ubuntu/) ( [互联网档案](https://web.archive.org/web/20110824012407/www.linuxreaders.com/2011/01/11/firefox-chrome-cache-on-ram-drive-fedora-ubuntu/))，这使得生活变得简单。使用内存磁盘提升性能并不是浏览器独有的，也可以用于其他软件，例如 [Nagios](http://lickthesalt.com/2009/04/19/tweaking-nagios-for-performance/) 。

我们之前已经介绍过一个名为[espe rance DV](http://hackaday.com/2008/11/20/faster-browsing-with-ram-disks/)的工具，用于在 Mac OSX 中将缓存转移到 RAM，对于任何感觉被忽略的 Windows 用户，有一些方法可以让 Firefox [屈从于你的意愿](http://windowstipoftheday.blogspot.com/2010/11/firefox-moving-your-cache-to-ram.html)。显然，您会看到 RAM 使用的增加(咄)，但这不应该是一个问题，除非您用完了系统上的空闲 RAM。记住，空闲内存是浪费的内存。