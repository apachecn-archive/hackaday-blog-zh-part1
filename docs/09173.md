# 厨房窍门:改进浓缩咖啡机

> 原文：<https://hackaday.com/2011/11/27/kitchen-hacks-improving-an-espresso-machine/>

[卡梅伦]的浓缩咖啡机中的热传感器工作不太好。他在提取浓缩咖啡时看到了一些非常疯狂的温度变化，当锅炉就放在那里时，加热器元件会将水加热到最大，然后关闭一段时间。由于从控制理论的角度来看，这是一个相当低的门槛，[卡梅伦]决定对他的咖啡机进行 [PID 改造](http://cameroncharles.blogspot.com/2011/11/saeco-aroma-pid-makeover.html)。

[Cameron]决定推出他自己的基于 ATMega328 微控制器的 Arduino 衍生产品，而不是像我们在少数[厨房黑客](http://hackaday.com/2011/11/23/kitchen-hacks-home-made-meat-smoker/)上看到的那样使用商业 PID 控制器。新设计的电路板读取“蒸汽”按钮的状态，几个控制加热器和泵的继电器，当然还有一个液晶显示器。

[卡梅伦]仍然需要做一点调整，让他的 PID 算法下来，但新的控制板已经比旧的恒温器保持更稳定的温度。花哨的新边框和液晶显示屏为他的咖啡机增添了许多技术含量。