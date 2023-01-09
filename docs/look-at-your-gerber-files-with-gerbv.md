# 用 Gerbv 看你的 Gerber 文件

> 原文：<https://hackaday.com/2009/09/03/look-at-your-gerber-files-with-gerbv/>

![gerbv_with_loaded_gerber_files](img/d26108df8b09f97e2f0fedf4d9cbea7a.png "gerbv_with_loaded_gerber_files")

厌倦了做幼儿园通心粉艺术 PCB？使用 Gerber 文件查看器检查您的 [Gerber](//en.wikipedia.org/wiki/Gerber_file) 文件，然后将它们发送到工厂。 [Viewplot](http://www.viewplot.com/) ，GerbTool 的[查看器](http://www.wssi.com/)，以及 FAB 3000 [免费 DFM](http://www.numericalinnovations.com/index.asp?PageAction=Custom&ID=71) 都是免费版本的付费软件，可以查看你的 Gerber 文件。如果您使用 Windows 和演示软件，这些都是不错的选择。如果没有，可以用 [gerbv](http://gerbv.sourceforge.net/) 。与 [gEDA](http://geda.seul.org/) 结盟，Gerbv 是免费的开源软件，您可以使用它来查看您所有的 RS-274X Gerber 文件和 Excellon 类型的钻孔文件。gerbv 仍在一个活跃的开发小组中工作，它并不具备所有的功能，它确实有删除对象的能力。休息之后来看看。

“你应该在运输前检查一下，否则你可能会在错误的地方留下洞。当你使用它时，一个鲜为人知的功能是你也可以删除东西！”-[ [扎克班克斯](http://hackaday.com/author/zbanks/)

首先，确保您已经安装了 gerbv 版本 2.1.0 或更高版本的 [cairo](http://cairographics.org/) 。

将以下几行复制并粘贴到文本文档中，然后随意保存:

*
% fs lax 24y 24 * %
% MOIN * %
% add 10c，0.250 * %
D10 *
x 00000y 00000d 02 *
x 10000y 00000d 01 *
x 10000y 10000d 01 *
x 00000y 10000d 01 *
x 0000y 0000d 01 *
x 05000

您现在将拥有一个简单的 Gerber 文件，您可以查看和使用它。通过命令行或启动 gerbv，然后选择“打开图层”…
![Gerbv with Loaded Gerber File](img/bfdbdbddfb827d213c5175d1d6f24e53.png "Gerbv with Loaded Gerber File")，在 gerbv 中打开它

现在，您应该会在屏幕右侧看到一个圆角矩形，里面有一个点。

如果它尚未突出显示，请单击屏幕顶部的箭头按钮进入对象选择模式。

![Gerbv with Selected Object](img/d50a85af95ca96c3768fd4ccaf5a5c52.png "Gerbv with Selected Object")

点击左右，您应该能够选择各种 Gerber 对象。您还应该能够绘制一个选择窗口来选择对象组。选择一个物体，在这张图片中，它显示了选中的中心闪光(点)。按 delete 键，你应该会得到一个弹出的窗口，询问你是否真的想要删除这个对象。继续删除那个对象，这就是为什么给你提供了小 Gerber 文件。

![Gerbv with Deleted Object](img/816988da404ae346cd465b051427b75e.png "Gerbv with Deleted Object")

你现在应该看到闪光消失了。如果没有，您应该检查以确保您处于正确的图层。您现在可以保存修改后的 Gerber 文件。

当然，这只是在 gerbv 中删除对象的一个例子。继续黑下去。