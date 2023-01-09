# 擦拭 IPhone(更彻底)

> 原文：<https://hackaday.com/2008/06/10/wiping-an-iphone-more-thoroughly/>

你可能希望通过出售旧手机来补贴购买 iPhone 3G，但由于你应该先从旧手机上删除所有个人数据，我们为你带来了[【富豪】从 iPhone 上删除所有个人数据的方法](http://www.hackaday.com/2008/05/20/erase-an-iphone-properly/)。这种用音乐覆盖数据的方法略有缺陷，主要是因为手机操作系统工作时无法删除实时文件，而且操作系统会保留一部分硬盘空间作为不可写空间，这使得音乐无法完全填满硬盘。

对于那些想要消灭所有个人信息的人来说，看看[【Jonathan Zdziarski】的方法](http://www.zdziarski.com/papers/wipe.html)。它包括恢复手机作为一个新手机，然后[越狱它](http://www.mahalo.com/IPhone_Jailbreak)。一旦用户拥有了 shell 访问权限，就可以使用 umount 强制两个挂载点进入只读模式。现在可以用/dev/zero 覆盖分区，这应该会将它们清除干净。然后，手机应被强制进入恢复模式，以执行另一个完整的系统恢复，该过程完成。正如[Zdziarski]所指出的，使用/dev/random 对该过程进行几次迭代甚至会阻止 NAND 恢复，但有一种更好的方法可以确保完全销毁数据:“只需拿一把大锤砸向设备。”如果你不熟悉命令行，有可能[Rich Mogull]的方法对你来说会更容易处理，但是如果你卖掉了你的手机，联邦调查局发现了你留在手机上的证据，不要责怪我们。

[via [Engadget](http://www.engadget.com/2008/06/10/how-to-completely-erase-user-data-from-an-iphone-part-two-comm/)

*   [永久链接](http://www.zdziarski.com/papers/wipe.html)