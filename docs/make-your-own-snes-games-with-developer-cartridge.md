# 使用开发商墨盒制作您自己的 SNES 游戏

> 原文：<https://hackaday.com/2009/10/23/make-your-own-snes-games-with-developer-cartridge/>

你是否一直希望你能为超级任天堂开发游戏，但因为它在 1990 年发布时你只有 4 岁而不能？这是第二次机会。[Max]和他的团队已经创建了一个 [SNES 开发者包](https://www.assembla.com/wiki/show/quickdev16)，它允许你加载自己的代码，在 SNES 上运行，并根据需要进行调试。其核心是 Atmel AVR ATmega644，运行引导加载程序，允许通过 USB 进行固件更新。一旦系统通电，ROM 代码通过 USB 发送到 16 兆位板载 SRAM。调试终端可以与 RS232 转换器连接，提供状态信息并允许一些寄存器操作。

我们可以相信有一些 SNES 的铁杆粉丝会花时间编写定制代码。我们也可以看到这被用于 SNES 合成音乐的目的。但是这种类型的硬件有广泛的需求吗？如果你曾经考虑为 SNES 开发，请在评论中告诉我们。