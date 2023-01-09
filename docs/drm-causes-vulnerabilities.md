# DRM 导致漏洞

> 原文：<https://hackaday.com/2010/09/26/drm-causes-vulnerabilities/>

![This image is from Microsoft's DRM page.](img/72a8d2a5859e17efe4849822fb28ade4.png "DRM_hero")

我们经常听到人们吹捧 DRM 的邪恶，但通常他们谈论的是所有权的概念。在这种情况下，DRM 实际上是在造成伤害。原来，微软的 msnetobj.dll，应该在你的电脑上执行 DRM，阻止你做某些事情，如保存你不“拥有”的文件[，是开放的 3 攻击](http://www.exploit-db.com/exploits/15061/)。易受[缓冲区溢出](http://en.wikipedia.org/wiki/Buffer_overflow)、整数溢出和拒绝服务的攻击，这个笨蛋问题百出。

这个文件中的漏洞并不是开创性的。缓冲区溢出是进入许多系统的常见方法。根据 BoingBoing 的一些评论，这里的问题是，每次你打开一个媒体文件时，这个 DLL 都会被调用。

[via [BoingBoing](http://www.boingboing.net/2010/09/24/microsofts-drm-makes.html)