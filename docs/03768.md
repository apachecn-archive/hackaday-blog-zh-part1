# 433 MHz 欧洲 ISM 频段上的 BPSK

> 原文：<https://hackaday.com/2009/08/03/bpsk-on-433-mhz-european-ism-band/>

![main](img/9b219458f3b79da3d560e6c94331e063.png "main")

[乘波者]正在使用一种叫做 BPSK 的[相移键控](http://en.wikipedia.org/wiki/Phase-shift_keying)向[传输数字声音和视频](http://4hv.org/e107_plugins/forum/forum_viewtopic.php?10352)进行远程遥测。尽管通信通常追求更高的信噪比(SNR ),但法律对总辐射功率有所限制。为了平衡两头野兽，他选择了频移键控，因为二进制频移键控能够在较低的信噪比下工作。这增加了在接收机处正确重构数字信号的难度。基于 PLL 的载波再生电路用于重构信号。使用 [Rabit2000 处理器](http://www.rabbit.com/products/rab2000/)作为发送器和接收器的主控制器，获得 96KB/秒的串行数据。光谱的另一端是[自制的再生管收音机](http://hackaday.com/2009/07/13/homemade-regenerative-tube-radio/)。