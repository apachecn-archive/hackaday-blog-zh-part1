# 将汽车充电器改装成可变电源

> 原文：<https://hackaday.com/2011/06/19/modding-a-car-charger-to-a-variable-power-supply/>

为了即将到来的公路旅行，[Patrick]需要一个小型可变电源。[Patrick]做了明智的事情，逆向设计了一个手机充电器来满足他的需求，而不是拖着一个工作台。

在撬开一个旧的京瓷汽车充电器后，[Patrick]发现了一个贴有完整标签的小型 PCB，所有元件都是通孔元件，这是非常好的逆向工程潜力。在 Semi MC33063 IC 上找到一个[之后，【Patrick】翻阅了数据手册，生成了一个网表，并开发了一个](http://www.onsemi.com/PowerSolutions/product.do?id=MC33063A)[原理图](https://5997623931453115636-a-1802744773732722657-s-sites.googlegroups.com/site/thejourneymanwizard/projects-and-bits/kyocera-car-charger/Schematic%20sketch.jpg?attachauth=ANoY7coZ3N27y7MxJPryvK6Rq5iYtAMRuMH2haKd2rzRsbuB75hUleVeBC8l2Fxf8MrM_6yywx80k87NnWvnPzvZVo08vTlhamUq4s_g-CC9a8ty0ZcHke4ams7inY0kCGUY7L9dBvLelXta3gZqUN8WjxzUMnSowOVPSyhAHStE5vG7pCFcB9c1v1B5sn08vQg-bJgDpteJt4hxTsTHoCwbqBWEln3mRsT-z6W26Kam9rVUGFQblNTaxLzGU3QXbYtQmmXMpaleDNGNNTxhRkahgLS3fUUWEg%3D%3D&attredirects=0)，与数据手册给出的参考原理图非常相似。

完成了所有繁重的工作后，[Patrick]开始着手完成他开始的工作——修改充电器以输出 3-10 伏的电压。在用一个 5k 的多圈罐替换了一个电阻之后，[Patrick]剩下的是一个输出电压从 2.8 到 8.8 伏不等的电源。不完全是所期望的，但是对于手边的应用来说已经足够了。虽然这个黑客不是迪斯科舞厅的地板，但它是一个很好的黑客过程演练——构建或修改一些东西来满足需要。