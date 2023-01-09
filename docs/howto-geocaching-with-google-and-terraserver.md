# 如何使用 Google 和 Terraserver 进行地理藏宝

> 原文：<https://hackaday.com/2005/02/10/howto-geocaching-with-google-and-terraserver/>

![terraserver hackaday headquarters](img/b7d475336dba6068756d61f6d1621f24.png)
如果你对[地理藏宝](http://www.gadling.com/entry/2598496638438251/)， [terraserver](http://terraserver.microsoft.com/) 和[谷歌地图](http://maps.google.com/)可能是你最大的盟友。嗯，也许是第二大，仅次于你可信赖的 gps 接收器。有了 terraserver，你可以调出美国大陆几乎所有地方的卫星照片和地形图。有了谷歌地图，你可以很容易地调出道路地图和行驶方向。

然而，当谷歌地图发布时，我注意到它的界面明显缺少纬度/经度输入框。原来有几个查询参数可以用来调出基于坐标的地图。有了这些信息，您可以制作一个简单的表单来获取给定纬度/经度组合的两个地图结果，这有望成为您下一次 gps 寻宝的便利工具。继续阅读，看看这是如何工作的。

**terraserver 参数** 

有两个查询参数用于指定纬度和经度。它们分别是 PgSrh:NavLat 和 PgSrh:NavLon，它们取十进制值。如果您的位置以度/分钟表示，只需将分钟除以 60，即可得到适当的十进制值。

最终的 terraserver 查询字符串如下所示:
[http://terraserver.microsoft.com/image.aspx?PgSrh:NavLon=-10](%20http://terraserver.microsoft.com/image.aspx?PgSrh:NavLon=-105.483&PgSrh:NavLat=37.583) …

插上这个应该能让你鸟瞰我的前两辆科罗拉多 14(小熊和布兰卡)。注意两者之间的毛脊线，我可能会死在那里。

**谷歌地图参数** 谷歌地图有一个单一的查询参数，您可以在其中指定纬度和经度。参数名为“sll”，格式为[纬度]% 2C[经度]。和 terraserver 一样，这些都是十进制格式。

最终的谷歌地图查询如下:
[http://maps.google.com/?sll=37.616%2C-115.816](%20http://maps.google.com/?sll=37.616%2C-115.816)

![google maps area 51](img/88605391119f23026889a14e889771bd.png)
进入那一个，再缩小一点，应该就能剧情出你下一次去超级绝密区 51 的行程了。

制作你自己的界面
你应该能够获得这些信息，并在你下一次的地理藏宝任务中加以利用。这两个服务对于不同的任务都很有用，所以我只是喜欢使用一个快捷的 html 界面来获取两个地图结果，以便我可以快速输入纬度/经度组合。制作你自己的并让我们知道，或者同时，只需在下面添加书签并使用我的:

杰森的快速和肮脏的谷歌地图/ terraserver 分屏浏览器

**跳上去**

是时候出去找点什么了。狩猎快乐，黑客快乐！