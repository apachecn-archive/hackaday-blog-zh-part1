# 坦南鲍姆股票，尽管市场因圣诞节而关闭

> 原文：<https://hackaday.com/2011/12/22/tannenbaum-ticker-even-though-the-markets-close-for-christmas/>

[![](img/22c964ddc043c4ab38f7fc906bff09bf.png "ticker")](http://hackaday.com/wp-content/uploads/2011/12/ticker.jpg)

也许我们有点苦涩，因为我们一直坚持到 11 月份，但我们必须尊重[尼克]的股票装饰。这是一个联网的圣诞装饰品，可以查询股票价格，并用 RGB LED 显示变化。

该构建使用一个 [Propeller 平台 USB](http://www.adafruit.com/products/312) 和 Propeller [E-Net 模块](http://gadgetgangster.com/find-a-project/56?projectnum=349)从谷歌下载股票报价。有了附带的源代码，选择任何交易公司都很容易；所有需要的是选择一个公司正在改变代码中的一行。在交易日中，Propeller 每 30 秒提取一次报价，并将其解析为“百分比变化”格式。如果变化超过 4%的负变化，装饰会发红光，如果在 0.2%的开放范围内，装饰会发绿光，如果超过 4%的正变化，装饰会发蓝光。

[Nick]更像是一个“一劳永逸”的投资者，所以这个装饰品是一种方便、被动的方式来监视他的投资。休息后请观看演示视频。

[https://www.youtube.com/embed/QbyvZmrN8Ns?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/QbyvZmrN8Ns?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)