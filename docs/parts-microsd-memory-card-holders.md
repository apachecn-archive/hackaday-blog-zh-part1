# 零件:MicroSD 存储卡支架

> 原文：<https://hackaday.com/2008/10/06/parts-microsd-memory-card-holders/>

![](img/c2e0a6bf87b29a2afb107bfe2fae3788.png "usd-holder-header-450")

SD 卡为你的项目增加了廉价的永久存储器，但是支架占用了大量的电路板空间。一个更小的选择是 [microSD](http://en.wikipedia.org/wiki/MicroSD) flash 格式。MicroSD 卡与普通 SD 卡兼容，大多数都带有免费适配器。我们为我们的[迷你网络服务器](http://hackaday.com/2008/09/25/web-server-on-a-business-card-part-2/)寻找了四个持有者。你应该选择哪个？阅读下面我们的经验。

![](img/09aec36c6d40bc374019fdbab9ca8b55.png "usd-holders450")

下面是上述交叉卡持有者的分类:

Alps[scha1b 0100](http://www.mouser.com/Search/ProductDetail.aspx?R=SCHA1B0100virtualkey68800000virtualkey688-SCHA1B0100)$ 1.27-你能从第一个支架的孔中看到大头针吗？他们很难看到，几乎无法接近。我们没有发现这个固定器对原型制作非常有用。

JAE[ST 6s 008 v4 ar 1500](http://www.mouser.com/Search/ProductDetail.aspx?R=ST6S008V4AR1500virtualkey65610000virtualkey656-ST6S008V4AR1500)$ 1.46——这是另一款在前面有插销的型号，但是这些插销更靠前，更容易拿取。焊接起来还是会很痛，如果可能的话尽量避免。

spark fun[PRT-00127](http://www.sparkfun.com/commerce/product_info.php?products_id=127)$ 3.95——最后，一个背后有别针的支架。这是一个相当容易焊接的部分，但它并不理想。焊接片非常小，稍微凹进屏蔽下面。这也是我们见过的最贵的 microSD 支架。SparkFun 在[他们的库](http://www.opencircuits.com/SFE_Footprint_Library_Eagle)中有这个零件的 [Cadsoft Eagle](http://www.cadsoft.de) 足迹。我们认为 Molex[538-502702-0891](http://www.mouser.com/Search/ProductDetail.aspx?qs=xbccQsLEe0ep5GA560fwAA%3d%3d)($ 3.58)很可能非常相似。我们将这个支架用于迷你网络服务器。

Alps[scha2b 0300](http://www.mouser.com/Search/ProductDetail.aspx?R=SCHA2B0300virtualkey68800000virtualkey688-SCHA2B0300)–1.27 美元–这款支架两侧的长插脚易于焊接。支架是反的，这意味着卡是上下颠倒插入的。反向支架在全表面贴装电路板上看起来很奇怪，但它们非常适合通孔设计。还没有老鹰的足迹，但是我们会给第一个[做出一个](http://www.instructables.com/id/How-to-make-a-custom-library-part-in-Eagle-CAD-too/)的人送一个 SCHA2B0300 下面是[数据表](http://www3.alps.com/WebObjects/catalog.woa/E/PDF/Connector/microSD_Card/SCHA/SCHA.PDF) (pdf)。

查看我们之前的[部分](http://hackaday.com/category/parts/)帖子: [0.1uF 去耦电容](http://hackaday.com/2008/09/29/parts-01uf-decoupling-capacitors/)、 [LM317 可调稳压器](http://hackaday.com/2008/09/22/parts-lm317-adjustable-voltage-regulator/)和[触摸开关](http://hackaday.com/2008/09/15/tact-switches-for-your-next-project/)。