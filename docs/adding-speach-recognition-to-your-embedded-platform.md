# 将语音识别添加到您的嵌入式平台。

> 原文：<https://hackaday.com/2010/07/11/adding-speach-recognition-to-your-embedded-platform/>

[https://www.youtube.com/embed/OEUeJb6Pwt4?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/OEUeJb6Pwt4?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)

上周，我们发布了一个关于如何在初级水平配置语音识别的故事。一些评论者表达了对嵌入式设备语音识别的兴趣。[Nickolay Shmyrev]自愿为那些人写一些说明。在本文中，[Nickolay]将带您了解使用 [CMUsphinx](http://cmusphinx.sourceforge.net/) 语音识别开源工具包设置嵌入式设备的基础知识。他用 C 和 python 给出了编程示例。虽然我们主持这个，我们还没有设置和尝试它，所以请直接在评论中对[Nickolay]有任何问题。
 这里我们将考虑如何使用 CMUSphinx 项目的
[Pocketsphinx 库实现语音识别功能](http://cmusphinx.sourceforge.net)

使用 Pocketsphinx 的优点是:

*   Pocketsphinx 是资源高效的。它可以完美地运行在嵌入式平台上。虽然不限于此，但是您可以在您的桌面/服务器上使用 pocketsphinx。Pocketsphinxvhas 只支持定点算法，因此可以在没有 FPU 的情况下运行。它还针对一些流行的平台进行了优化:Blackfin、Maemo、IPhone。
*   Pocketsphinx 支持许多现成的语言。它支持美国英语，中文，法语，俄语，德语，荷兰语等，而不需要培训什么。
*   Pocketsphinx 是完全免费的软件。
*   提供了几种编程语言的可用绑定。

所以 Pocketsphinx 真的是你语音识别库的最佳选择。

在你开始编程语音界面之前，有几件事你需要知道

*   语音识别器要求你指定他们将理解的单词(所谓的语法)，除了指定的语言，他们不会理解任何其他东西。
*   语音本质上是不准确的，你需要把它放在语音界面设计的角落里。识别器返回识别文本的置信度值。确保使用这个置信度值来拒绝不可靠的结果。如果识别器没有信心，尝试再次输入文本，询问附加信息，确认用户意图。
*   语音识别库的任务不是进行声音输入。音频接口通常是特定于设备的。您需要在应用程序中录制音频，并将其转换为特殊格式——PCM、单声道、8kHz、16 位。再次确认。如果你有 mp3，转换一下。如果您有 44.1kHz 的音频，请对其进行下采样。

让我们从简单的测试开始。一旦安装了 Pocketsphinx，只需不带任何参数运行 Pocketsphinx_continuous
即可。等到

准备好了…

会出现在终端上然后说些什么。Pocketsphinx 将从您的麦克风记录音频并输出识别结果。

000000001:你好(-11998485)

你没能让它识别你好？别担心，有些人发现产生识别结果的是命运之手。算你运气好。

现在让我们尝试学习如何指定语法，Pocketsphinx 将识别的语言。使用以 [JSGF 格式](http://java.sun.com/products/java-media/speech/forDevelopers/JSGF/)编写的语法文件来完成。

这是相当简单的人类可读的文本格式，也许最好从示例开始:

# JSGF V1.0
语法 goforward
公共<移动> =前进<方向> <距离>【米|米】；
<方向> =向前|向后；
<距离> =(一|二|三|四|五|六|七|八|九|十|二十)+；

你可以看到它可以指定替代，重复和跳过。JSGF 基本上描述了识别器的有限状态自动化。你的语法越严格，识别的准确性就越好。但是不要忘记在真正的语法中包括所有那些填充符
和错误的开始。用户不会对设备说

"意大利香肠披萨"

他们会说

“我想要，让我想想……三个意大利香肠比萨饼，不……洋葱比萨饼”

你的语法应该涵盖这一点。一旦你创建了你的语法，将其存储为
grammar.jsgf。另外，以 8khz 单声道录制音频文件，并将其命名为“myrecording.wav”。

现在，让我们做一些编程。为了演示如何创建语音识别应用程序，让我们首先尝试将 Pocketsphinx 与 Python 结合使用。Python API 非常简单，示例只有 6 行代码。要识别语音，你需要完成三个步骤，它们是:

#!/usr/bin/python

#第一步，初始化
导入 pocketsphinx 为 ps
解码器= ps。解码器(jsgf = '/path/to/your/jsgf/grammar . jsgf '，samp rate = ' 8000 ')
#第二步，打开音频文件。
fh = open("myrecording.wav "，" Rb ")
nsamp = decoder . decode _ raw(FH)
#第三步，获取结果
hyp，uttid，score = decoder . get _ hyp()
print " Got result % s % d " %(hyp，score)

现在，让我们用 c 做同样的事情。它与 python 并没有真正的不同，只是更适合你的设备。

#包括

int
main(int argc，char * argv[])
{
PS _ decoder _ t * PS；
cmd _ ln _ t * config；
FILE * FH；
char const *hyp，* uttid
int 16 buf[512]；
int RV；
int32 评分；

/*配置的初始化*/
config = cmd_ln_init(NULL，ps_args()，TRUE，
"-samprate "，" 8000 "，
"-jsgf "，" test.jsgf "，
NULL)；
PS = PS _ init(config)；

/*打开音频文件，开始馈入解码器*/
FH = fopen(" my recording . wav "，" Rb ")；
rv = ps_start_utt(ps，" go forward ")；
while(！feof(FH)){
size _ t nsamp；
nsamp = fread(buf，2512，FH)；
rv = ps_process_raw(ps，buf，nsamp，FALSE，FALSE)；
}
RV = PS _ end _ utt(PS)；

/*获取结果并打印*/
hyp = ps_get_hyp(ps，& score，&uttid)；
if (hyp == NULL)
返回 1；
printf("已识别:%s with prob %d\n "，hyp，ps_get_prob (ps，NULL))；

/* Free the stuff */
f close(FH)；
PS _ free(PS)；
返回 0；
}

在 Linux 上，用简单的命令行编译演示:

gcc ' pkg-config pocket sphinx–cflags–libs ' demo . c-o demo

然后跑

。/演示

如果有效，它就可以被包含到您的设备中。阅读 API 指南中关于 Pocketsphinx 函数
的更多信息:

[http://cmusphinx.sourceforge.net/api/pocketsphinx/](http://cmusphinx.sourceforge.net/api/pocketsphinx/)

完成基本示例后，就该使用 Pocketsphinx 构建应用程序了。当你设计它的时候，解放你的思想，不要只关注像“开灯”这样简单的命令。现代应用包括智能逻辑分析、连续听写支持和许多其他东西。尝试变得合理，设计你的界面和语法，考虑用户和你的演讲
应用将会成功。

还是不相信能行？查看演示 pocketsphinx 在诺基亚 N800 上运行的视频(在帖子顶部)。有关 Pocketsphinx、CMUSphinx 项目、语音识别的更多详情，请访问[http://cmusphinx.sourceforge.net](http://cmusphinx.sourceforge.net)

Adding speech recognition feature to your device

这里我们将考虑如何使用 CMUSphinx 项目([http://cmusphinx.sourceforge.net](http://cmusphinx.sourceforge.net))的
Pocketsphinx 库实现语音识别功能

使用 Pocketsphinx 的优点是:

* Pocketsphinx 是资源高效的。它可以完美地运行在嵌入式平台上
虽然不限于这些平台，但是你可以在你的桌面/服务器上使用 pocketsphinx。Pocketsphinx
只支持定点算法，因此可以在没有 FPU 的情况下运行。这也是优化
对一些流行的平台:Blackfin，Maemo，IPhone。
* Pocketsphinx 支持多种现成语言。它支持美国英语，中文，法语，俄语，德语，荷兰语等，而不需要培训什么。
* Pocketsphinx 是完全免费的软件。
*提供多种编程语言的可用绑定。

所以 Pocketsphinx 真的是你语音识别库的最佳选择。

在你开始编程语音界面之前，有几件事你需要知道

*语音识别器要求您指定他们将理解的单词(所谓的语法)，除了指定的语言，他们不会理解任何其他东西。
*语音天生就是不准确的，你需要把这个放在语音界面设计的角落里。
识别器返回你所识别文本的置信度值。确保使用这个置信度
值拒绝不可靠的结果。如果识别器不自信，再次尝试输入文本，
询问附加信息，确认用户意图。
*语音识别库的任务不是做声音输入。音频接口
通常是特定于设备的。您需要在您的应用程序中录制音频，并将其转换为特殊的
格式——PCM、单声道、8kHz、16 位。再次确认。如果你有 mp3，转换一下。如果您有 44.1kHz 的
音频，请对其进行降采样。

让我们从简单的测试开始。一旦安装了 Pocketsphinx，只需不带任何参数运行 Pocketsphinx_continuous
即可。等到

准备好了…

会出现在终端上然后说些什么。Pocketsphinx 将从您的麦克风记录音频并输出识别结果。

000000001:你好(-11998485)

你没能让它识别你好？别担心，有些人发现产生识别结果的是命运之手。算你运气好。

现在让我们尝试学习如何指定语法，Pocketsphinx 将识别的语言。这是用 JSGF 格式的语法文件完成的。

[http://Java . sun . com/products/Java-media/speech/for developers/JSGF/](http://java.sun.com/products/java-media/speech/forDevelopers/JSGF/)

这是相当简单的人类可读的文本格式，也许最好从示例开始:

# JSGF V1.0
语法 goforward
公共<移动> =前进<方向> <距离>【米|米】；
<方向> =向前|向后；
=(一|二|三|四|五|六|七|八|九|十|二十)+；

你可以看到它可以指定替代，重复和跳过。JSGF 基本上描述了识别器的有限状态自动化。你的语法越严格，识别的准确性就越好。但是不要忘记在真正的语法中包括所有那些填充符
和错误的开始。用户不会对设备说

"意大利香肠披萨"

他们会说

“我想让我想想……三个意大利辣香肠比萨饼，不……加洋葱”

你的语法应该涵盖这一点。一旦你创建了你的语法，将其存储为
grammar.jsgf。另外，以 16khz 单声道录制音频文件，并将其命名为“myrecording.wav”。

现在，让我们做一些编程。为了演示如何创建语音识别应用程序，让我们首先尝试将 Pocketsphinx 与 Python 结合使用。Python API 非常简单，示例只有 6 行代码。要识别语音，你需要完成三个步骤，它们是:

#!/usr/bin/python

#第一步，初始化
导入 pocketsphinx 为 ps
解码器= ps。解码器(jsgf = '/path/to/your/jsgf/grammar . jsgf '，samp rate = ' 8000 ')
#第二步，打开音频文件。
fh = open("myrecording.wav "，" Rb ")
nsamp = decoder . decode _ raw(FH)
#第三步，获取结果
hyp，uttid，score = decoder . get _ hyp()
print " Got result % s % d " %(hyp，score)

现在，让我们用 c 做同样的事情。它与 python 并没有真正的不同，只是更适合你的设备。

#包括

int
main(int argc，char * argv[])
{
PS _ decoder _ t * PS；
cmd _ ln _ t * config；
FILE * FH；
char const *hyp，* uttid
int 16 buf[512]；
int RV；
int32 评分；

/*配置的初始化*/
config = cmd_ln_init(NULL，ps_args()，TRUE，
"-samprate "，" 8000 "，
"-jsgf "，" test.jsgf "，
NULL)；
PS = PS _ init(config)；

/*打开音频文件，开始馈入解码器*/
FH = fopen(" my recording . wav "，" Rb ")；
rv = ps_start_utt(ps，" go forward ")；
while(！feof(FH)){
size _ t nsamp；
nsamp = fread(buf，2512，FH)；
rv = ps_process_raw(ps，buf，nsamp，FALSE，FALSE)；
}
RV = PS _ end _ utt(PS)；

/*获取结果并打印*/
hyp = ps_get_hyp(ps，& score，&uttid)；
if (hyp == NULL)
返回 1；
printf("已识别:%s with prob %d\n "，hyp，ps_get_prob (ps，NULL))；

/* Free the stuff */
f close(FH)；
PS _ free(PS)；
返回 0；
}

在 Linux 上，用简单的命令行编译演示:

gcc ' pkg-config pocket sphinx–cflags–libs ' demo . c-o demo

然后跑

。/演示

如果有效，它就可以被包含到您的设备中。阅读 API 指南中关于 Pocketsphinx 函数
的更多信息:

[http://cmusphinx.sourceforge.net/api/pocketsphinx/](http://cmusphinx.sourceforge.net/api/pocketsphinx/)

完成基本示例后，就该使用 Pocketsphinx 构建应用程序了。当你设计它的时候，解放你的思想，不要只关注像“开灯”这样简单的命令。现代应用包括智能逻辑分析、连续听写支持和许多其他东西。尝试变得合理，设计你的界面和语法，考虑用户和你的演讲
应用将会成功。

还是不相信能行？观看此视频[http://www.youtube.com/watch?v=OEUeJb6Pwt4](http://www.youtube.com/watch?v=OEUeJb6Pwt4)
演示在诺基亚 N800 上运行的 pocketsphinx。有关 Pocketsphinx、CMUSphinx 项目、语音识别的更多详情，请访问[http://cmusphinx.sourceforge.net](http://cmusphinx.sourceforge.net)