# 如何:建立自己的点焊机

> 原文：<https://hackaday.com/2009/06/23/how-to-build-your-own-spot-welder/>

点焊机用于制造汽车、电脑机箱、电源、微波炉、电气接线盒、法拉第笼和各种电子设备。使用点焊机是因为它能产生高度明确的接触焊接点。焊接材料无需过度加热，因此工件易于操作。焊接也是高度受控和可重复的。在本指南中，我们将介绍点焊机的基础知识，然后向您展示如何用微波炉变压器制作点焊机。

点焊机的电极至少有三个功能。它们将电能传递给材料，同时也将材料结合在一起；这也控制阻力。夹紧力越大，电阻越小，这导致电阻加热减少。较小的夹紧力导致电阻加热增加。在关闭周期中，电极还将热量从材料中传导出去，帮助冷却和回火焊缝。电阻点焊通常被称为“熔核”。点焊机通常局限于黑色金属材料，这多少限制了它们的应用范围。大多数用低电压高电流焊接。本指南中的焊机使用 3 伏交流电的次级电压工作。初级电压为 120vac 线电压，应谨慎对待。低压次级使得焊机非常安全，因此电极的电击危险几乎不存在。然而，与任何焊机一样，高温也有灼伤的危险。

这种特殊的焊机不是用来焊接 1966 年吉普的车身板件的；它不适用于比 20gauge 金属板重的材料。预期用途是用于小型项目，因为它不能连续运行。可能的用途如下:用于[电解槽](http://hackaday.com/?s=hydrogen+fuel)的焊接电极材料。与真空管的精密[部件一起工作。为小型机器人平台建造轻型框架。我们大多数人都有足够的零件来制造一台点焊机。如果你身边有一个](http://hackaday.com/2008/01/07/how-to-make-a-vacuum-tube/)[微波炉变压器(MOT)](http://www.kronjaeger.com/hv/hv/src/mot/index.html) ，那么你已经成功了一半。另外，我们在 2006 年报道过一个[微波炉弧焊机](http://hackaday.com/2006/09/21/microwave-oven-arc-welder/)。

![Materials needed](img/64c1740b3678994665682c38a0ce8235.png "Materials needed")

我们还需要一些粗铜线。我们使用了大约 4 英尺的 4AWG 线来建立照片中的点焊机。其他材料包括 2×6、2×2 的废料、两个铜螺丝型接线片、两个铜焊接电缆接线片、两个 MIG 焊接头、两个 4″ x 3/4″镀锌角撑、干墙螺钉和三个垫圈。

![MOT](img/36746a09540dfba742adcca09fac909a.png "MOT")

上图是一个工作 MOT。我们要做的第一件事是移除次级线圈。即高压绕组和低压绕组。我们使用带切割轮的角向磨光机，同时小心不要切割初级绕组。

![Removing secondary](img/50d682ce7477738cdce8f9d6553113b1.png "Removing secondary")

我们用 MOT [叠片铁芯](http://wiki.answers.com/Q/What_is_the_purpose_of_laminating_an_iron_core_in_transformers)切割第二平面。MOT 的两边都应该剪。检查 MOT 是否有层压板被焊接的迹象。我们发现，焊接 mot 比仅密封的配对零件能处理更多的滥用情况。如果可能的话，尽量保持铁芯绝缘完好无损，因为二次绕组将在此处缠绕。虽然它不是一个节目停止，如果绝缘损坏。绝缘使得包裹大规格次级线圈稍微容易一些。

![Removed secondary](img/310c1928ff7b5e89ed32c7ea4f5f9bda.png "Removed secondary")

移除第二个之后，我们有了类似上面这张照片的东西。如果磁分流材料脱落，请务必按原样更换。分流器防止核心将过多的能量转移到次级。如果你愿意，可以称之为磁性镇流器。分流用来控制磁芯的饱和。像这样的强力项目依赖于这样的分流正常运作。

![Winding the secondary](img/1e60a357ffc7f94bd0fd3cf047e799b0.png "Winding the secondary")

用 4AWG 倒带一个 MOT 可不是在公园里散步。如果你已经损坏了核心绝缘体，我们建议在它们的位置缠绕一层绝缘带。这将有助于避免在电线穿过线芯时损坏其绝缘层。我们的经验是 3-4 圈就足够了。毕竟这个点焊机靠的是大电流和边际电阻。不是高电压。

![Helical winding](img/954308f2491deb539ea3550d0a1a7aba.png "Helical winding")

我们小心翼翼地确保次级[线圈以螺旋](http://en.wikipedia.org/wiki/Helix)方式缠绕，以完成次级。

![Mount the MOT and 2x2 on 2x6 base](img/01e10c57f5fd373ff45a66f70b4b6109.png "Mount the MOT and 2x2 on 2x6 base")

我们将 MOT 和 2×2 安装到 2×6 底座上。这个特殊的构建使用了 12 英寸 2×6 英寸和两个 7 英寸 2×2 英寸。这些尺寸可能有效，也可能无效，这取决于 MOT 的物理尺寸。这里唯一关键的部分是保持电线长度尽可能短。

![Attch the upper jaw](img/67aad68c49be04bbd5573fe655756981.png "Attch the upper jaw")

下颌装好后，我们也装上了角撑。结果发现，一块 2×2 的备用垫片可以很好地对齐上下颌骨。上颌对齐后，我们用螺丝把它固定在角撑上。这形成了颚的铰链部分。

![Assemble electrode](img/0e304b0c5a5f7ad86afb0c4625d5ae17.png "Assemble electrode")

上图显示的是 MIG 焊机的焊嘴和螺旋式铜焊片。这是对我们早期模型的改进。最初，我们使用带孔的铜管和一根 6AWG 接地线作为焊接电极。接地线由一个垂直于电极拧入铜管的螺钉固定。虽然很粗糙，但是很有效。这种新方法更实用。

![Assembled electrodes](img/c9615598dd2862d0cb3cd042cdf1d6a9.png "Assembled electrodes")

这是两个准备固定在上下颌骨上的电极。我们仔细检查了 MIG 电极，以确保它们是紧密的。松动的连接会带走[焊接熔核](http://www.naun.org/journals/mechanics/m-20.pdf)的热量。

![Align electrodes with jaws](img/e7cc24f8389c1a3d3c3fcc98704db618.png "Align electrodes with jaws")

均匀地对齐焊接电极，我们小心地将上颚保持在安装的自然位置。这为焊接电极保持了平坦的接触区域。在我们确定电极已经正确对齐后，就在钳口上做了标记。然后我们钻了一个小洞。因为我们安装了 2×2 的纹理，所以这些孔有助于防止 2×2 的纹理裂开。

![Attach electrodes to jaws](img/a40d4fe3667ada736c52fed5242e0c57.png "Attach electrodes to jaws")

安装好电极后，我们将电线剪成合适的长度。我们从来没有削减我们需要的确切数量。我们总是削减超过我们需要的。这条经验法则应该适用于所有的电线。毕竟，切掉多余的部分比包装一个新的次级线圈要容易得多。

![Prepare wires for crimp lugs](img/011d6c3b97adeaa5a19022a329f8e2e5.png "Prepare wires for crimp lugs")

我们将电线弯曲到它们将要组装的大致位置，并剥去电线，为卷曲型焊片做准备。这是一个好主意，剥离超过这里所需要的。在估算凸耳深度后，只需切除多余部分。切勿用接线片压接绝缘层。由于传导损失，这将产生一个潜在的问题区域。

![Wires with crimped lugs](img/642ba2b075825152dfe306e225dfe606.png "Wires with crimped lugs")

使用良好的非绝缘压接工具固定导线。我们检查了卷边，并进行了拉伸试验。只要拉一下线，如果线松了，它就会被拉出来。如果不能拔出，则说明已经形成了适用于高电流的足够的压接。

![Align electrodes](img/700587c50ef7a8d64864d8cbc471b1d8.png "Align electrodes")

用螺钉将卷曲的电线连接到焊接电极上。我们小心翼翼，不要把螺丝拧得太紧。如果干墙螺丝从木头上脱落，我们就必须用一个更大的木螺丝来代替它。在两个焊接电极都固定在夹钳上后，我们将电极对齐。我们用钳子弯曲电极，使它们均匀地相互接触。电极应该已经相当接近，因为它们在钻孔之前已经对齐。

![Test secondary voltage](img/78224805b0c6ad79baea4586fa99b9a8.png "Test secondary voltage")

我们打开钳口，将初级线圈连接到电线上，然后测试次级线圈。如果断路器跳闸，检查以下情况:

1.  次级短路(钳夹闭合)
2.  磁分路丢失或没有正确安装
3.  初级线路接线故障或初级短路
4.  测试电路负载过大或断路器尺寸过小

我们遵守了正确的电线惯例。还需要强调的是，这是一台焊机，它应该像任何其他焊机一样有一个专用电路。

![Check electrode and material alignment](img/3748c9b51582302b09b47d9cb2ccd327.png "Check electrode and material alignment")

在电源物理断开的情况下，我们验证了焊接电极与我们打算加工的材料的对准。在连接电源和进行初始焊接之前，我们遵守了一些安全准则。这是一台焊机，会产生很高的温度。让手指远离焊接电极。搬运前让材料冷却。请始终佩戴护目镜。您可能有兴趣阅读关于[点焊机参数](http://www.robot-welding.com/Welding_parameters.htm)的内容。还有可燃材料的问题…

![Compaq screen support frame](img/7c713701c9d672730d1c79a8da4f9f3d.png "Compaq screen support frame")

这款康柏电脑使用非常薄的铝来支撑屏幕和连接铰链。金属断裂并毁坏了大部分下层塑料。我们能够用 22AWG 不锈钢金属板制造新的支架。所有的焊接都是用带有特殊电源控制器的点焊机完成的。电源控制器将在另一篇操作指南中介绍。

[https://www.youtube.com/embed/VG1xVNpm7k8?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/VG1xVNpm7k8?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)