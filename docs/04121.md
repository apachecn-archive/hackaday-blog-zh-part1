# Gameboy 彩色启动 ROM

> 原文：<https://hackaday.com/2009/09/28/gameboy-color-boot-rom/>

![top_view_full](img/4382070f519d009142fc7acf52dc62f6.png "top_view_full")

超级游戏男孩的靴子从被【Costis】抛弃才过了一周，他又开始玩了。这一次他设法从手中抢走了[游戏机颜色的靴子。他发现新的 Gameboy Color 硬件能够应对高达 100MHz 的时钟速度，因此他在超级 Gameboy 上使用的原始时钟增加技巧将不再有效。](http://www.fpgb.org/?page_id=17)

相反，他发现在 0xFF50 之前快速断开时钟和电源会使 Gameboy 跳转到 ROM 中的随机区域。然后它只是一个熵、运气和一些特殊的 NOP 指令的问题，直到最后他有了引导 ROM。继续好好工作。