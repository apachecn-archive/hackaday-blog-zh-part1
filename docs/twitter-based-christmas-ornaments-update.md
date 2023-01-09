# 基于 Twitter 的圣诞饰品更新

> 原文：<https://hackaday.com/2009/12/31/twitter-based-christmas-ornaments-update/>

![](img/532338551d4502712169bd6e0be07ec7.png "4")

当我们向你介绍 Twitter 圣诞树装饰品时，很遗憾我们对这个项目知之甚少。幸运的是[Rob]联系上了我们，并向我们提供了内部运作的线索。事实证明，我们对 Arduinos 的使用是错误的！我们邀请你在休息之后检查所有有趣的内部工作。
 让我们直接进入解释，

> 因此，控制器使用单个 Arduino 连接到 3 个 74HCT595 移位寄存器。’595 采用一个时钟位和一个数据位，并且时钟位的每个前沿(0-1 转换)移入一个数据位。然后是一个 8-bot 锁存器，另一条线的前沿将移位寄存器的状态捕捉到输出。每个' 595 存储 8 位，可以链接，有三个。这使得它只需 3 条 I/O 线就能控制 24 盏灯。在标准 NPN 配置中，每个输出连接到 TIP31 晶体管。TIP31 最高可切换至 3A，因此可以轻松处理 1A 6V 灯。这非常接近我们正在使用的原理图，除了只有 24 个输出:
> 
> [![](img/b7aa39ecd516f24cfd846d60506741bc.png "y7875786")](http://hackaday.com/files/2009/12/y7875786.png)
> 
> 这是我用来控制移位寄存器的草图:
> 
> ```
> long count;
> 
> unsigned long val;
> 
> void setup()
> 
> {
> 
>   Serial.begin(9600);
> 
>   pinMode(10, OUTPUT);
> 
>   pinMode(11, OUTPUT);
> 
>   pinMode(12, OUTPUT);
> 
>   pinMode(13, OUTPUT);
> 
>   digitalWrite(10, HIGH);
> 
>   digitalWrite(11, LOW);
> 
>   digitalWrite(12, LOW);
> 
>   digitalWrite(13, LOW);
> 
> 
> 
>   count = 0x00;
> 
>   val = 0;
> 
> }
> 
> 
> 
> void loop()
> 
> {
> 
>   unsigned long i;
> 
> 
> 
>   if (Serial.available())
> 
>   {
> 
>     char c = Serial.read();
> 
>     if (c >= '0' && c <= '9') {
> 
>       val = val * 10 + (c - '0');
> 
>       Serial.print(c);
> 
>     } else if (c == '\n')
> 
>     {
> 
>       Serial.print("setting count to ");
> 
>       Serial.println(val);
> 
>       count = val;
> 
>       val = 0;
> 
>     }
> 
>   }
> 
> 
> 
>   unsigned long bv;
> 
>   digitalWrite(10, LOW);
> 
>   for (i=0, bv=1; i < 24; ++i, bv <<= 1)
> 
>   {
> 
>     byte bitval = LOW;
> 
>     if (count & bv)
> 
>       bitval = HIGH;
> 
>     //Serial.print("i ");
> 
>     //Serial.print(i);
> 
>     //Serial.print(" bit ");
> 
>     //Serial.println((int)bitval);
> 
> 
> 
>     digitalWrite(11, bitval);
> 
>     digitalWrite(13, HIGH);
> 
>     delayMicroseconds(50);
> 
>     digitalWrite(13, LOW);
> 
> 
> 
>     delayMicroseconds(50);
> 
>   }
> 
>   digitalWrite(10, HIGH);
> 
> 
> 
>     delay(10);
> 
>     //++count;
> 
>     //count &= 0x3ff;
> 
> }
> ```
> 
> 我修改了 SPI 协议，因为我在使用硬件 SPI 时遇到了麻烦，并认为这比摆弄寄存器要容易得多。我后来发现试验板有点不稳定，降低比特率可能也有用，但那是针对 V2.0 的:-)它监听串行端口上的一个数字，并将该数字转移到 74595 中。
> 
> 另一面是一个旧的上网本，运行一个处理草图——由于我没有写它，并且忘记了请求许可，所以我不能附加它，但本质是一个循环，它对 Twitter 的搜索 API 进行屏幕抓取，并将 long 的位设置为与它找到的单词相对应。我现在正在更新它，根据一个单词出现的频率来更快或更慢地闪烁，因为像圣诞节这样的词似乎在一年中的这个时候经常出现，谁知道呢？
> 
> 抢劫 D

这就是了。对于那些好奇的人来说，这个示意图实际上是为即将到来的光控盾[Rob]工作的。你可以期待在四月左右得到你自己的。对于那些不能满足阿尔法一号实验室需求的人，请务必在美国东部时间今晚 7 点参加[的常规 UStream](http://www.ustream.tv/channel/alpha-one-labs-alphaonelabs) 。