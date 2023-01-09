# 微型 Atari 810 磁盘驱动器升级

> 原文：<https://hackaday.com/2011/05/05/tiny-atari-810-disk-drive-upgrade/>

随着技术的进步，一切都变得越来越小。[Rossum]通过[构建这个微小的替代品](http://rossum.posterous.com/a-little-atari-810-disk-drive)来减少 Atari 810 磁盘驱动器所需的空间。当然它不用软盘，取而代之的是 microSD 卡。它不能代替一个软盘驱动器，而是可以模拟多达八个不同的驱动器。最棒的是，[Rossum]不辞辛苦地设计了一个外壳，并通过 3D 打印进行制造，以便看起来就像原始硬件的玩偶之家版本。它使用 LPC1114 ARM Cortex-M0 微处理器来翻译与 Atari 硬件之间的数据传输，并将其存储在 8 GB 卡上。

像往常一样，你很快就会在[他的 git 库](https://github.com/rossumur/)上找到原理图、电路板插图和代码。