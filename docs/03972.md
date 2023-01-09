# Firefox CSS Hack:更改导航图标

> 原文：<https://hackaday.com/2009/09/06/firefox-css-hack-change-navigation-icons/>

![firefox_custom_icons](img/7d8535bc9050eb085418189a8d389296.png "firefox_custom_icons")

为什么要满足于浏览器上的标准主页图标呢？如果你的 home 键把你带到[hackaday.com](http://hackaday.com)，为什么不让图标反映那个目的地呢？这种破解既快速又简单。我们将使用 Firefox 3 和带有标准大小图标的默认主题带你浏览一遍。

我们首先使用我们最喜欢的[图形程序制作一个 24×24 像素的图标](http://www.gimp.org/tutorials/Creating_Icons/)，然后保存为 PNG 文件，不进行压缩。

为了使用新图像作为主页图标，我们编辑了一个[级联样式表](http://en.wikipedia.org/wiki/Cascading_Style_Sheets)，它存储在文件 classic.jar 中。在 Ubuntu 9.04 上，这可以在/usr/lib/Firefox-3 . 0 . 13/chrome/中找到，但[该文件将位于其他操作系统上的其他地方](https://developer.mozilla.org/en/Creating_a_Skin_for_Firefox%2F%2FGetting_Started#Extract_Theme)。我们做了一个 classic.jar 的备份，然后解压内容( [JARs](http://en.wikipedia.org/wiki/JAR_(file_format)) 基本和 zip 文件一样)。

在解压后的文档中，我们导航到文件夹 /skin/classic/browser/ 并使用文本编辑器打开 browser.css 。这就是奇迹发生的地方，虽然我们只改变了主页按钮的图标，但是你还可以看到更多的可能性。我们更改了 #home-button 条目，以便图像 URL 指向使用 file:///格式的新文件。这是我们的改变后的样子:

```
#home-button {
 list-style-image: url("file:///path_to_our_icon/hackaday-icon.png");
}
```

我们保存了这个文件，然后将文件结构压缩成一个名为 classic.jar 的文件，并将其复制到我们最初找到它的位置。火狐的快速重启显示了新图标。请在评论中告诉我们你对 Firefox 的其他改进！

 ****更新:**【Colby】指出这种类型的 CSS 更改应该在“userChrome.css”文件中进行。他是对的，他是这样说的:

[找到你的用户档案目录](http://support.mozilla.com/en-US/kb/Profiles)，进入其中的“chrome”子目录。创建文件“user chrome . CSS”；可能已经有一个示例文件，您可以对其进行重命名。这个 CSS 文件的重要部分是告诉 Firefox 如何使用它的名称空间行。这是我们的样子:

```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */

#home-button {
 list-style-image: url("file:///path_to_our_icon/hackaday-icon.png") !important;
}
```

为了让 Firefox 能够听到我们的新图标，我们必须有“！重要”关键词。现在只需重启 firefox，享受你新家图标的荣耀。**