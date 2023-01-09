# 一天问黑客:触摸屏黑客

> 原文：<https://hackaday.com/2009/12/03/ask-hack-a-day-touch-screen-hack/>

![](img/cf1288f3b5eb073d35d5c2be1f5e0fa8.png "touchadd")

读者[Chad Essley]问我们:

> “我想知道黑客们的庞大知识库是否知道某种方法，可以将几乎任何笔记本电脑变成某种触摸屏。其实任何表面。”

他有一台较旧的 Wacom 平板电脑，希望能够添加电阻式触摸屏功能，这样他就不会被迫使用 Wacom 笔。作为一名艺术家和兼职黑客，他甚至在一篇漫画风格的帖子中总结了这个问题。

我们知道一些工具，比如 [EZscreen](http://www.ezscreen.com/instant-touch.htm) instant touch:

![](img/08d1dd9920e8a2ba76a6ad74900bf041.png "EZ-Tablo-mounting")

which allow “Clip on Tablet abilities”, however you have to use their pen, which doesnt help with the tablet problem, but may help with your “any monitor” problem. Another solution is to buy a generic touch screen kit (usually on [eBay](http://shop.ebay.com/i.html?_nkw=touch+screens+kit&_sacat=0&_trksid=p3286.m270.l1313&_odkw=touch+screens&_osacat=0) from somewhere in China), and install it yourself. That will work for most laptops and desktop monitors, however we wouldnt recommend using it with your Wacom tablet, as it would probably interfere with the pen functionality. [Hak5](http://revision3.com/hak5/virtualshowdown) recently did an episode on Touchscreen kits, but there are also a number of places all over the internet to find [step-by-step](http://www.touchscreens.com/products-addon.html) how-tos for kits.![](img/462cd7afb953996526985b90e90ef70d.png "eee_kit")We dont think you could use an infrared camera from the side like in your drawing, because it would be very difficult to calibrate (wouldnt be able to tell the difference between cold hands, and hands that are farther away/etc in our opinions). Things like the Microsoft Surface use infrared, but from underneath (which is much easier for [machine vision](http://en.wikipedia.org/wiki/Machine_vision) to handle.) A flat, unlit surface (not like a monitor or a tablet) could use something similar to the [laser keyboard](http://www.virtual-laser-keyboard.com/).![](img/4f953ff70ef5b9c6d9f1d3b64cf7037f.png "bluetooth-virtual-keyboard")We have also covered a couple of gesture and touch based input tools which may help out anyone willing to take on this task. [TISCH](http://hackaday.com/2008/11/23/tisch-multitouch-framework/) is a top-down camera based multi-touch framework, and [Scratch Input](http://hackaday.com/2008/11/14/scratch-input/) is a tool for using acoustic signals on a wall or a table to interpret touch and drag motions.Unfortunately, that is about all the ideas we could come up with, but the Wikipedia page on [Wacom tablets](http://en.wikipedia.org/wiki/Graphics_tablet) might be a good place to start for background information on what could or could not work with this configuration. Hopefully some of our ideas will spark the interests and specialties of our readers, feel free to respond in the comments, or send any ideas to our tip line!Thanks again to [Chad] for his question, and feel free to send any other ideas for Ask Hack a Day.