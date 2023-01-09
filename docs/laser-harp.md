# 激光竖琴

> 原文：<https://hackaday.com/2009/12/23/laser-harp/>

![](img/b8cd8b3634b898409f06988bc1b497cf.png "laser-harp")

[Jared]有一束以前项目遗留下来的激光，他用它制作了这个激光竖琴。它的外观让我们想起了一个非常小的[古筝](http://en.wikipedia.org/wiki/Koto_%28musical_instrument%29)或者可能是一个[自动竖琴](http://en.wikipedia.org/wiki/Autoharp)(尽管在这个模型上和弦不能改变)。

我们很高兴[Jared]花时间为乐器制作了如此精美的琴身。传统上在竖琴上产生声音的琴弦已经被照射在硫化镉光敏电阻上的激光二极管所取代。当光束中断时，Arduino 通过 CdS 电池检测到变化，并通过表壳内的 Altec Lansing 扬声器播放声音。

不幸的是，没有可用的视频，但我们很确定它会发出“皮尤-皮尤”的声音。有一个下载源代码的链接，但它指向概述页面，而不是可下载的代码。从 [fritzing](http://hackaday.com/2009/08/25/fritzing/) 图来看，CdS 单元是分压器的一部分，该分压器向 Arduino 提供数字逻辑。这应该很容易复制，即使没有看到[Jared 的]代码，我们相信你可以从其他 Arduino 乐器项目中获得关于[wave shield](http://hackaday.com/2009/12/02/x-mas-hack-8-channel-musical-show/)或[midi 功能](http://hackaday.com/2009/10/27/these-midi-controllers-stink/)的提示。

[感谢廉价的蔬菜园丁]