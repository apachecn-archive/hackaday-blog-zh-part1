# 推进器和机枪定时

> 原文：<https://hackaday.com/2010/11/09/propeller-and-machine-gun-timing/>

[马特]在寻找挑战。受第一次世界大战飞机上机枪设置的启发，他想制造一种能在旋转螺旋桨叶片之间射击的枪。最初的枪使用[一个中断齿轮](http://electronicsfluff.blogspot.com/2010/11/microcontroller-interrupter-gear.html)使机枪与引擎机械同步开火。[Matt]开始使用微控制器来做这件事。

要完成这项工作，有两条重要的信息:螺旋桨现在转得有多快，小球通过叶片需要多长时间？[Matt]使用示波器和一些红外传感器建立了大约 20-22 毫秒的点火延迟。另一个传感器显示螺旋桨以每分钟 500 转的速度旋转，通过一些简单的计算表明，叶片之间确实有足够大的时间窗口来开火。在用一个可见的 LED 进行测试，然后构建出其余的电路之后，他实现了他的目标。他甚至添加了一个测试功能，专门测试刀片，看看系统有多精确。我们希望这能出现在一个红色男爵遥控模型的复制品中，或者其他的飞行武器库中。

[via [被黑的小工具](http://hackedgadgets.com/2010/11/09/shoot-a-bullet-through-a-spinning-propeller-blade/)