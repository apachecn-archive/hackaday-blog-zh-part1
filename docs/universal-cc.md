# 万能信用卡在你的手中

> 原文：<https://hackaday.com/2009/09/23/universal-cc/>

![universal_credit_card](img/b953d8e5fcacd0abf367547a7d66f8e3.png "universal_credit_card")

还记得《终结者 2》里的磁卡欺骗器吗？这有点牵强，因为显然这种设备可以通过读卡器刷卡，神奇地显示出工作账号和个人识别码。随着按钮可编程的[Jaroslaw 的][卡片欺骗器的出现，我们正在接近这种神奇的效果。](http://www.soniktech.com/sonik-dynamik-magnetic-card-encoder.html)

在一个允许通过 iPod 和电磁铁进行欺骗的项目的基础上，[Jaroslaw]想要一种不需要计算机来组合卡代码的东西。他通过将 16 按钮键盘和字符 LCD 与 AVR ATmega168 微控制器接口来实现这一点。可以用按钮输入卡代码，并在 LCD 上验证。当然，这仍然依赖于你首先知道代码。

如你所知，信用卡使用这项技术。我们不认为沃尔玛会同意你在收银台排队结账，更不用说当地的 five-oh。这项技术也用于大学、企业和酒店的建筑通道。如果与其他[间谍技术](http://hackaday.com/2009/09/22/photographic-key-duplication/)结合使用，你将成为一名特工。