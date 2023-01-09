# Arduino 上的基本编程

> 原文：<https://hackaday.com/2011/08/28/basic-programming-on-an-arduino/>

[Mike]发来了他正在做的一个项目——一个适合 Arduino 的基本解释器的端口。该代码旨在成为 68000 的 [Tiny BASIC 的忠实端口，并且符合 Tiny BASIC 的形式，它适合 Arduino 非常有限的 RAM。](http://members.shaw.ca/gbrandly/68ktinyb.html)

忠实于 Tiny BASIC 的汇编根，[Mike]的 C 移植大量使用了“无限滥用”的 goto 语句。Kernighan 和 Ritchie 自己说，“包含 goto 代码总是可以不用 goto 来编写”，但是[Mike]发现使用 goto 为基本代码留下了更多的空间。基本解释器占用了大约 600 字节的 Arduino RAM，剩下大约 1.4 kB 用于基本代码。不多，但比最低端的[基本款](http://www.parallax.com/Store/Microcontrollers/BASICStampModules/tabid/134/ProductID/3/List/1/Default.aspx?SortField=UnitCost,ProductName)多。

[Mike]说他开始这个项目是为了看看“老胡子”是如何用几 kB 的内存变出这么多令人印象深刻的程序的。Tiny BASIC 最初是为配备 256 *字节*内存的 [Altair 8800](http://oldcomputers.net/altair.html) 设计的，所以看起来非常合适。现在，我们所知道的是，我们将花周末的时间翻看我们的*多布博士的日记*。