# 拆除风暴蠕虫僵尸网络

> 原文：<https://hackaday.com/2009/01/16/dismantling-the-storm-worm-botnet/>

![malware](img/8ca641f492970c32a991abcfd75f396b.png "malware")

Zero Day 采访了德国研究人员，他们已经找到了摧毁风暴蠕虫僵尸网络的方法。他们的程序[Storm sucker](http://events.ccc.de/congress/2008/Fahrplan/events/3000.en.html "Owning the Storm Botnet")利用了 Storm 指挥网络的缺陷:处于 [NAT](http://en.wikipedia.org/wiki/Network_address_translation) 的节点只使用一个四字节的 [XOR](http://en.wikipedia.org/wiki/XOR_gate) 挑战。没有被 NAT 的节点只使用普通的 64 位 RSA 签名。他们的解决方案可以清除受感染的机器，还可以分发到其他节点。不幸的是，未经用户同意安装软件与恶意软件是完全相同的行为。不要期望在任何种类的广泛使用中看到它。研究人员确实指出，一些互联网服务提供商已经开始关闭受感染客户的服务，直到他们的机器被清理干净。