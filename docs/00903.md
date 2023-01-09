# 在 WRT 上运行的 Metasploit

> 原文：<https://hackaday.com/2006/05/19/metasploit-running-on-a-wrt/>

![metasploit](img/19d320cf9971bd49c186311f480cda90.png)

See-Security 的人已经在 Linksys WRTSL54GS 上运行了 [Metasploit 框架。他们是在看到](http://www.hackingdefined.com/index.php/Getting_Metasploit_to_run_on_a_Linksys_Router)[黑客皮条客](http://hackerpimps.com/)笔测固件后受到启发的，这个[我们在](http://www.hackaday.com/entry/1234000093059705/)之前已经报道过了。Metasploit 框架用于针对目标机器开发和执行漏洞利用代码。由于 RAM 的限制，See-Security 团队在运行 Metasploit 时遇到了麻烦。这种特殊型号的路由器有一个 USB 端口，因此他们能够在闪存驱动器上创建交换空间。一旦他们将绑定地址设置为网关 IP，web 界面也能正常工作。从 OpenWRT 开始，他们已经提供了完成这项工作所需的所有步骤。

[感谢穆特和斯蒂尔本]

*   [永久链接](http://www.hackingdefined.com/index.php/Getting_Metasploit_to_run_on_a_Linksys_Router)