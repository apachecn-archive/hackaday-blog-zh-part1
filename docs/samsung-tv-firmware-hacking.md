# 三星电视固件黑客

> 原文：<https://hackaday.com/2009/10/18/samsung-tv-firmware-hacking/>

![tv-firmware-hacking](img/acefe56159f3c60b27da9b3592e9278b.png "tv-firmware-hacking")

[艾尔丹姆]正通过一个名为 SamyGo 的项目带头对三星电视固件进行逆向工程。三星官方固件使用 Linux 内核，这使它成为许多开发人员熟悉的系统。到目前为止，他们已经实现了通过网络共享文件的 NFS 和桑巴，改进了 USB 设备的播放，并解锁了使用非三星 WiFi 加密狗的能力。

为了对系统进行更改，您需要[在设备](http://sourceforge.net/apps/mediawiki/samygo/index.php?title=How_to_enable_Telnet_on_samsung_TV%27s)上启用 telnet 连接。SamyGo 团队通过在十六进制编辑器中更改固件的官方版本来在引导时启动 telnet 守护程序，从而实现了这一点。然后，使用三星的内置升级系统刷新这一修改后的固件。启用 telnet 后，可以手动刷新非官方固件。

我们很乐意看到这个项目在未来扩展到其他电视品牌。事实上，早在 6 月份，当我们意识到我们的索尼 Bravia 运行 Linux 内核并可以通过 USB 驱动器更新时，我们就在寻找类似的东西。如果你想尝试这个，要小心。我们只能想象在告诉你的另一半你用砖头砸了一台高价液晶显示器后的后果。