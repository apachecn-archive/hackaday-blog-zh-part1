# Twitter IRC 服务器

> 原文：<https://hackaday.com/2009/01/05/twitter-irc-server-tircd/>

![tircd](img/429df38020b7d95fa92985e6bdffcf56.png "tircd")

tircd 是一个 ircd 代理，用于与 T2 的 Twitter API T3 对话。它应该适用于任何标准的 IRC 客户端。运行 Perl 脚本后，您使用您的 Twitter 用户名作为您的/nick 向 IRC 服务器进行身份验证。加入房间#twitter 和/主题将被设置为您的最后更新。你输入的任何信息都会更新 Twitter 和房间的主题。你关注的所有人都以用户身份出现在房间里，并在他们发微博时发布消息。如果你私信其中一个，它将成为 Twitter 上的直接消息。其他命令也有效:/whois 获取某人的个人资料，/invite 开始关注，以及/kick 取消关注。该项目是全新的，并将在未来增加新的功能，如搜索 API 支持。关注 [@tircd](http://twitter.com/tircd "Twitter / tircd") 更新。