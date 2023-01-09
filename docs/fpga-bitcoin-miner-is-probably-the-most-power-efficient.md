# FPGA 比特币矿工可能是最省电的。

> 原文：<https://hackaday.com/2011/08/22/fpga-bitcoin-miner-is-probably-the-most-power-efficient/>

[fpgaminer]，[Li _ 易刚]和[newMeat1]在过去的几个月里一直在合作开发一个 FPGA 比特币挖矿器，它在能效方面让 GPU 采矿设备望尘莫及。该板每秒 100 Mhashes 只需要 6.8 瓦，但[李 _ 易刚]的博客说，该团队希望通过一些改进达到 150-200 mhash。那就是效率[GPU 碰不到](https://en.bitcoin.it/wiki/Mining_hardware_comparison)。

[比特币](https://en.bitcoin.it/wiki/Mining_hardware_comparison)是一种数字货币，通过计算验证比特币交易的哈希来“挖掘”。虽然挖掘操作可以在 CPU 上执行，但在每秒可以执行多少次哈希运算方面，[显卡和 FPGAs 比 CPU](https://en.bitcoin.it/wiki/Why_a_GPU_mines_faster_than_a_CPU)快几个数量级。

该板的核心是 Spartan-6 LX150 FPGA，这是一个昂贵的套件，该团队以 440 美元的价格出售每块板。花这么多钱，你可以半价买两台 ATI 6770s，一秒钟可以处理四倍的哈希运算。然而，在不到 7 瓦的情况下，我们不会太担心冷却钻机，电力成本将非常低。