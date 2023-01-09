# 简单的弹出通知

> 原文：<https://hackaday.com/2009/09/03/simple-pop-up-notifications/>

![simple_linux_notifications](img/6598fee45b0ad116683af2b84327460e.png "simple_linux_notifications")

[Kristofer]分享了一个关于向 Linux 脚本添加弹出通知的简单方法。libnotify 包允许您使用命令“notify-send”在需要时弹出消息。语法非常简单，只需将消息放在命令后面的引号中，如下所示:

```
notify-send "Go read hackaday.com"
```

这个命令还有很多其他选项，比如添加图标和设置消息显示的时间。这对于通过脚本进行交互的项目来说是非常好的，可以在事件发生时显示消息。对于 Ubuntu，安装这个包就像“sudo apt-get install lib notify-bin”一样简单。