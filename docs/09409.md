# 声音反应坎耶眼镜！

> 原文：<https://hackaday.com/2012/01/01/sound-reactive-kanye-glasses-2/>

![](img/5cd08de82dbac77a7700696208460fb8.png "KanyeGlasses")

[Ch00f]决定带着一些 [el wire Kanye 眼镜](http://ch00ftech.com/2011/12/31/stronger-glasses/)迎接新年。从技术上来说，这种眼镜的术语要么是“百叶窗式太阳镜”，要么是“板条式太阳镜”，大约在 80 年代由[Alain Mikli]发明，最初的绰号是“威尼斯太阳镜”。Kanye West 显然得到了原创者自己的复古设计，剩下的就是历史了。目前维基百科已经足够了。[Ch00f]增加了原始设计，在眼镜的百叶窗上安装了六条多色 EL 线轨道。EL 线通过围绕佩戴者耳朵的几根离散的线反馈到两个控制盒。正如视频所示，眼镜的功能是基于驱动电路接收的音频，作为一个原始的 V/U 表。

不同于典型的微控制器[Ch00f](他对 Arduino 有一些根深蒂固的问题)决定对整个设计进行全面模拟。音频信号通过各种运算放大器电路输入，首先放大微弱的麦克风信号，然后用低通滤波器进行滤波，以聚焦低音频率。过滤后的低音随后被发送到包络检波器，将音频波转换为 DC 电压信号。与运算放大器设计保持一致[Ch00f]然后使用一个梯形电阻和六个比较器电路(输出端带有三端双向可控硅开关)来调谐 EL 条的触发电压电平。三端双向可控硅开关可以处理 EL 条的 100 伏左右的电压，这样[Ch00f]就不用在口袋里装六个 EL 电源了。对于在家计算的人来说，总共有 13 个运算放大器。

结果很棒，看看下面的视频，看看眼镜的效果。据报道，该电路确实发生了故障，并将所有的三端双向可控硅开关锁定在导通状态，但电源开关的秘密翻转暂时解决了这个问题。[Ch00f]承认，由于即将到来的新年晚会，该项目相当仓促，但现在一切都结束了，我们只需要让[Ch00f]推出一个立体声版本。如果你需要更多的[ch00f],我们之前已经报道过他的一些项目，比如他的[破冰船 POV 玩具黑客](http://hackaday.com/2011/12/21/reverse-engineering-the-icebreaker-pov-toy/)和使用反射传感器的[贫民区加速度计](http://hackaday.com/2011/11/16/pov-bauble-uses-diy-accelerometer-to-sync-the-image/)。

感谢[Daniel]和[sanchooo]的提示，也是通过[[Reddit](http://www.reddit.com/r/gadgets/comments/nxthl/i_made_some_soundreactive_kanye_glasses_for_new/)]。新年快乐！

![](img/98f33dbdb2167100429f7849a4a6b206.png "More...")

[https://www.youtube.com/embed/hYAkWoUIqQE?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/hYAkWoUIqQE?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)