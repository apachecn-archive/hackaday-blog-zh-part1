# Windows 7 和 Vista 因中小企业漏洞而崩溃

> 原文：<https://hackaday.com/2009/09/09/windows-7-and-vista-crash-via-smb-exploit/>

![vista_dx10_bsod](img/88df5d727b681346600df2a9bd4c1c4c.png "vista_dx10_bsod")

[Laurent Gaffié]发现了一个影响 Windows Vista、Windows 7 和 Windows Server 2008(未经证实)的[漏洞。此方法通过协商协议请求进行攻击，协商协议请求是发送的第一个 SMB 查询。该漏洞仅存在于包含](http://g-laurent.blogspot.com/2009/09/windows-vista7-smb20-negotiate-protocol.html)[服务器消息块 2.0](http://en.wikipedia.org/wiki/Server_Message_Block#SMB2) 并启用了该协议的 Windows 版本上。成功的攻击不需要本地访问机器，并导致[蓝屏死亡](http://en.wikipedia.org/wiki/Bsod)。

[Laurent]在他的文章中提供了一个 python 脚本形式的概念证明(请， [white hat](http://en.wikipedia.org/wiki/White_hat) 仅使用)。此漏洞没有修补程序，但禁用 SMB 协议将保护您的系统，直到有可用的修补程序。

**更新:**根据[微软公告](http://www.microsoft.com/technet/security/advisory/975497.mspx)该漏洞可能导致代码执行，使其比我们想象的更糟糕。从好的方面来说，他们声称 Windows 7 的最终版本不会对这种攻击开放，只开放 Windows Vista 和 Windows Server 2008。

[通过[全面披露](http://seclists.org/fulldisclosure/2009/Sep/0039.html)

[图片:[问询者](http://www.theinquirer.net/inquirer/news/1042793/windows-vista-dx10-bsod-pictured)