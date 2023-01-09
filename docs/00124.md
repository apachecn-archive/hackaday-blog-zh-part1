# 在 Ipaqs 上启用蓝牙耳机

> 原文：<https://hackaday.com/2005/01/02/enable-bluetooth-headsets-on-ipaqs/>

![enable bluetooth headsets on ipaqs](img/02e3ce1595dd33bd3da98f7409696e57.png)

这是一天一个黑客朋友拉斯送来的…

有一个规则。您可以编辑该键以在 ipaq 上启用蓝牙耳机。
将 1 而不是 0 放入:

HKeyLocalMchineSOFTWAREWidcommBtConfigServices 005Enabled=1

并将 DWORD Enabled=1 Enabled=1 添加到

HKeyLocalMchineSOFTWAREWidcommBtConfigServices 006

在软件 mediaplayer 中也有一个关键，它在游戏中有一些东西 unsupported=0 (off ),使它必须做一些事情，但我不知道是什么，但我想你们可以弄明白。

因此，如果你的手机有蓝牙耳机，并且有蓝牙 ipaq，那么你很有可能可以使用耳机通过耳机听音频。