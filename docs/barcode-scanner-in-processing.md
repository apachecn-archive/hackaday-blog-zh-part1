# 条形码扫描仪正在处理中

> 原文：<https://hackaday.com/2009/09/22/barcode-scanner-in-processing/>

![barcode_sc](img/5ce3674fe66ba963dcbac0cf0512e2de.png "barcode_sc")

读者【Nikolaus】决定不使用基于[现有](http://en.barcodepedia.com/)图像的[条形码解码器](http://hackaday.com/2008/11/10/messing-with-barcodes/)，而是由[自己编写](http://www.local-guru.net/blog/2009/09/22/barcodescanner-in-pure-processing)。使用[处理语言](http://en.wikipedia.org/wiki/Processing_(programming_language))他创造了一个扫描仪，当条形码位于图像中心时，它可以解析黑白图案。然后，他的代码解析该数据，并将其与初始化字符进行比较，以提供一个引用。目前他的扫描仪支持三种字符集的[代码 128 编码](http://en.wikipedia.org/wiki/Code_128)，并且[提供了他的完整代码](http://www.local-guru.net/processing/barcodescanner.pde)，以便其他人可以添加他们认为合适的代码。他承认由于冗长的字符表，代码有点乱，但是非常简单。