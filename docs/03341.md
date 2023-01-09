# 来自基本逻辑的通孔总线盗版套件

> 原文：<https://hackaday.com/2009/03/31/through-hole-bus-pirate-kit-from-fundamental-logic/>

![bpv1ath](img/70dfeef120a38399c1d050a4eb330708.png "bpv1ath")

基本逻辑是销售基于我们通用串行接口工具的[总线盗版套件](http://store.fundamentallogic.com/ecom/index.php?main_page=product_info&cPath=26&products_id=474)和[裸 PCB](http://store.fundamentallogic.com/ecom/index.php?main_page=product_info&cPath=26&products_id=475) 。他们从我们基于串口的 [v1a 硬件](http://www.buspirate.com)开始，修改后使用所有通孔部件。8 引脚 DIP[LP 2951 ACN](http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&name=LP2951CN-ND)/[-3.3](http://search.digikey.com/scripts/DkSearch/dksus.dll?Detail&name=LP2951CN-3.3-ND)可切换电压调节器取代了我们使用的表面贴装 [TPS79650](http://www.mouser.com/Search/ProductDetail.aspx?R=TPS79650DCQRvirtualkey59500000virtualkey595-TPS79650DCQR) / [33](http://www.mouser.com/Search/ProductDetail.aspx?qs=sGAEpiMZZMsGz1a6aV8DcPXeWoVS0Fnzr3zi8%252bAr99Q%3d) 。PIC 预编程有我们最新的[固件](http://code.google.com/p/the-bus-pirate/)，版本 0f，其中包括一个引导加载程序，通过串行端口轻松更新固件。文件包括图解的[组装说明](http://spiffie.org/kits/buspirate/assemble.shtml)。

说到总线盗版的好处，我们正忙着开发硬件 V2。正如敏锐的读者可能已经注意到的，总线盗版的最终版本包含一个 FTDI USB- >串行芯片，并从 USB 端口获取电源。我们还解决了软件控制的上拉电阻特性，减少了整体器件数量和成本。最重要的是，我们正在努力使组装好的印刷电路板可以在全球范围内运输。指南应该在几周内准备好。