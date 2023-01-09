# 来自读者:低电量断电解决方案

> 原文：<https://hackaday.com/2011/12/01/from-the-readers-low-battery-cutoff-solutions/>

在周一更换电池帖子的评论区中，我们得到了很多关于低电量切断选项[的非常棒的反馈。提醒您一下，一些电动工具的电池被锂聚合物电池所取代，如果在充电前电量过低，电池可能会损坏。我们曾以为现在许多锂电池都有断路电路。一致的意见是，这些电池没有，因为他们是为钢筋混凝土应用的重量是一个问题。但是我们确实收到了很多人发来的商业解决方案，大部分来自 RC 爱好商店，所以如果你感兴趣的话，可以四处搜索一下。](http://hackaday.com/2011/11/29/pros-and-cons-of-replacing-tool-batteries-with-lithium-polymer/#comments)

[Christopher]发给我们一个链接，链接到他为他的自行车灯建造的切断电路。你可以在上面看到它的示意图([直接链接](https://github.com/unixbigot/Flat-Mate/raw/master/hw/flatmate.png))。他采购了一个 ATtiny45 来驱动一个 MOSFET，当电池电量过低时，它会断开电池。这将很容易适应其他用途，但请注意，这涉及到一个稳压器和一些其他无源器件…这不是一个困难的解决方案，但也不那么简单。

同样的概念也可以适用。一些评论者提到使用晶体管(或 MOSFET ),其基极由包含齐纳二极管的分压器驱动。这样，当达到阈值时，二极管的额定电压将有效地关闭栅极。

我们也喜欢阅读关于[比尔的] [人类控制的切断电路](http://hackaday.com/2011/11/29/pros-and-cons-of-replacing-tool-batteries-with-lithium-polymer/#comment-522546)。它还使用了齐纳二极管，但这次是与电阻器和 LED 串联，并插入工具的触发器中。当电池状态良好时，LED 会发出明亮的光。它将在接近结束时变暗，并且在达到临界极限时无法点亮。只要确保你在集中注意力并且状态良好。