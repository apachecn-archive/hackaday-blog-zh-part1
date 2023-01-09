# PHP 运行时重写，由脸书？

> 原文：<https://hackaday.com/2010/02/03/php-runtime-rewritten-by-facebook/>

![](img/c24a719faf6c01cdaa75e921c28fc317.png "I'm more of a classic rock fan.")

是的，这是真的。脸书已经完全重写了 PHP 运行时，使其更快更有效，并且完全开源。命名为 HipHop，它被描述为一个源代码转换器，将 PHP 转换为优化的 C++，然后使用 g++编译。从而在利用 C++性能的同时保留了 PHP 的优点。使用 HipHop，脸书网络服务器的 CPU 使用率已经降低了大约百分之五十！谁会想到，这和许多[在编程方面的其他酷进步](http://www.facebook.com/video/video.php?v=124728580468&ref=mf)，始于[的黑客马拉松](http://en.wikipedia.org/wiki/Hackathon)。