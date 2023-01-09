# JavaScript 中的 MegaUpload 验证码破解

> 原文：<https://hackaday.com/2009/01/23/megaupload-captcha-cracking-in-javascript/>

![megaupload-the-leading-online-storage-and-file-delivery-service](img/d7c6a568fceaaaa537304b876e4e413a.png "megaupload-the-leading-online-storage-and-file-delivery-service")

这肯定是我们今天最不希望看到的事情。[ShaunF]创建了一个 Greasemonkey 脚本来[绕过文件托管网站 Megaupload](http://userscripts.org/scripts/show/38736 "Megaupload auto-fill captcha for Greasemonkey") 上的验证码。它使用 JavaScript 中的[神经网络](http://en.wikipedia.org/wiki/Neural_network "Neural network - Wikipedia, the free encyclopedia")来完成所有的 OCR 工作。它会自动提交并开始下载。这是一个非常聪明的方法，当然也得益于该网站使用的简单的 3 个字符的验证码。事实证明，尝试用 ReCAPTCHA 做[同样的事情要困难得多。](http://userscripts.org/topics/18922?page=3#posts-85120 "reCAPTCHA – Userscripts.org")

**更新:**【约翰·瑞西格】解释[如何运作](http://ejohn.org/blog/ocr-and-neural-nets-in-javascript/)。

[via [蜡质](http://waxy.org/links "Links Miniblog")