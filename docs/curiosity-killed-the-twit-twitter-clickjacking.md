# 好奇心杀死了推特，推特点击劫持

> 原文：<https://hackaday.com/2009/02/12/curiosity-killed-the-twit-twitter-clickjacking/>

![dontclick](img/cce2f98bc7bd7c7a4e1984d509d9a26c.png "dontclick")

今天早上，推特上充斥着用户发布的“不要点击:[http://tinyurl.com/amgzs6&# 8221](http://tinyurl.com/amgzs6&#8221)；。TinyURL 自从[终止了 URL](http://tinyurl.com/nospam.php?id=amgzs6 "TinyURL.com - where tiny is better!") 。[原页面](http://www.umoor.eu/blog/yes-we-can.php)好像也不活了。它显示了一个按钮，上面写着“不要点击”。如果用户碰巧登录了 Twitter，它会自动更新他们的状态。煽动者在其博客 ( [译](http://translate.google.com/translate?prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fwww.korben.info%2Fpetit-cours-de-twitt-jacking.html&sl=fr&tl=en&history_state0= "Google Translate"))上部分描述了方法[。该页面将在一个不可见的 iframe 中加载用户的 Twitter 页面。状态将被粘贴，并且“不要点击”按钮将被放置在“更新”按钮的顶部。你可以在这里找到](http://www.korben.info/petit-cours-de-twitt-jacking.html "-) | Korben")[代码片段](http://raven-seo-tools.com/blog/310/evil-genius-how-to-get-people-to-tweet-for-you-without-them-knowing "How to Get People to Tweet for You Without Them Knowing - Raven SEO Tools")，原作者[认为这篇文章](http://james.padolsey.com/general/clickjacking-twitter/ "Clickjacking Twitter - James Padolsey")给了你灵感。Twitter 从[开始在每个页面上添加一个 JavaScript 片段](http://james.padolsey.com/general/clickjacking-twitter/#comment-5095 "Clickjacking Twitter - James Padolsey")来突破 iframes。

```
if (window.top !== window.self) { window.top.location.href = window.self.location.href; }
```