# 使用继电器

> 原文：<https://hackaday.com/2008/12/05/working-with-relays/>

![relay](img/f983805b7936d4b2a6027e967b6957a5.png "relay")

SparkFun 的最新教程向你展示[如何使用继电器](http://www.sparkfun.com/commerce/tutorial_info.php?tutorials_id=119)。继电器是一种电动开关。在这种情况下，他们用它来切换 120 伏交流电插座。这篇文章带有关于如何不要用 AC 杀死自己的标准警告(加上一些贯穿全文的非序列链接)。作为额外的预防措施，他们选择了 GFI 的一家分店。您可能知道中继是如何工作的，但是值得看看他们是如何实现的。他们使用晶体管来防止微控制器的 GPIO 引脚过载。控制引脚被拉至地，以保持继电器关闭。一个二极管跨接在继电器线圈上，用于控制继电器放电时的电流。包括一个 LED 指示灯，用于显示继电器何时闭合。这是一个自动化项目的伟大基础，或者也许你只是想[恐吓你的猫](http://www.plasma2002.com/blenderdefender/ "Blender Defender")。