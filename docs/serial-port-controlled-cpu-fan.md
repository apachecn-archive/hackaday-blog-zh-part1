# 串行端口控制的 CPU 风扇

> 原文：<https://hackaday.com/2010/09/08/serial-port-controlled-cpu-fan/>

![](img/b962011e20dd9bcd8a7cc0cac4a80b20.png "cpu_fan")

[Christian]正在运行一台 Linux 机器作为家庭服务器，但是[需要一种方法来安静嘈杂的机器](http://sites.google.com/site/chrisatronics/)。像许多 Linux 服务器一样，他使用一些非常旧的硬件，这些硬件没有 CPU 风扇的板载插头，而 CPU 风扇会产生很多不必要的声音。这些接头很好，因为软件可以监控 CPU 和主板的温度，并相应地调整风扇。

[Christian 的]解决方案是使用串行端口完成任务。他建立了一个小电路，其中串行引脚 3 驱动晶体管的基极，引脚 5 提供接地，软驱电源线提供 5 伏电压。在那里，他编写了一个 RUBY 程序来监控 CPU 温度，并在串行端口上生成一个 PWM 信号，根据需要调节风扇速度。

[CC 图片来源: [Garrette via Flickr](http://www.flickr.com/photos/garrette/53236643/)