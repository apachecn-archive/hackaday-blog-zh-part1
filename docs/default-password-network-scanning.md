# 默认密码网络扫描

> 原文：<https://hackaday.com/2008/10/13/default-password-network-scanning/>

![](img/8a9328bea774429632bb4aac55b0b082.png "trinity")

午夜研究实验室刚刚发布了一个新工具。Depant 将扫描您的网络并检查服务是否使用默认密码。它通过执行 [Nmap](http://nmap.org/) 扫描来发现网络上可用的服务。它根据响应速度来组织这些服务。使用 [Hydra](http://freeworld.thc.org/thc-hydra/) 它使用[默认密码列表](http://www.phenoelit-us.org/dpl/dpl.html)对这些服务进行强力密码检查。用户可以提供第一阶段的备选清单或后续检查中使用的附加清单。Depant 有许多不同的选项来配置您的扫描，当然会帮助您找到网络上有人未能安全设置的流氓硬件。