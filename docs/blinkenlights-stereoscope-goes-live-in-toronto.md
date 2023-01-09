# Blinkenlights 的立体镜在多伦多上线

> 原文：<https://hackaday.com/2008/10/04/blinkenlights-stereoscope-goes-live-in-toronto/>

![](img/ff9c5b8f234171c6633f24d93298c6d5.png "stereoscope")

*我们很高兴呈现这篇来自历史黑客[ [Bre Pettis](http://brepettis.com/) ]的客座博文。今天[Bre]采访了[闪光灯](http://blinkenlights.net/)团队，他们将整栋建筑变成了展示品。他们目前的项目是[立体镜](http://blinkenlights.net/stereoscope)，今天在加拿大多伦多上线。*

本周早些时候，我发布了关于闪光灯项目的[开端。它始于 2001 年的柏林，但现在 7 年后，2008 年 5 月，blinkenlights 又回来了。多伦多市询问 blinkenlights 团队是否有兴趣加入另一个 Nuit Blanche(就像他们在 2002 年在巴黎所做的那样)。时间紧迫，雄心勃勃，他们决定重新设计并推进这个项目，让多伦多市政厅实现无线上网，因为两座大楼将有 960 个窗户。在上面的照片中，你可以看到立体镜的辉煌。](http://brepettis.com/blog/2008/09/29/blinkenlights/)

[https://www.youtube.com/embed/YWuu7AIcSGI?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/YWuu7AIcSGI?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

我忍不住，这是一个如此棒的项目。我需要知道更多！我让蒂姆把它分解开来，说出细节。
 *立体镜项目有什么故事？*

在欧洲各地进行了各种各样的新尝试，但都没有成功(由于财政原因或建筑业主在最后一分钟撤回了支持)，这花了六年时间，直到我们能够提出一个新项目(不包括在原位置重复使用的两个小闪光灯)。

但在 2008 年 5 月，多伦多市问我们是否有兴趣在 2008 年 10 月加入另一个 Nuit Blanche(就像我们 2002 年在巴黎做的那样)。剩下的时间真的不多了，所以我们马上开始做这个宝贝，有几个非常艰难的最后期限要满足。尤其是因为我们不想使用 2002 年使用的技术。多伦多市政厅甚至比法国国家图书馆还要大(960 个窗户对 520 个窗户)，分为两个塔楼，我们也想挑战一下极限。

所以我们想出了一个主意，主要是无线的，以节省设置时间。虽然是一个大得多的安装，我们可能只需要一半的时间来设置一切-如果事情不会出错的话。
 *立体镜有什么特别之处？*

多伦多市政厅的外观在很多方面都很特别。首先有两座独立的塔:高度和宽度都不同。两个面都被分成大小不等的两部分，因为中间有没有窗户的机械地板。

更重要的是，塔楼有一个弯曲的结构，所有的窗户都朝内。这使得无论你从哪里看都不可能同时看到所有的窗户。我们以前所有的安装都只呈现一个单一的屏幕，非常像我们在电脑上习惯的屏幕。

Blinkenlights 不是关于建筑展示。这是关于人们的参与和对建筑的诠释。所以我们试图“说建筑的语言”为了弥补视角的困难，我们提倡一种流畅的外观:事物缓慢移动——你现在看不到的，过一会儿就会看到。所有这些也强调了建筑立面奇怪的空间外观，因此命名为立体镜(“空间视角”)。我们会看到这一切是如何发生的——我们从来不知道我们的装置会是什么感觉。对我们来说这将是一个惊喜，对普通观众来说也是如此。

创建一个 iphone 应用程序有多难？

为移动设备创建应用程序的想法和我们的项目一样古老。但在 2001/2002 年，还看不到任何可以做到这一点的迹象。然而，iPhone 是我们一直在等待的设备。

首先，我们希望这个应用程序对每个人都有用。所以我们专注于一个模拟器，它提供了正在发生的事情的实时视图。每个人都可以加载应用程序，在任何他们想去的地方收听直播(当然，只要他们能上网)。这个基础在我们的代码中已经存在很长一段时间了——因为我们一直在我们的安装中使用 IP 数据包进行帧分配，所以只需要将一个副本流式传输到可以在某种可视化工具上显示数据流的各个应用程序。

我们最初工具包中的 blinkensim 程序做到了这一点。智能代理(blinkenproxy)将其增强为按需模型:代理不断从单一来源接收数据流，并将数据流重新分发到每个要求副本的模拟器。我们希望我们的基础设施能够很好地满足需求。

对于立体镜，我们在许多方面增强了我们的协议:每个数据包都有实时时间戳，因此模拟器可以显示流生成的时间——无论是实时还是从档案副本回放。我们还增加了对多屏幕的支持，因为立体镜支持单个子屏幕和虚拟矩阵等概念。

我们希望应用程序看起来非常非常漂亮。因此，我们组建了一个由天才的 3D 和 2D 图形艺术家和两名优秀的 iPhone/Mac 程序员组成的团队:来自慕尼黑的编码猴子，以他们的协作文本编辑器 SubEthaEdit 和有用的 Circulator iPhone 应用程序而闻名。他们齐心协力，结果是一个非常出色的小应用程序，允许从任何角度或预定义的视点查看建筑，同时流畅地显示来自我们中央服务器的数据流。

由于奇怪的分销模式和 iTunes 应用商店漫长的审批时间，我们可能无法添加更多的功能。每次更新通常需要一周才能显示出来，这对这样一个时间关键的作品来说是非常糟糕的。关于如何将这个应用程序变成一个位置感知控制器，允许协作绘画和其他好主意，我们有很多想法。我们将看到最后结果如何。项目 Blinkenlights 一直在进行中，我们将保持数据流运行后，我们不得不采取安装本身，以便我们可以继续发挥和试验一个虚拟建筑的未来安装。
 *到目前为止有什么破事？有人受伤吗？*

设置进行得非常顺利，我们有信心及时做好准备。目前没有人员伤亡，但愿如此。

你会把旧电影移植到新项目中吗？你会特别展示一个女人在灰度中跳舞的视频吗？

我们将展示新旧材料的混合体。我们软件的新的多层核心允许多个电影和游戏同时运行，针对不同的子屏幕等等。代码中的新特性比我认为我们在两周内可以利用的还要多。我们走着瞧。

关于跳舞的女人，我刚刚被告知原始数据被锁在一台电脑里，这台电脑被塑料包裹着，放在澳大利亚内陆一所小房子的地下室里。我想我们不能及时恢复那个特别的动画了。

但我们无论如何都想去寻找新的原创内容。有一套适用于 Mac 的功能强大的工具。我们已经建立了一个基础设施，使用 Quartz Composer 来创建立体镜动画，我们希望有经验的设计师将使用它来创建酷的东西。苹果电脑也有一个独立的 3D 模拟器(还没有 iPhone 版本漂亮，但我们正在努力)。

将会有额外的工具用于 Mac 和 Windows，比如用于小电影的 Blinkenpaint 风格的编辑器和用于 Linux 和 BSD Unix 的更新的 blinkensim 模拟器。我们还会在网站上列出第三方工具。
 *关于这个项目还有什么人们应该知道的吗？*

我们所有的硬件和软件都将公开。无线调光技术将在知识共享许可下发布，新代码将获得 BSD 或 GPL 许可。我们仍然认为项目 Blinkenlights 是一个开放的平台，应该不断发展壮大。我们希望看到软件和硬件黑客都来承担我们已经完成的工作，并提出新的想法和扩展。

我们真的希望我们不会再次陷入这么长时间的无所事事，并能够尽快开展后续项目。这可能是一个很好的想法，以虚拟的方式展示以前的装置，但我想这是一个真实的世界，它变得有趣，因为人们需要有形的东西。没有什么能打败现实。

想参与进来吗？iPhone 应用程序是一个供人们实时观看的工具，也可以在开发动画时用作测试应用程序。

blinkenlights 团队最感兴趣的是人们为建筑创作滑稽的动画。他们提供了一个[扩展的工具集](http://blinkenlights.net/stereoscope/create),现在包括一个 Mac 上基于 Quartz Composer 的开发环境和一个用于跨平台处理的库。

他们现在正忙着设置提交表单，并将发布更多的背景信息。所以每个有兴趣参与的人都可以订阅 blinkenlights 博客。

他们还在开发一个基于 Java 的游戏 API，面向那些喜欢编写小应用程序的人，与用手机打电话的人进行互动。

如果你没有在 Twitter 上关注 [Tim，你应该关注一下！他最近](http://twitter.com/timpritlove)[在推特上](http://twitter.com/timpritlove/statuses/941558209)说他们已经订了披萨，而送披萨的人找不到那栋大楼，所以他们用“披萨来了”这句话点亮了那栋大楼

[图片:[安特妮](http://flickr.com/photos/antenne/2902395591/in/set-72157607534508166/)