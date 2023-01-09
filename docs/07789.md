# 芯片套件草图:迷你复音采样合成器

> 原文：<https://hackaday.com/2011/06/08/chipkit-sketch-mini-polyphonic-sampling-synth/>

![](img/11a590b5ef6646f141e10b479d52a57d.png "chipkit-synth-title")

在我们对 Digilent chipKIT Uno32 的动手评测中，我们提出了一个问题，即 32 位 Arduino 仿制品的持久吸引力可能是什么。我们觉得它需要一些新颖的应用来开发它的特殊功能……而不仅仅是带有 MOAR 比特的旧 Arduino 草图。在分形演示之后，我们发现了一些独特而有趣的东西…

那么，与普通的 Arduino 相比，chipKIT 有什么独特之处呢？在今年夏天预计的以太网盾发布之前，一些想法被搁置了。让我们看看……不缺少 MIPS，当然……但是也有大量的 RAM 和闪存。对于后者，我想到了采样音频。有适合这种事情的 Arduino shields——[Adafruit Wave Shield 出现在许多项目中,](http://hackaday.com/?s=%22wave+shield%22),使用 SD 卡存储声音——但是如果一个人的需求不大，chipKIT 的 PIC32 完全能够在自己的 flash 程序空间中存储简短的音频样本，不需要卡、适配器或额外的费用。我们估计 Max32 可以容纳将近一分钟的语音质量的音频。

考虑到这个想法，我们发现我们可以做得更好。实际上，好几个。像 Wave Shield 这样基于 SD 卡的播放器的一个局限性是，它们一次只能播放一种声音。处理 FAT 文件系统和缓冲卡上的音频数据几乎需要 Arduino 的小 ATmega 芯片所能召集的一切…复调声音需要[组装](http://hackaday.com/2011/02/27/layering-pinball-audio-using-parallel-wav-shields/)。但我们芯片套件中的 flash 音频样本很难获取。凭借快速的 32 位 CPU，可以同时处理许多样本…然后，借助大量 RAM，可以添加基于时间的效果，如混响。在我们意识到之前，桌子上放着一个玩具合成器:

![](img/7dba0969895b4a919054e29992c22bac.png "overview")

之前使用 Microchip 的工具尝试过 PIC32，我们对它的简单性感到惊讶。除了一些早期的粗糙点，chipKIT 和 MPIDE 环境显示了像 Arduino 一样简单的主要前景。事实上，整个构建比文档阶段完成得更快。然后第二个惊喜，甚至对我们来说:除了 chipKIT 板本身，零件列表中的一切都是常见的东西，可以在 [RadioShack](http://hackaday.com/2011/05/27/speak-your-mind-and-help-radioshack-suck-less/) 找到。没有时髦的特殊集成电路，组件或邮购盾牌。多亏了这个快速的微控制器，大部分的“魔力”都在软件中。

这是一个完成的迷你合成器的演示:

[https://www.youtube.com/embed/hdpQ8LEku90?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/hdpQ8LEku90?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

请原谅这位示威者缺乏节奏感和协调性。这就是为什么专业音乐家拿着数百万的薪水，而业余爱好者作为科技博客写手却过着悲惨的生活。感谢我们让你免于一场闹剧。

输入通过五个[压电](http://hackaday.com/2010/10/01/disco-drumming-with-piezo-sensitive-lighting/)传感器(RadioShack #273-0073，每个 2.19 美元)连接到模拟输入 A0 到 A4。当然，我们可以只使用按钮，但我们需要能够感知每次点击压力的东西，这些东西比力敏电阻便宜。压电传感器有特定的极性，正极(红线)应连接到模拟输入，黑色连接到地。每个元件上还增加了一个 2000 欧姆的电阻:

![](img/7add65e526fadf86854b037018da8bda.png "schem-pads")

混响效果的输入很简单。模拟输入 A6 和 A7 上的两个 10K 电位计(它们位于 chipKIT Uno32 上模拟输入的第二行，Arduino 上没有)。一个控制幅度，另一个控制延迟:

![](img/8942c117418a059d76b25f660e1a4d48.png "schem-pots")

最后，声音输出使用数字引脚 3 上的高速 PWM 输出，通过简单的低通滤波器到达耳机插孔:

![](img/e40e6412778cf7ba0db837bf04265c89.png "schem-filter")

在我们的试验板上，我们使用了 SparkFun 的一个方便的小[耳机转接板](http://www.sparkfun.com/products/10588)，但人们可以将适当的导线焊接到“The Shack”的一个裸露插孔上(唉)。你可以选择在耳机插孔前增加一个 1 兆的罐子。该电路与耳机或放大的 iPod 扬声器一起工作良好，但当直接馈送时，我们的相机的麦克风输入完全饱和。

本演示使用 16 KHz 声音样本。根据[奈奎斯特理论](http://en.wikipedia.org/wiki/Nyquist_rate)，低通滤波器设计为 8 KHz (-ish)截止频率。对于纯语音应用，这些速率的一半就足够了(节省闪存空间并允许更长的采样)，两个电阻值应加倍。

零件就这些了。你能相信吗？关于代码…

首先，我们需要能够将声音文件转换成 C 编译器可以使用的格式的东西。一个丑陋的小 UNIX 命令行实用程序将 WAV 文件从一种非常特殊的格式(8 位单声道，未压缩)转换成 C 头文件，可以#包含在 MPIDE 项目中。Arduino 通常会使用 PROGMEM 指令将这些表放入代码闪存空间，但这里并不要求这样做。令人惊讶的是，备受喜爱的 [Audacity](http://hackaday.com/2011/02/13/modern-freaking-pull-phone-numbers-from-youtube-audio/) 程序无法导出 8 位 wav，但我们发现可以使用 iTunes 批量转换声音。

```

const signed char sample_drum[] = {
        0x02,0x03,0x01,0x00,0x00,0x00,0x00,0x01,
        0x01,0x01,0x01,0x01,0x01,0x01,0x01,0x00,
        ...HUNDREDS OF LINES OF STUFF...
        0xff,0xff,0xff,0xfd,0xfd,0xff,0x00,0x00,
        0x00,0x00,0x00,0x00,0x02,0x00 };

```

我们将让您不必害怕查看代码或进行转换。您可以[在这里](http://www.paintyourdragon.com/Synth.zip)下载完整的项目文件集，然后根据您自己的需要进行调整。本文的剩余部分只讨论 MPIDE 代码。

但是首先，需要一个修正:在我们的[前一篇文章](http://hackaday.com/2011/05/27/chipkit-uno32-first-impressions-and-benchmarks/)中，我们遇到了芯片套件的模拟读取速度的问题，并在评论中讨论了一个修正。这包括在 MPIDE 源文件中查找“wiring_analog.c ”,并更改几行代码。旧代码类似于:

```

delayMicroseconds(99);
while ( ! mAD1GetIntFlag() ) { }
analogValue = ReadADC10(0);
mAD1ClearIntFlag();

```

这应改为:

```

delayMicroseconds(2);
mAD1ClearIntFlag();
while ( ! mAD1GetIntFlag() ) { }
analogValue = ReadADC10(0);

```

我们被告知这一变化将被纳入到工具包的后续版本中，这将不再是必要的。如果你只是从这个项目中翻出数字音频代码，而忽略鼓垫的东西，你可以完全跳过这个变化。

然后是我们的草图代码:

```

// Mini sampling synthesizer for chipKIT Uno32.

#include &quot;sounds.h&quot;       // N_SAMPLES and data are here
#define PWM_PIN         3 // OC1 PWM output - don't change
#define SAMPLE_RATE 16000 // All samples fixed at 16 KHz
#define MAX_SOUNDS     10 // Polyphonic limit
#define MAX_ECHO     4000 // 1/4 sec fits in Uno32 RAM

short
  echo_data[MAX_ECHO]; // Circular buffer for echo

int
  echo_delay = 0, // Duration of echo effect
  echo_vol   = 0, // Echo effect volume (0-1023)
  echo_pos   = 0; // Current position in echo buffer
volatile int      // May change during interrupt:
  n_sounds   = 0; // Number of sounds currently playing

struct soundStruct {
  int sample; // Index of corresponding audio sample
  int pos;    // Current position within sample
  int vol;    // Playback volume, 0-1023
} sound[MAX_SOUNDS];

#define N_PADS N_SAMPLES // One pad for each sample

struct padStruct {
  short max;       // Max pressure during press (0-1023)
  short count;     // Timer for filtering out noise
  byte  triggered; // If set, currently reading a press
  short add;       // If &gt;0, begin sound at next interrupt
} pad[N_PADS];

void setup()
{
  memset(pad, 0, sizeof(pad));    // Clear drum pad data
  memset(echo_data, 0, sizeof(echo_data)); // Clear echo
  pinMode(PWM_PIN, OUTPUT);     // Enable PWM output pin

  // Open Timer2, 1:1 w/256 tick interval (for 8-bit PWM)
  OpenTimer2(T2_ON | T2_PS_1_1,256);
  OpenOC1(OC_ON | OC_TIMER2_SRC | OC_PWM_FAULT_PIN_DISABLE,
    0,0);

  // Open Timer1 with interrupt for sample mixer (16 KHz)
  ConfigIntTimer1(T1_INT_ON | T1_INT_PRIOR_3);
  OpenTimer1(T1_ON | T1_PS_1_1, F_CPU / SAMPLE_RATE);

  delay(1);  // Slight delay avoids false trigger at start.
}

// Piezo transducers as input pads are fussy.
// To avoid false positives, a bit of hysteresis is used:
#define PRESS_MIN     20 // Must read at least this force
#define PRESS_COUNT    3 // for this many samples, then...
#define RELEASE_MAX    8 // Must read less than this force
#define RELEASE_COUNT 15 // for this many samples.
// Still imperfect; there are occasional double-triggerings
// and false triggers on adjacent pads.  Could be addressed
// with better mounting and isolation of pads and/or with
// improved input filtering in code or in hardware.

// The loop() function just reads pad and dial inputs; all
// audio work is done in the subsequent interrupt function.

void loop()
{
  int i, a;

  for(i = 0; i &lt; N_PADS; i++) {  // Sample each pad...
    a = analogRead(i);

    if(pad[i].triggered) {    // Previously pressed?
      if(a &lt;= RELEASE_MAX) {  // Yes, released now?
        if(++pad[i].count &gt;= RELEASE_COUNT) {  // Really?
          // Sounds aren't added to play list here, just
          // flagged; they're added to the mix in the
          // interrupt.  This avoids a race condition
          // where this code may be trying to add a sound
          // while the interrupt is removing one.
          pad[i].add       = pad[i].max;
          pad[i].triggered = 0;
          pad[i].count     = 0;
        }
      } else {  // Still pressed...watch for new max
        if(a &gt; pad[i].max) pad[i].max = a;
        pad[i].count = 0;  // Reset release counter
      }
    } else if(a &gt;= PRESS_MIN) {  // Untriggered; new press?
      if(++pad[i].count &gt;= PRESS_COUNT) {  // Really?
        pad[i].triggered = 1; // Flag to watch for release
        pad[i].count     = 0;
        pad[i].max       = a;
      }
    } else {  // Untriggered and below press threshold
      pad[i].count = 0;  // Clear press counter
    }
  }

  // Echo parameters come from potentiometers on A6 and A7
  echo_vol   = analogRead(6);
  echo_delay = map(analogRead(7), 0, 1023, 0, MAX_ECHO);
}

// This is the mixing/sample-playing interrupt,
// invoked at 16 KHz to match the audio sample rate.
// With guidance from Mark Sproul's PIC32 port of
// Brett Hagman's Tone library for Arduino.
extern &quot;C&quot;
{

void __ISR(_TIMER_1_VECTOR,ipl3) playSample(void)
{
  int i = 0, sum = 0;

  mT1ClearIntFlag();  // Clear interrupt flag

  while(i &lt; n_sounds) {  // For each sound playing...
    // Waveform is cumulative, NOT averaged
    sum += (int)sample[sound[i].sample].data[sound[i].pos] *
      sound[i].vol;
    sound[i].pos++;  // Advance counter.  If end hit...
    if(sound[i].pos &gt;= sample[sound[i].sample].size) {
      n_sounds--;  // Decrement number of sounds playing:
      // Move sound at end of list to the slot currently
      // occupied by the vacating sound (unless the same)
      if(i &lt; n_sounds) {
        memcpy(&amp;sound[i], &amp;sound[n_sounds],
          sizeof(soundStruct));
        continue;  // Sound moved; dont advance index
      }
    }
    i++;
  }
  sum /= 1024;

  // Add in echo effect (if enabled) from circular buffer.
  // This takes place before audio level clipping so that
  // any clipping distortion won't be repeated in echo.
  if((echo_delay &gt; 0) &amp;&amp; (echo_vol &gt; 0)) {
    sum += echo_data[echo_pos] * (echo_vol + 1) / 1024;
    echo_data[echo_pos] = sum;
    if(++echo_pos &gt;= echo_delay) echo_pos = 0;
  }

  // Clip audio to 8-bit range.  This may cause distortion
  // when multiple sounds or echo exceed the 8-bit range.
  // Invoking the &quot;quick &amp; dirty&quot; alibi again.
  if(sum &lt; -128)     sum = -128;
  else if(sum &gt; 127) sum =  127;

  SetDCOC1PWM(sum + 128);  // Set PWM output value 0-255

  // Check for any new sounds flagged by loop().
  // Done last because sounds finished above will
  // free up polyphonic slots.
  for(i = 0; i &lt; N_PADS; i++) {
    if(pad[i].add) {
      if(n_sounds &lt; MAX_SOUNDS) {
        sound[n_sounds].sample = i;
        sound[n_sounds].pos    = 0;
        sound[n_sounds].vol    = pad[i].add + 1;
        n_sounds++;
      }
      pad[i].add = 0;  // Clear flag even if not added
    }
  }
}

} // end extern &quot;C&quot;

```

## 解释:

函数的作用是:初始化两个定时器:

*   定时器 2 和输出比较 PIC32 芯片的硬件特性)用于脉宽调制( [PWM](http://hackaday.com/2011/05/14/optimizing-code-for-pwm-efficiency/) )。结合前面描述的滤波器，这将为每个音频样本定位扬声器(谷歌“PWM DAC”的解释和示例)。PWM 输入时钟设置为芯片的全速 80 MHz，间隔为 256“滴答”(8 位分辨率)，产生 312，500 Hz 的 PWM 波形。对于这种 DAC 滤波，建议 PWM 频率至少是采样速率的 10 倍，这样就足够满足我们的需求了。这也是代码绕过用于 PWM 的原生 Arduino analogWrite()函数的原因，该函数的工作时钟要慢得多。最后，使用输出比较 1 指示我们*必须*使用数字引脚 3 进行音频输出；这是该芯片上五条原生硬件 PWM 线路之一。
*   定时器 1 以我们的音频采样频率(16 KHz)运行，并附带了一个[中断](http://hackaday.com/2010/09/27/beginner-concepts-all-about-avr-interrupts/)功能。该功能混合音频样本，并改变定时器 2/OC1 的 PWM 占空比。这两个定时器的速率只需设置一次，无需更改，只需改变一个占空比。

这一段代码(以及中断函数中的一行代码)不可否认地不太像 Arduino，以不可移植的方式直接访问硬件特性。更正式的实现是将这些细节抽象成一个库，程序员新手只需将数据传递给这个库即可。但是为了一个简单的单文件演示，它就在那里，毫无保留。在许多方面，这只是一个工作的起点。

loop()函数读取压电传感器的状态，并标记要播放的声音(稍后由中断接收)。压电输入有一些粗糙的[去抖](http://hackaday.com/2010/11/09/debounce-code-one-post-to-rule-them-all/)…这真的可以使用一些更复杂的滤波(PIC32 可以轻松处理)，但为了简洁起见，它被跳过。该代码通常检测不同的压力，但仍有相当多的错误触发。在这个函数中，混响控制也被读取:只有两个 analogRead()调用，第二个调用映射到混响缓冲区的全长。

中断处理程序是所有有趣的事情发生的地方，它出奇的简单。

extern“C”声明使 C++编译器对中断函数声明感到满意。

该程序设计用于多达 10 个并发声音，其细节保存在“声音”结构数组中(对于更大的复音来说，CPU 性能绰绰有余，但主要是输入板对此不太实用)。当检测到键盘点击时，一个新的项目被添加到这个数组中(直到最大值)。结构元素指示用于此声音的音频样本、样本中的当前回放位置以及音量。

音频样本存储为有符号值(而不是无符号值)，因为这使它们更容易混合(只是相加)和更容易调整增益(只是相乘)。利用一切机会使用定点数学。从之前的分形演示中，我们看到了这可以带来多么巨大的性能差异——有时是几个数量级。我们的大部分模拟读数(以从 0 到 1023 的 10 位整数返回)对应于 0.0 到 1.0(或 0%到 100%)的增益(相对音量)值。要以定点单位执行这种缩放，读数加 1，执行乘法(PIC32 上的一条指令)，然后除以 1024(一个简单的移位操作，也是一条指令)。与转换成浮点相比，精度没有损失；无论如何，源值和目标值都将被量化。

```

// Floating-point, slow:
// scale = float 0.0 to 1.0
out = (int)((float)in * scale);

// Fixed-point, crazy fast:
// scale = integer 0 to 1023
out = in * (scale + 1) / 1024;

```

请注意，在对音频样本求和时，会跳过这一部分，直到结束。这样可以节省一些周期，结果也是一样的。从代数上讲，(A/X)+(B/X)=(A+B)/X，以此类推。临时的 32 位总和不太可能溢出。

应用混响时，定点数学再次发生。整数变量 echo_vol(也是 10 位，来自模拟旋钮之一)中的回声音量在 0 到 1023 的范围内，对应于 0%(无混响)到 100%(回声与原声一样大)。混响(在 echo_data[]数组中)是一个循环缓冲区，当声音播放时，这里的内容(由 echo_vol 缩放)首先被添加到输出中，然后结果被放回数组中的相同位置，并且位置计数器递增 1。当到达数组的末尾(或者由 echo_delay 指示的更短的限制)时，我们“绕回”到开头。

最终产生的音频值被限幅到 8 位范围。当同时使用许多响亮的声音时，这可能会引入削波失真。再次为了简洁起见，省略了铃铛和哨子，但是勇敢的程序员可以选择在这里添加“软剪辑”来限制这种失真。有充足的 CPU 能力。

最终的 8 位有符号值随后被转置到无符号范围，并馈入 PWM 输出的 OC1 占空比。

最后，中断检查 loop()函数标记为“命中”的任何声音，并将这些声音添加到并发播放列表中。这种标记并添加的行为，而不是直接在 loop()中添加项目，避免了潜在的令人讨厌的竞争情况，即 loop()可能正在添加声音，而中断正在删除其他声音，从而引发计数器。

这就是全部了。这个演示只使用了 Uno32 上大约四分之一的存储，而 uno 32 本身的容量只有 Max32 的四分之一…我们还没有利用任何类型的[压缩](http://hackaday.com/2010/09/23/codec2-gnu-low-bitrate-speech-codec/)。这里可能会有一些有趣的应用，可能会给厕所添加[更好的超级马里奥声音](http://hackaday.com/2011/06/06/retro-video-games-sounds-for-your-toilet/)，或者给其他 chipKIT 项目添加语音提示(“你的门半开”)。你认为这里还会出现什么其他想法？