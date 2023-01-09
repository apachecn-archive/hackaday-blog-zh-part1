# 具有秘密按键激活的 Kindle 终端

> 原文：<https://hackaday.com/2010/12/10/kindle-terminal-with-secret-key-press-activation/>

![](img/3701a671ce0c43a23e6f08b02db1caf4.png "kindle-3-terminal")

[Luigi Rizzo]一直在为他的第三代 Kindle 做一些黑客工作。已经有一个基于 Python 的终端模拟器叫做 AjaxTerm，但是他想要一个轻量级的独立模拟器，所以他用 C 语言重新实现了这个程序。100k 二进制程序监视键盘，当它检测到 Shift-T 序列时启动终端模拟器。它还使用替代按键映射来填补 Kindle 键盘上缺失的一些按键。

自从 Kindle 被黑客攻击来运行 Ubuntu 以来，我们还没有看到太多的黑客攻击。似乎这个终端模拟器是一个有用且不引人注目的工具，可以在心爱的读者身上试用。