# 用 Fluid 构建一个 Twitter 客户端

> 原文：<https://hackaday.com/2008/06/25/build-a-twitter-client-with-fluid/>

<http://www.vimeo.com/moogaloop.swf?clip_id=1220895&amp;server=www.vimeo.com&amp;show_title=0&amp;show_byline=0&amp;show_portrait=0&amp;color=000000&amp;fullscreen=1>


[Fluid Site Specific Browser](http://fluidapp.com/)(SSB)是我们最喜欢的 Leopard 套件之一。你可以使用 Fluid 为 Gmail、脸书、维基百科或 Pandora 等你经常使用的网络服务提供自己的图标和一个针对该网站特定工作流程定制的浏览器。Fluid 基于 WebKit，并在[许多其他特性](http://fluidapp.com/features/)中有插件支持。上面嵌入的是【埃里克·埃格特】展示如何[使用它创建一个合理的 Twitter 客户端](http://www.vimeo.com/1220895)。初始设置与任何其他流体应用程序相同:将其指向[https://twitter.com/](https://twitter.com/)。巧妙之处在于利用了 Fluid 的 GreaseMonkey 风格的用户脚本支持。他创建了一个用户脚本来自动刷新。第二个用户脚本用于[去除所有无关的页面元素](http://userscripts.org/scripts/show/29007)，只留下文本字段和时间线。每当你收到一个新消息，它会生成一个咆哮通知，你甚至可以把它附加到状态栏。最棒的是:它**避免了所有的 API 限制**，因为你是通过 web 界面访问的。

*   [永久链接](http://www.vimeo.com/1220895)