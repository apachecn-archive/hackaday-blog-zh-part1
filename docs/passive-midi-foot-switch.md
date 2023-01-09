# 无源 MIDI 脚踏开关

> 原文：<https://hackaday.com/2009/01/20/passive-midi-foot-switch/>

![foot](img/76c8aad2182f861b5cb29dbb707ddd8a.png "foot")

[Matt]正在寻找一些软件，这些软件允许他使用声卡作为控制模拟音频设备的一种方式。在看到它是如何工作的之后，他有了一个想法，试图做相反的事情。他正在发送一个信号到他的音频输入端，并通过管道传输到一个 MIDI 软件接口。他选择的输入是一个[脚踏开关](http://meshlabs.net/2009/01/passive-footswitch-to-midi-using-your-soundcard/)。为了产生信号，他只需要在按下开关时提供电压。你可以在上面看到，他用电池和一个简单的接触开关来发送信号。然后，他使用 [Maple 虚拟 MIDI 电缆](http://www.hurchalla.com/Maple_driver.html)将其连接到虚拟 MIDI 端口。不幸的是，这不适合旋钮，但这可能是他的清单上的下一个。