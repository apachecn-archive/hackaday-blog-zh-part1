# 从 NOAA 气象卫星上获取您自己的图像

> 原文：<https://hackaday.com/2011/10/20/grab-your-own-images-from-noaa-weather-satellites/>

你能相信[hpux735]使用家用设备从国家海洋和大气管理局的一颗气象卫星上下载了这张卫星气象图像吗？原来，他们有三颗气象卫星在低地球轨道上，每天从头顶飞过几次。如果你有一些自制硬件和后期处理印章[，你可以从这些气象卫星上抓取你自己的图像](http://alternet.us.com/?p=1398)。

第一步是数据采集。[hpux735]使用他从套件中构建的软件定义无线电接收器。这让我们回想起[Jeri Ellsworth]使用 FPGA 构建的软件无线电项目——它能适用于这个目的吗？但是我们跑题了。为了记录输入数据，使用了名为 [DSP Radio](http://homepage.mac.com/smrozek/Sebastian_Mrozek/Download.html) 的 Mac 程序。一旦你捕捉到一个音频样本，你需要一些东西把它转换成图像。恰好有一个专门用于天气图像解码的程序叫做 [WXtoImg](http://www.wxtoimg.com/) ，另一个在 Linux 下运行的程序叫做 [WXAPT](http://5b4az.chronos.org.uk/pages/apt.html) 。加入一点后期处理，罗伯特是你母亲的兄弟，你就有了上面看到的图像。

[Hpux735]提到他正在撰写一篇关于他为该项目建造的天线的帖子，并对自动化系统有未来的计划，在该系统中，他将有一个始终显示最新图像的网页。我们期待着听到那件事。