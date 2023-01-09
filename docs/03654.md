# 使用回溯破解 WEP

> 原文：<https://hackaday.com/2009/07/02/crack-wep-using-backtrack/>

![wepcrack04](img/d355c0d2d4c986bd7d73604b0eb86635.png "wepcrack04")

Lifehacker 写了一个使用回溯破解 WiFi 网络 WEP 密码的指南[。](http://lifehacker.com/5305094/how-to-crack-a-wi+fi-networks-wep-password-with-backtrack)[回溯](http://www.remote-exploit.org/backtrack.html)是一个用于安全测试的 Linux live CD，附带了破解 WEP 所需的工具。不是所有的无线网卡都能做到这一点；你需要一个[支持包注入](http://www.aircrack-ng.org/doku.php?id=compatible_cards)的。这种破解的工作原理是收集合法的数据包，然后将它们重放几次，以生成数据。他们指出，这种方法可能不可靠，尤其是在网络上几乎没有其他用户的情况下，因为破解需要经过认证的数据包。我们在之前讨论过[破解 WEP，但是使用回溯应该可以解决兼容性问题。](http://hackaday.com/2005/05/15/cracking-wep/)