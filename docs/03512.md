# D-Link 路由器验证码破解

> 原文：<https://hackaday.com/2009/05/19/d-link-router-captcha-broken/>

![d-link](img/dbfda7cd96082c07d21754598a67a95f.png "d-link")

我们上周报道过，D-Link 正在为其路由器添加验证码，以防止恶意软件自动登录。不出所料，它并不是一直都有效。来自 SourceSec 的团队抓起新固件，开始摆弄它。他们发现[某些页面不需要认证](http://www.sourcesec.com/2009/05/12/d-link-captcha-partially-broken/ "SourceSec Security Research  » Blog Archive   » D-Link Captcha Partially Broken")就可以访问。其中之一就是 WPS 激活。 [WPS](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup "Wi-Fi Protected Setup - Wikipedia, the free encyclopedia") 让你做按钮式 WPA 配置。一旦激活，任何附近的客户端都可以使用类似 [WPSpy](http://www.sourcesec.com/2009/05/09/wpscan-wpspy-tools/) 的工具请求 WPA 密钥。只需要用户级别的凭证就可以实现这一点，所以只更改管理员密码不会阻止这一点。

[图片:[肖希](http://www.flickr.com/photos/schoschie/1448798334/ "D-Link DI-524 undressed on Flickr - Photo Sharing!")