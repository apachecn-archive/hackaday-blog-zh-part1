# 苹果终于修复了 DNS 漏洞

> 原文：<https://hackaday.com/2008/09/15/apple-finally-fixes-dns-bug/>

![](img/e9c8c28b2c1b871a1b2701712b9e1ff9.png "had_iphone")

随着今天[安全更新 2008-006](http://support.apple.com/kb/HT3137) 的发布，苹果终于解决了今年夏天的 [DNS 漏洞](http://hackaday.com/tag/dns/)。在他们之前的更新[中，他们修复了绑定](http://support.apple.com/kb/HT2647)，但是这只影响运行服务器的人。现在，他们已经更新了 mDNSResponder。由于包含了源端口随机化，客户端不再容易受到 DNS 缓存中毒攻击。

该安全更新解决了其他一些有趣的错误。Time Machine 在没有使用适当权限的情况下存储敏感日志，因此任何用户都可以查看它们。

[照片:[年龄](http://flickr.com/photos/edans/1526393678/)