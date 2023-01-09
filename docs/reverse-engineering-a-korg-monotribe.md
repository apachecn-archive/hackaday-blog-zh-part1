# 逆向工程

> 原文：<https://hackaday.com/2011/12/03/reverse-engineering-a-korg-monotribe/>

![](img/d7cc47943ee61deeab588ce5418e912c.png "monotribe")

昨天，Korg 发布了他们的 ribbon 控制器 synth 的固件更新。固件只是一个音频文件，需要播放到盒子的同步输入端。[gravitronic]认为这相当有趣，所以他决定[解码 monotribe 固件](http://gravitronic.blogspot.com/2011/12/decoding-korg-monotribe-firmware.html)。这是定制 Monotribe 固件的第一步，也是对这个整洁的盒子进行逆向工程的第一步。

把固件更新转换成. wav 后，【gravitronic】用十六进制编辑器看了一下文件，发现每个样本都是两个字节，左右声道是一样的。这很有道理，所以在去掉一个通道后，他通过 Python 发送它，看看 1 和 0 的模式。

当然【gravitronic】任意选择了 high = 1，low = 0，little-endianness。第一个结果没有在头中产生一个好的“KORG 系统文件”，所以他尝试了其他组合，直到输出文件看起来合理。结果是实际的。bin 文件，它将作为一个好的自制固件的基础。你可以在这里获取【gravitronic】的 Python 脚本[并解码你自己的固件。](https://github.com/gravitronic/monotribe/blob/master/decoder.py)