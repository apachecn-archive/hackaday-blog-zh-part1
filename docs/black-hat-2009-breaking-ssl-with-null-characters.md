# 黑帽 2009:用空字符破坏 SSL

> 原文：<https://hackaday.com/2009/07/29/black-hat-2009-breaking-ssl-with-null-characters/>

![](img/4ecdacc26d8cc8327b41e65f81bd1128.png)

**更新:**【莫邪】[演讲视频现已上线](https://www.blackhat.com/html/bh-usa-09/bh-usa-09-archives.html#Marlinspike)。

[莫邪·马林斯派克]早在二月份就出现在我们的视线中，当时他在黑帽 DC 表演了[sslstrip。这是一个了不起的软件，可以劫持和重写所有的 SSL 连接。合法网站和被劫持网站之间的区别很难被注意到。他最近偶然发现了一些东西，使得攻击更加有效。](http://hackaday.com/2009/02/23/sslstrip-hijacking-ssl-in-network/ "sslstrip, hijacking SSL in network  - Hack a Day")

如果您申请证书，证书颁发机构会查看表单上的通用名称并联系域所有者。CA 忽略子域。诀窍是在子域中加入一个空字符。如果您注册了 http://www . paypal . com[nullcharacter]. thoughtcrime . org，CA 将联系 thoughtcrime.org 的所有者并颁发证书。当像 Firefox 这样的客户端使用 NSS 验证证书时，空字符会导致他们认为证书对 http://www.paypal.com 的[有效，因为他们在空字符处停止。即使用户在浏览器中查看证书，它也会显示 http://www.paypal.com](http://www.paypal.com)的[。](http://www.paypal.com)

通配符也可以。你可以获得*[null character]. thoughtcrime . org 的证书，并显示为你想要的任何网站。[莫邪]已经找到了防止证书撤销和浏览器更新的方法。这一新代码将成为 [sslsniff](http://www.thoughtcrime.org/software/sslsniff/ "Moxie Marlinspike >> software >> sslsniff") 0.6 的一部分。

[为奇怪的符号道歉。WordPress 显然去除了空字符…]