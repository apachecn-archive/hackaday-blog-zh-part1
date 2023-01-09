# Exploit-Me 火狐 XSS 和 SQL 扫描插件

> 原文：<https://hackaday.com/2008/06/14/exploit-me-firefox-xss-and-sql-scanning-addon/>

[https://www.youtube.com/embed/RbL2ptbjoSA?version=3&rel=0&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/RbL2ptbjoSA?version=3&rel=0&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)
我们在 [LayerOne](http://layerone.info/) 看到的最好的工具之一是 [Exploit-Me 系列](http://www.securitycompass.com/exploitme.shtml)由【Dan Sinclair】展示。Security Compass 创建了这些工具来帮助开发人员轻松识别跨站脚本(XSS)和 SQL 注入漏洞。

XSS-我是一个加载在侧边栏的火狐插件。它识别页面上的所有输入字段，并遍历用户提供的 XSS 字符串的[列表:打开新标签并检查结果。当此过程完成时，您会得到一份报告，其中包含哪些攻击通过了，哪些没有通过，以及哪些可能通过了。即将到来的 0.3 版本将使用试探法来确定哪些字符可以使用，并自动跳过不会通过的攻击字符串。](http://ha.ckers.org/xss.html)

SQL Inject-Me 的工作方式几乎完全相同。但是这确实需要一点计划:当攻击通过时，你需要告诉它你期望的结果页面是什么样子。

最新的工具 Access-Me 会在你通过网站认证的同时陪你一起冲浪，并检查你是否能看到未经认证的同一个页面。

*   [永久链接](http://www.securitycompass.com/exploitme.shtml)