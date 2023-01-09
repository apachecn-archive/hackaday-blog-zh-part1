# WordPress 2.7 升级一步到位

> 原文：<https://hackaday.com/2008/12/10/wordpress-27-upgrade-in-one-line/>

![wordpress](img/43cffb1df40f18f7467ad4f23e53601c.png "wordpress")

[WordPress 2.7](http://wordpress.org/ "WordPress › Blog Tool and Publishing Platform")[刚刚发布](http://wordpress.org/development/2008/12/coltrane/ "WordPress › Blog »   WordPress 2.7 “Coltrane”")，其特点是一个完整的界面革新。Hack a Day 在由主持的 WordPress MU 上运行，所以我们上周得到了这个更新。不过，我们在所有的个人博客上都运行标准 WordPress.org。我们推荐它，因为它是免费的，有大量的用户，如果你自己托管它，你可以用它做任何你想做的事情。

为了使升级过程尽可能简单(并且为了“RM-RF”的纯粹冲击】,我们使用一行命令。

`$ curl [http://wordpress.org/latest.zip](http://wordpress.org/latest.zip) -o "wp.zip" && unzip wp.zip && rm -rf ./wordpress/wp-content/ && cp -r ./wordpress/* ~/www/`

[curl](http://curl.haxx.se/ "cURL and libcurl") 从 wordpress 下载最新版本。将所有文件解压到一个名为“wordpress”的目录中。rm -rf 删除“wp-content”目录中的所有内容。否则，您将覆盖您的图像、主题和插件。cp -r 将所有内容复制到您的 http 文档根目录，覆盖先前的安装。

自然，你应该提前备份你当前的安装和数据库。我们倾向于不计后果地使用一行程序。如果你想知道它的简洁性，它被设计成[符合 Twitter](http://twitter.com/cfinke/status/779468837 "//wo ...")140 个字符的限制。

[谢谢，[克里斯·芬克](http://www.chrisfinke.com/ "Less Talk, More Do")