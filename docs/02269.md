# DNS 漏洞利用

> 原文：<https://hackaday.com/2008/07/23/dns-exploit-in-the-wild/>

![](img/b77c2b868f5801e330040a8cf921be6d.png)
我们一直在跟踪 [Metasploit](http://metasploit.com/) 的提交，因为马塔萨诺[在周一过早公布了【丹·卡明斯基】的 DNS 缓存中毒漏洞](http://blog.wired.com/27bstroke6/2008/07/details-of-dns.html)，我们非常清楚功能漏洞即将到来。仅仅两个小时前,[HD Moore]和[I]ruid]在 Metasploit 项目中添加了一个模块，该模块将允许任何人测试漏洞(评论:“[ZOMG。这是什么？> :-)](http://metasploit.com/dev/trac/browser/framework3/trunk/modules/auxiliary/spoof/dns/baliwicked_host.rb?rev=5579) "。[HD] [告诉威胁等级](http://blog.wired.com/27bstroke6/2008/07/dns-exploit-in.html)对于已经被 DNS 服务器缓存的域还不起作用，但是会自动等待缓存条目过期，然后完成攻击。你可以在 CAU 的公告中阅读更多关于 bailiwicked_host.rb 模块[的内容。关于攻击如何工作的更详细的描述，见 Matason 帖子](http://www.caughq.org/exploits/CAU-EX-2008-0002.txt)的[镜像。你可以通过](http://beezari.livejournal.com/141796.html)[使用【Dan】网站上的工具](http://www.doxpara.com/)来检查你正在使用的 DNS 服务器是否易受攻击。

[图片: [mattdork](http://flickr.com/photos/dork/413073001/)

*   [永久链接](http://www.caughq.org/exploits/CAU-EX-2008-0002.txt)