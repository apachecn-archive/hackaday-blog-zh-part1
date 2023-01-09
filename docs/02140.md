# ARDAgent.app 仍易受攻击

> 原文：<https://hackaday.com/2008/07/05/ardagentapp-still-vulnerable/>

![](img/d3e5a0fea1975e3c8f4a67379cb7c905.png)
当苹果推送他们最[最近的安全更新](http://support.apple.com/kb/HT2163)时，我们首先检查的是 [ARDAgent 问题](http://www.macshadows.com/kb/index.php?title=ARDAgent_exploit)是否修复。不是的。该漏洞允许任何人以特权用户的身份执行代码，这种攻击的各种版本已经被发现。虽然几个 Ruby、SMB 和 WebKit 问题已经解决，但 ARDAgent 仍然没有打补丁。【Dino Dai Zovi】已经[公布了 ARDAgent 实际上变得易受攻击的方法](http://blog.trailofbits.com/2008/07/05/ardagentapp-vulnerability-analysis/):启动时安装自己的 Apple 事件处理程序，用 kAEInteractWithSelf 调用 AESetInteractionAllowed()。这应该将它限制在它自己的事件中，但出于某种原因，这并不是最终的行为。他还指出，SecurityAgent 也表现出了类似的怪异；即使它不调用苹果事件函数，也容易受到苹果事件的攻击。我们可以看到这种意想不到的行为是如何使补丁开发花费更长的时间，并可能最终发现一个更大的问题。查看[【迪诺】的帖子](http://blog.trailofbits.com/2008/07/05/ardagentapp-vulnerability-analysis/)了解更多信息。

*   [永久链接](http://blog.trailofbits.com/2008/07/05/ardagentapp-vulnerability-analysis/)