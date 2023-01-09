# 性爱机器人

> 原文：<https://hackaday.com/2005/03/25/sex-bots/>

请原谅，我要离开一会儿。为什么机器人，不管是设计的还是想象的，总是仅仅为了满足人类的一个目的或乐趣而存在？他们不是也有感情吗？也许是时候我们制造一些机器人了，它们的唯一目的是与其他机器人联系，变得有点怪异，并制造一些机器人后代。

在这篇文章中，我们将探索机器人的爱。我做了几个简单的乐高思维风暴机器人，并对它们进行编程，让它们繁殖——也就是说，它们可以交换代码。实际上，两个机器人走到一起，交换它们的基因组，然后死去，两个新的机器人在它们的位置上诞生。

打开巴里·怀特的音乐。摆脱你的思想风暴。我们开始吧。

 **基因组**

当我开始从事这个项目时，我必须对机器人繁殖实际上如何工作做出一些初步决定。由于他们不能创造一个新的机器人，他们的复制将不得不与我们习惯的功能有所不同。

我想要的是一种机制，能够让两个父母机器人结合他们的软件，产生两个不同的孩子机器人，取代他们的父母，展示新的和独特的行为。

我使用的机器人是简单的双轮双传感器机器人。在这些机器人中，基因组将用于确定机器人正常生命过程的行为，即:

*   机器人的主要执行循环

*   如果左侧传感器被击中，该怎么办

*   如果击中了右边的传感器，该怎么办

遗传密码决定了这三项任务中的每一项会发生什么。可能的操作可以是以下各项的任意组合:

*   前进

*   倒退

*   向左转

*   向右转

*   试图繁殖

*   什么也不做

所以一个合理的执行循环可能是:forward、mate、forward 等。

左传感器环路可能是:向后、向右、向右等。

**上** ![mating robots](img/eca369b8ab62f9c57e1def79196e6d6e.png)
三个生命过程的每一个都有固定的长度。当机器人打开时，这些被初始化为一个非常基本的例程，并且大多数可能的动作都用 noops 填充。

当机器人试图交配时，它会在红外端口发出信号。如果另一个机器人能够看到这个信号，它将开始握手，开始基因组转移。父母一次交换一个例程，用新的子程序替换他们以前的动作。

为了阻止后代变得懒惰，我增加了一个要求，即在他们变得“成熟”并能够开始交配程序之前，每次成功交配之间必须发生一定数量的运动。

 **进化**

当两个机器人繁殖时，每个机器人都会得到另一个机器人的遗传密码。每个生命例行程序的每个可能动作的结果是在两个父代码之间的随机选择。考虑到双亲都是用相同的代码初始化的，光是这一点就会导致一些非常不友好的孩子，所以我增加了大约 1%的可能性，即每个被复制的动作都会发生突变。

这个想法是，一个能够更好地四处机动而不被卡住的机器人将有更好的机会找到另一个机器人并繁衍后代。

不幸的是，我只有两个机器人可以使用，但结果仍然非常有趣。各种不同的行为突然出现，从大圈和之字形行驶的机器人，到撞到东西时总是朝同一方向行驶的机器人。

**灭绝
![robotic extinction](img/dc4d11623c3179d03b55b6db12a3feee.png)** 然而在一个小种群中，事情并不总是朝好的方向发展。上图中的一个机器人发生了变异，当传感器被击中时，它不会转动。第二个机器人设法与它交配过一次，但随后受到同样基因故障的困扰。他们无法走出困境，基本上灭绝了。

随着人口的增加，你可能会看到更少的物种灭绝和更有趣的群体行为。只有两个机器人，它们在每一代都有几乎相同的构成。

人们可以想象一个更大的群体分成不同的类别——一些机器人不太动，很容易被发现，另一些则擅长在社区中游荡和传播。

如果有人能接触到一堆思维风暴，试一试，让我们知道你的结果。

可能的应用
![fembots](img/4e084d3a7bdfee6e80a3e25ace174c99.png)
除了作为一种简单有趣的模拟生命和进化的方式(更不用说一篇文章的无耻标题)，性爱机器人还有一些有趣的潜在应用。

 **机器人优化** 当我第一次发布我的机器人时，我用来初始化它们的软件并不完全适合我放置它们的环境。偶尔，他们会被挂在角落里，或者在永远不会相交的连续圆圈中移动，这样他们就能看到彼此。

对于一个小型的初学者社区，你可以让他们在自己的环境中自由活动，让他们运行一段时间。他们会从基因上优化他们的日常生活以适应他们的环境。那些找不到彼此的生物基本上会灭绝。其余的会在保持交流的同时适应周围的环境。

自动软件更新
你也可以很容易地编码一个版本标识符。当交配时，机器人会检查它们是否来自同一个版本库。以前的版本会完全采用新版本，而相同版本的两个机器人会正常交配。想象一个需要软件升级的分布式、松散的机器人网络。简单地释放一些装有新软件的机器人，人们最终会自动转换到新版本。

毫无疑问，有许多方法可以制造一个复制机器人，而且我相信这项技术还有许多我没有想到的用途。所以去做你自己的性爱机器人，让我们知道吧！