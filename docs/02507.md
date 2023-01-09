# 如何:Leopard 网络上的 Windows Media Center

> 原文：<https://hackaday.com/2008/09/23/how-to-windows-media-center-on-a-leopard-network/>

![](img/e5022d27dfb236826904f0a07c16ff74.png "mce_leopard")

我们使用微软的媒体中心已经有几年了，并且越来越喜欢它。我们还注意到，越来越多的苹果电脑出现在我们的家庭网络中，并决定是时候让一切顺利合作了。请跟随我们一起走过我们跳过的所有环节，让一切都相互配合。

为了让事情变得简单，我们可以抛弃媒体中心，到处使用 MAC 电脑。苹果电脑缺少的一个东西是一个完整的 10 英尺电视接口。当然，你可以选择[广场](http://elan.plexapp.com/)、[前排](http://en.wikipedia.org/wiki/Front_Row)、[电视](http://www.mahalo.com/Eyetv)；虽然它们各有千秋，但没有一个能像微软的媒体中心那样给用户提供完整的单一电视观看体验。

通常所说的 MCE 可以使用一个遥控器从一个界面播放 DVD、音乐、视频和广播电视。我们希望建立一个家庭网络，将我们所有的媒体集中起来，为苹果电脑提供 [Time Machine](http://www.apple.com/macosx/features/timemachine.html) 备份，并充当 bittorrent 客户端和打印服务器。

我们知道我们可以很容易地设置另一台 Windows 机器来充当服务器，但 Time Machine 只支持写入 Mac 格式的驱动器。有信息显示[如何绕过这个](http://www.macosxhints.com/article.php?story=20071028173642747)，但是我们不想使用不支持的方法来冒险备份。[运行 NAS 盒](http://hackaday.com/2008/07/05/hackit-network-attached-storage/)也是出于同样的原因。

1TB 的时间胶囊可能是我们问题的答案，因为它支持时间机器备份，我们可以为 Windows 电脑插入 FAT32 格式的 USB 驱动器。这里的问题是关于 [4GB 的文件大小限制](http://support.microsoft.com/default.aspx?scid=kb;en-us;314463)，因为大多数录制的高清节目都在 6-15GB 之间。我们需要一个支持更大文件大小的文件系统，如 [NTFS](http://en.wikipedia.org/wiki/NTFS) 或 [HFS+](http://en.wikipedia.org/wiki/HFS%2B) 。

我们决定在运行 Leopard 的 Mac 上运行我们的服务器。所有的驱动器将被 Mac 格式化，以处理大文件大小，这将允许本机时间机器备份。只要我们在 Leopard 中启用了 SMB 支持，Windows 电脑就能够毫无问题地读写 Mac 驱动器。

由于这将是一台功能齐全的计算机，我们可以将其配置为打印服务器以及 bittorrent 客户端。我们的列表相当简单，显示了启动和运行混合计算机网络并不需要太多。

**硬件**

*   Mac 桌面
*   运行 Leopard 和 Windows Media Center 的客户端电脑
*   4 个硬盘
*   USB 打印机

**软件**

*   [调整用户界面](http://www.microsoft.com/windowsxp/downloads/powertoys/xppowertoys.mspx)
*   [调整 MCE](http://www.microsoft.com/downloads/details.aspx?FamilyID=3400190A-511A-4A3A-9B89-524511A76F58&displaylang=en)
*   [传输](http://www.transmissionbt.com/)
*   [读者通知者](http://troelsbay.eu/software/reader)
*   [微软远程桌面客户端](http://www.microsoft.com/mac/products/remote-desktop/default.mspx)

**附加设置信息**

*   工作家庭网络
*   分配给服务器和 MCE 计算机的静态 IP
*   从路由器到服务器和 MCE 计算机的有线连接
*   Media Center 计算机应该使用相同的管理员登录名和密码进行设置，并启用自动登录。
*   [使用 VIDEO_TS 结构抓取的 DVD 电影](http://hackaday.com/2008/07/11/hackit-ripping-dvds/)

由于我们的服务器将主要用于托管网络驱动器，我们真的不需要最新和最好的计算机。我们的数字媒体中心是第一代 1.42 GHz PPC Mac mini，配有 1GB 内存、80GB 硬盘、蓝牙和 AirPort Extreme。

我们使用了 3 个 375GB 的 Seagate 驱动器，每个驱动器都放在各自的 FireWire 机箱中。我们还在清仓时买了一个 500GB 的 Iomega FireWire 驱动器作为我们的时间机器磁盘。我们[选择 FireWire 而不是 USB](http://en.wikipedia.org/wiki/USB#USB_compared_with_FireWire) 的原因是处理器负载的问题。由于 USB 需要 CPU 来决定数据的去向，不像 FireWire 的点对点方法，我们觉得最好是尽可能减轻 CPU 的负担。

![](img/e2d45bdcb92b765c14ca1131dc2d2fdb.png "mini-server")

我们也考虑过使用 Power Mac G4/G5，但喜欢 Mac mini 的尺寸。即使有 4 个外部驱动器，整个东西也很适合我们的书架。无论你决定使用哪种 Mac，只要确保它满足运行 Leopard 的最低规格即可。

在初始操作系统安装和更新之后，我们开始一个接一个地格式化驱动器。使用 Leopard 的磁盘工具，我们将每个外部驱动器格式化为 *GUID 分区、Mac OS 扩展(日志式)*

![](img/1d1d0cc150a8d95ee1030fc5fabdabc4.png "disk-utility")

接下来，每个驱动器都被赋予了一个逻辑名称，按照它们在 mini 下的安装顺序: *HDD001* 、 *HDD002* 、 *HDD003* 和时间机器。 *HDD001* 将作为我们的一个 DVD 驱动器，以及用于保存我们共享的音乐、照片和种子的驱动器，所以我们创建了以下文件夹:*我的 DVD*、*我的音乐*、*我的图片*和*种子*。 *HDD002* 将仅用于 DVD，因此驱动器只有一个标记为*My DVD*的文件夹。这使得硬盘 003 成为录制 MCE 节目的驱动器，因此创建了一个名为 RecordedTV 的文件夹。Time Machine 驱动器上没有创建文件夹，因为连接到它的每台 Mac 在备份时都会创建自己的文件夹。

然后，我们继续创建将访问驱动器的不同用户配置文件。为了方便起见，我们在 MCE 计算机上使用了相同的管理员登录和密码，但是我们没有将它们作为管理员组的一部分，而是将它们作为标准用户组的一部分。因为我们对每台 MCE 计算机使用相同的登录，所以我们只需在服务器上创建一个用户。对于 Mac 电脑，我们使用电脑本身使用的个人登录名和密码，并且只给他们共享帐户。

![](img/dfd2c84e0d9057a38ffc767255a832dd.png "file-sharing")

从这里，我们开始启用文件共享设置，添加 4 个驱动器中的每一个，并为每个驱动器分配不同的用户。我们为 Mac 帐户创建不同的登录帐户而不是使用一个像 MCE 帐户一样的通用帐户的原因是为了给每个用户不同的访问权限。有些人只需要访问时间机器，而其他人需要访问其他驱动器。通过不同的帐户，我们能够指定哪些帐户可以访问哪些驱动器。因为我们希望能够在 Windows 下映射驱动器，所以我们通过单击*选项*按钮为 MCE 用户启用了 SMB 支持。

我们还想远程登录到计算机，因为这种设置将在没有显示器、键盘或鼠标直接连接的情况下运行。通过启用*远程管理*服务，我们现在可以通过另一台 mac 电脑或运行 [VNC 客户端的电脑来管理电脑，就像在 iPhone](http://www.mochasoft.dk/iphone_vnc.htm) 上一样。

我们的 Mac 附带了一个内置的 WiFi 卡，当客人来访时，我们将它用作第二个 WiFi 接入点。这是一种让他们上网的简单方法，我们不必给出我们主要 WiFi 连接的密码。

![](img/ea6ffc907f19961929c301a4e6021aa7.png "internet-sharing")

在互联网共享下，我们选择*以太网*作为我们想要共享的连接，选择*机场*作为访客连接。在机场选项下，我们给了它[一个不同于主连接的 SSID](http://en.wikipedia.org/wiki/SSID) 。现在，当客人来访时，我们可以远程访问服务器并启用连接，当他们离开时，我们会禁用服务。

我们希望我们的服务器做的最后一件事是自动下载种子。这需要安装阅读器通知和传输。Reader Notifier 与 [Google Reader](http://www.mahalo.com/Google_Reader) 协同工作，将根据我们对种子目录的 RSS 订阅自动下载种子文件。传输，然后设置为自动监控这个目录的新种子文件，一旦读者通知下载种子，传输开始下载。

![](img/18b947e508b5a67436b3b7970c68f0f8.png "rss-reader")

如果我们想添加一个新的种子源，我们只需将其添加到谷歌阅读器。因为传输设置为监控种子目录，如果任何人从任何计算机手动将种子文件放入该目录，下载也将自动开始。

MCE 的 2005 和 Vista 版本都不支持写入网络连接驱动器。通过 TweakMCE 对注册表进行了一些修改，我们纠正了这个问题，并在此过程中添加了一些增强功能。

![](img/251fe50f15f418386f40ad4bd0aeec45.png "mce-service")

我们首先找到 3 个媒体中心服务，并暂时停止它们。一次一个，我们双击每个服务，在登录选项卡下，将默认设置更改为“此帐户框”,并输入计算机的管理员名称和密码。

![](img/09bc91c34273ab6a9a2c5e0f6621a09b.png "recordedtv")

在服务仍然停止的情况下，我们启动了 TweakMCE 并导航到录制的电视的存储位置，并将当前路径替换为指向新服务器的 UNC 路径。我们对录制的电视节目的【T4 观看】文件夹也做了同样的处理。

![](img/509a4174a7c6f5c19ee87e0a0fd9c8d1.png "my-dvds")

为了充分利用我们的 DVD 存储在服务器上的优势，我们还启用了 TweakMCE 的 *DVD* 菜单下的*My DVD*选项。

保存我们的每个更改并退出 TweakMCE 后，我们继续映射我们将使用的每个网络驱动器，确保使用相同的用户名和密码，并选择“登录时重新连接”选项。这将确保在重新启动的情况下，驱动器将始终重新连接。

然后，我们重新启动计算机，一旦回来，启动 MCE。在*视频*菜单下，我们添加了新的驱动器，确保包含 2 个*我的 DVD*文件夹，因为 MCE 将使用这些信息来填充主屏幕上新的*我的 DVD*菜单。将网络路径添加到*我的音乐*和*我的图片*目录也允许 MCE 计算机访问相同的内容。

像服务器一样，我们想要远程管理这些计算机，所以我们启用了*远程桌面服务*。微软为苹果电脑开发了一个免费的客户端，XP MCE/专业版内置了远程客户端。除了播放我们想要的各种文件所需的不同编解码器之外，不需要任何进一步的配置。

设置 Mac 相当快，因为我们将连接到另一台 Mac 的驱动器。启动 Finder 后，我们将服务器放在窗口的左侧。选择服务器，输入在服务器上创建的共享用户名，将登录信息保存到钥匙串中。

![](img/c43b0adb07f1c3dbae76681cb91018ff.png "time-machine")

启用 Time Machine 使用网络驱动器等同于选择本地连接的驱动器。在 Time Machine 偏好设置屏幕中，选择*更换磁盘*选项以显示所有连接的驱动器。在选择了标有*时光机*的驱动器后，我们退出了屏幕，不需要黑客攻击。

与 Windows 电脑不同，OS X 不会在重启时自动挂载网络驱动器。如果我们无法安装驱动器，时间机器将无法执行备份..我们发现的最简单的方法是在登录时创建一个 Automator 脚本来装载驱动器。

![](img/1b3a3cb548453be6e7cd5e58fd76b1b9.png "automator")

我们的第一步是让 Automator 通过 IP 调用我们想要挂载的每个驱动器。一旦我们指定了我们需要的驱动器，下一步就是让 Automator 连接到服务器来安装驱动器。一旦我们通过*运行*按钮确认它连接到了正确的驱动器，我们就将它保存为一个应用程序，并放在我们的应用程序文件夹中。然后，我们将它添加到我们希望访问驱动器的每个用户的登录项中。现在登录后，脚本将自动运行并连接到驱动器。

随着我们的服务器现在开始运行，MCE 计算机现在可以访问电影、音乐、图片和共享录制节目的驱动器。如果我们家客厅的电脑录了一集《太空堡垒 Galatica》，家里所有的 MCE 电脑都可以访问。此外，有了 MCE，我们现在可以在家里的任何地方访问我们所有的 DVD。

因为我们选择将 Mac 作为服务器，所以我们网络上的 Mac 现在可以与 Time Machine 无线备份，并共享一台打印机。

如果我们必须再做一次，我们会选择基于英特尔的 mini，因为它配备了千兆以太网，不像 G4 的快速以太网。除此之外，我们应该使用更大的驱动器，并尝试 Leopard 的内置软件 RAID。除此之外，我们对新家庭网络很满意。