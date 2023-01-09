# 量子密码带内攻击

> 原文：<https://hackaday.com/2008/10/06/quantum-cryptography-in-band-attack/>

![](img/58e5a16098fe734c1f9ceca457a83698.png "quantum")

量子密码术是一个新兴领域，但低安装基数并没有阻止研究人员探索针对它的攻击。这是一项有吸引力的技术，因为攻击者嗅探密钥交换会改变相关光子的量子状态。因为量子力学的这个基本原理，所有的窃听者都可以被探测到。

我们已经看到了对正在使用的硬件的理论上的旁道攻击，但直到现在还没有看到带内攻击。来自特隆赫姆科技大学的瓦迪姆·马卡洛夫(Vadim Makarov)已经[做到了](http://technology.newscientist.com/channel/tech/dn14866-laser-cracks-unbreakable-quantum-communications.html)(链接失效，[试试互联网存档](https://web.archive.org/web/20081010064043/http://technology.newscientist.com/channel/tech/dn14866-laser-cracks-unbreakable-quantum-communications.html))。量子密钥分发系统是为应对噪声而设计的，[马卡洛夫]利用了这一点。这种攻击的工作原理是向系统中的所有探测器发射一道明亮的闪光。这增加了记录读数所需的光量。攻击者然后发送他们想要检测的光子，这些光子有足够的能量被预定的检测器读取，但对其他人来说不够。因为它没有清除阈值，所以检测器不会抛出任何异常。攻击者可以嗅探整个密钥并在不被发现的情况下重放它。

这是一个非常有趣的攻击，因为它是合法的密钥窃听。通过更好地监控检测器的功率波动，这种情况可能会得到缓解。

[via [I)ruid](http://twitter.com/druidian/statuses/948799488)