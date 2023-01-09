# 从 EEPROM 中窃取管理员密码

> 原文：<https://hackaday.com/2009/09/24/steal-the-administrator-password-from-an-eeprom/>

![locating_atmel](img/fd709335bb7d3f9484b56dd19f35a252.png "locating_atmel")

您是否忘记了基于硬件的密码，现在被锁定了？如果是 IBM ThinkPad，你可能会很幸运，但这不仅仅是移除备用电池。SoDoItYourself 有一篇文章详细介绍了从 EEPROM 中检索密码数据的[。](http://sodoityourself.com/hacking-ibm-thinkpad-bios-password/)

这个过程很有趣。拆开你的笔记本电脑。构建一个串行接口，并将其焊接到存储密码的 [EEPROM 芯片](http://hackaday.com/2009/06/30/parts-spi-eeprom-25aa25lc/)上。将此接口连接到第二台计算机，并使用它将数据转储到文件中。下载一个特殊的程序来解密转储文件，并通过十六进制代码寻找类似密码的东西。重新组装你的笔记本电脑，希望它能正常工作。

我们知道大多数人不需要 ThinkPad 管理员密码，但是在其他情况下[从 EEPROM 读取数据会派上用场](http://forums.afterdawn.com/thread_view.cfm/357863)。你用这种方法做什么？