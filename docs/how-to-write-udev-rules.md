# 如何编写 Udev 规则

> 原文：<https://hackaday.com/2009/09/18/how-to-write-udev-rules/>

自从采用内核 2.6 以来，Linux 一直使用 [udev 系统](http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev.html)来处理 USB 连接的外围设备等设备。如果你想改变插入 USB 端口时的行为，这一部分就是为你准备的。作为一个例子，我们将使用 USB 拇指驱动器，但这些方法应该翻译成任何由 udev 处理的设备。作为本练习的目标，我们决定创建一个符号链接，并在加载特定的拇指驱动器时执行一个脚本。我们在这个练习中使用的操作系统是 Ubuntu 9.04 Jaunty Jackalope。

### 背景调查

在编写规则之前，我们必须收集识别设备所需的所有信息。通过插入并检查`/var/log/messages`，我们找到了驱动器被分配到的[块设备节点](http://en.wikipedia.org/wiki/Device_node#Block_devices)。然后，我们将该位置(/dev/sdd1)传递给我们同时运行的两个命令。有些发行版使用“udevinfo”命令，但在 Ubuntu 9.04 中，该命令已更改为“udevadm info”:

```
udevadm info -a -p $(udevadm info -q path -n /dev/sdd1)
```

它的输出非常丰富。我们需要找到提供用于安装可移动存储的块节点的链的顶端(在我们的例子中是/dev/sdd1)。使用这个内核作为标识将确保我们的符号链接指向一个可挂载的块设备，而不是 USB 控制器的某个部分。我们还在寻找设备特定的标识符，以便将这个特定的拇指驱动器与所有其他的区别开来:

```
looking at device '/devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2:1.0/host29/target29:0:0/29:0:0:0/block/sdd/sdd1':
 KERNEL==&quot;sdd1&quot;
 SUBSYSTEM==&quot;block&quot;
 DRIVER==&quot;&quot;
 ATTR{partition}==&quot;1&quot;
 ATTR{start}==&quot;63&quot;
 ATTR{size}==&quot;31310622&quot;
 ATTR{stat}==&quot;     208    15448    16282      776        2        0        2       12        0      508      788&quot;

looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-2':
KERNELS==&quot;1-2&quot;
 SUBSYSTEMS==&quot;usb&quot;
 DRIVERS==&quot;usb&quot;
 ATTRS{configuration}==&quot;&quot;
 ATTRS{bNumInterfaces}==&quot; 1&quot;
 ATTRS{bConfigurationValue}==&quot;1&quot;
 ATTRS{bmAttributes}==&quot;80&quot;
 ATTRS{bMaxPower}==&quot;200mA&quot;
 ATTRS{urbnum}==&quot;1858&quot;
 ATTRS{idVendor}==&quot;13fe&quot;
 ATTRS{idProduct}==&quot;1f00&quot;
 ATTRS{bcdDevice}==&quot;0110&quot;
 ATTRS{bDeviceClass}==&quot;00&quot;
 ATTRS{bDeviceSubClass}==&quot;00&quot;
 ATTRS{bDeviceProtocol}==&quot;00&quot;
 ATTRS{bNumConfigurations}==&quot;1&quot;
 ATTRS{bMaxPacketSize0}==&quot;64&quot;
 ATTRS{speed}==&quot;480&quot;
 ATTRS{busnum}==&quot;1&quot;
 ATTRS{devnum}==&quot;69&quot;
 ATTRS{version}==&quot; 2.00&quot;
 ATTRS{maxchild}==&quot;0&quot;
 ATTRS{quirks}==&quot;0x0&quot;
 ATTRS{authorized}==&quot;1&quot;
 ATTRS{manufacturer}==&quot;OCZ&quot;
 ATTRS{product}==&quot;DIESEL&quot;
 ATTRS{serial}==&quot;50E6920B000AE8&quot;
```

在编写 udev 规则时，这些特征中的任何一个都可以用作规则执行的条件。也就是说，只有来自 **设备的一个** 父设备和来自设备本身的属性可以匹配。尝试匹配链中多个父项的值将是无效的，并且不起作用。

### 规则

规则文件存储在`/etc/udev/rules.d/`目录中。我们从该目录中的自述文件中获得了一些关于如何命名规则文件的建议:

> 文件应命名为 xx-descriptive-name.rules，xx 应根据以下顺序点首先选择
> :
> 
> < 60  most user rules; if you want to prevent an assignment being
> 覆盖默认规则，使用:=运算符。
> 
> 这些不能访问持久信息，例如来自
> vol_id 的信息
> 
> < 70 条运行 vol_id 等帮助程序来填充 udev 数据库的规则
> 
> udev db)
> 
> > =90 条应该最后运行的规则

我们计划用这个规则运行一个脚本，所以我们给它起了一个名字，这个名字以一个比其他规则大但小于 90 的数字开始。我们使用了文件名:

```
81-thumbdrive.rules
```

udev 规则的第一部分是匹配的密钥。我们将使用链最顶端的内核条目以及设备特定信息中的 idVendor、idProduct 和 serial 属性。这将肯定地识别这个特定的拇指驱动器，并忽略所有其他驱动器。内核参数使用一个问号作为通配符，这样如果我们的驱动器安装在不同的节点上(例如:sda1、sdb1、sdc1 等)。)它仍然可以被识别。

```
KERNEL==&quot;sd?1&quot;, ATTRS{idVendor}==&quot;13fe&quot;, ATTRS{idProduct}==&quot;1f00&quot;, ATTRS{serial}==&quot;50E6920B000AE8&quot;
```

现在我们有了识别我们正在寻找的特定硬件所必需的键，我们可以添加赋值参数。在我们的例子中，我们添加了两个。第一个在/dev/目录中创建一个指向该设备的符号链接。第二个在我们的主目录中执行一个脚本:

```
SYMLINK+=&quot;hackaday&quot;, RUN+=&quot;/home/mike/notify-plugin.sh 'HackaDay Thumbdrive:' 'Connected as: $KERNEL'&quot;
```

下面是最后一条规则:

```
KERNEL==&quot;sd?1&quot;, ATTRS{idVendor}==&quot;13fe&quot;, ATTRS{idProduct}==&quot;1f00&quot;, ATTRS{serial}==&quot;50E6920B000AE8&quot;, SYMLINK+=&quot;hackaday&quot;, RUN+=&quot;/home/mike/notify-plugin.sh 'HackaDay Thumbdrive:' 'Connected as: $KERNEL'&quot;
```

我们在规则文件中添加了这一行，然后使用以下命令重新启动 udev:

```
sudo nano /etc/udev/rules.d/81-thumbdrive.rules
sudo /etc/init.d/udev restart
```

### 脚本(和错误解决方法)

我们想使用前一段时间讨论过的[弹出通知，但是无法使用。经历了一点挫折之后，我们发现](http://hackaday.com/2009/09/03/simple-pop-up-notifications/)[notify-send 包在从 root 运行的脚本中调用时，无法将通知放到用户的屏幕上](https://bugs.launchpad.net/ubuntu/+source/libnotify/+bug/160598)。这个 bug 有一个[的变通办法。出于我们的目的，我们稍微修改了一下脚本，并将其粘贴到一个名为:/usr/local/bin/alt-notify-send 的新文件中](http://ubuntuforums.org/showthread.php?p=6889270#post6889270)

```
#!/bin/sh
user=`whoami`
pids=`pgrep -u $user gnome-panel`
title=$1
text=$2
timeout=$3
icon=$4

if [ -z &quot;$title&quot; ]; then
 echo You need to give me a title &gt;&amp;2
 exit 1
fi
if [ -z &quot;$text&quot; ]; then
 text=$title
fi
if [ -z &quot;$timeout&quot; ]; then
 timeout=60000
fi

for pid in $pids; do
 # find DBUS session bus for this session
 DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS \
 /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
 # use it

 #icon hack:
 if [ -z $icon ]; then
 DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS \
 notify-send -u low -t $timeout &quot;$title&quot; &quot;$text&quot;
 else
 DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS \
 notify-send -u low -t $timeout -i &quot;$icon&quot; &quot;$title&quot; &quot;$text&quot;
 fi
done
```

然后我们创建了 udev 规则调用的脚本。它位于我们的主目录/home/mike/notify-plugin.sh 中

```
#!/bin/bash

su mike alt-notify-send &quot;$1&quot; &quot;$2&quot; 6000 &quot;/home/mike/hackaday_icon.png&quot;
```

这个脚本可以做我们想要它做的任何事情。在这种情况下，它调用通知解决方法脚本，传递来自 udev 规则的两个字符串、一个延迟时间和一个与弹出窗口一起显示的图标。

### 事件顺序:

现在一切就绪，让我们来看看当我们的驱动器插上电源时会发生什么。

1.  -USB 驱动器已插入计算机
2.  -Udev 检查/etc/udev/rules.d/目录，并开始按顺序使用规则文件
3.  -Udev 访问我们的文件:81-thumbdrive.rules 并匹配“sd？1 英寸内核、idVendor、idProduct 和 u 盘序列号。
4.  -如果 udev 确认我们的四个条件匹配，则在/dev/hackaday 创建一个符号链接，并执行/home/mike/notify-plugin.sh 脚本，向它传递一条包含内核信息的消息。
5.  -我们的脚本使用 alt-notify-send 变通方法执行创建弹出通知。
6.  -HAL 接管，自动挂载我们的驱动器(这是 Ubuntu 可移动存储处理的一部分，与我们的 udev 规则无关)。

在这里，我们看到指向我们的数据块设备的符号链接和弹出通知:

![udev_symlink](img/05d6affcde18d204f8f9f912d7e13f63.png "udev_symlink")

![plugin_popup](img/1f693a6b1e0781109b11a37b71069846.png "plugin_popup")

### 其他用途:

Udev 规则让您可以控制连接到您机器上的硬件。如果您正在处理 USB 连接的项目，这些规则将允许您设置访问权限，在添加或删除时执行脚本，并提供访问此硬件的永久符号链接，而无需每次连接设备时都依赖相同的节点名称。我们使用 udev 规则允许 [avrdude](http://savannah.nongnu.org/projects/avrdude/) 在没有 root 权限的情况下访问我们的 [AVR Dragon](http://www.atmel.com/dyn/Products/tools_card.asp?tool_id=3891) 程序员。在这种情况下，我们的规则为所有者和组设置读/写权限，然后将设备分配给“plugdev”组。只要试图运行 avrdude 的用户是 plugdev 组的成员，该程序就能够访问 dragon。规则如下:

```
SUBSYSTEM==&quot;usb&quot;, ATTR{idVendor}==&quot;03eb&quot;, ATTR{idProduct}==&quot;2107&quot;, MODE=&quot;0660&quot;, GROUP=&quot;plugdev&quot;
```

我们希望这有助于阐明 udev 系统是如何工作的。在你的下一个项目中尝试一下。

### 资源:

*   丹尼尔·德雷克撰写 udev 规则:[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)
*   通知-发送 bug:[https://bugs . launch pad . net/Ubuntu/+source/lib notify/+bug/160598](https://bugs.launchpad.net/ubuntu/+source/libnotify/+bug/160598)
*   通知-发送解决方法:[http://ubuntuforums.org/showthread.php?p=6889270#post6889270](http://ubuntuforums.org/showthread.php?p=6889270#post6889270)