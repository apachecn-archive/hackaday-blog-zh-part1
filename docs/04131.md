# 如何生成字体和图片头文件

> 原文：<https://hackaday.com/2009/09/29/how-to-generate-font-and-picture-header-files/>

![custom_fonts_displayed](img/8fbfbb5848119260b88bebd688b8e37a.png "custom_fonts_displayed")

使用微控制器在 LCD 屏幕上显示自定义字体或图像通常需要相当多的工作。我们已经使用了一些现成的工具，让您的下一个项目变得更加容易。我们的 python 脚本将 BMP 文件转换成一个头文件，以备 AVR 微控制器使用。休息之后我们会带你走一遍。

在本教程中，我们将结合使用 [Python](http://www.python.org/) 和 [GNU 图像处理程序](http://www.gimp.org/)。我们正在开发一个 Ubuntu 9.04 系统，但是因为这些是跨平台的工具，你应该可以在任何操作系统上完成。

**脚本的作用:**

Python 脚本获取一个或多个 1 位调色板索引的 [BMP 图像](http://en.wikipedia.org/wiki/BMP_file_format)，截取标题和任何未使用的列数据，并输出一个头文件，其中的信息存储在 PROGMEM 中的一维数组中。然后，可以从数组中读取这些数据，并在 AVR 代码中进行处理，以便以您需要的任何显示格式使用。这可以用来生成字体，或转换更大的图像。

**生成 BMP 文件:**

**![create_new_image](img/97f4ec3ff6c289da011c2da190bbed33.png "create_new_image")**

打开 GIMP，用您需要的尺寸创建一个新文件。高度由您决定，但宽度应该是 8 的倍数，以符合 8 位宽的存储方案。在这种情况下，我们感兴趣的是生成一组将在 24×30 像素区域显示的字体。

![centering_character](img/df01812e7be0b897d7b2d842df004ec0.png "centering_character")

使用字体工具，选择你想要的字体并添加你的角色。调整大小和位置，直到填满画布。您应该确保没有选中字体工具的抗锯齿复选框。

![indexed_bmp](img/75e3bc251346c041a0a0caa571634167.png "indexed_bmp")

BMP 文件是自下而上保存的，**我们需要将图像反转**。为此，请单击图像菜单，转到变换，并选择“垂直翻转”。我们还需要使这成为一个索引图像。为此，单击顶部的图像菜单，进入模式并选择“索引…”。从该菜单中，选取“使用黑白(1 位)调板”。现在将文件保存为 BMP 图像。在我们的例子中，我们将它保存为 4.bmp。对您希望包含在新字体头文件中的每个字符重复这个步骤。

**使用脚本:**

下载我们的 [bmp2header.py 文件](http://blog.mahalo.com/hackaday/misc/bmp2header.zip)。

```
$ python bmp2header.py *.bmp

Please enter how many bytes (8-bits) wide
the image data needs to be:

3

Generating header file with a byte width of: 3 bytes
Successfully generated: my_header.h
```

运行该文件，将您的 BMP 图像作为命令行参数。您将被要求输入图像所需的列宽。我们的示例图像为 24 像素宽，因此我们希望标题数据为 3 字节宽(24 像素/8 位= 3 字节)。从输出中可以看到，脚本成功创建了 my_header.h。

下面是该文件的内容(在本例中，是“4”字符的数据):

```
#include &lt;avr/pgmspace.h&gt;

static const char PROGMEM my_header[]={

//4
0x1f, 0x00, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x80, 0x00,
0x3f, 0x81, 0xfc,
0x3f, 0x81, 0xfc,
0x3f, 0x81, 0xfc,
0x3f, 0xff, 0xfc,
0x3f, 0xff, 0xfc,
0x3f, 0xff, 0xfc,
0x3f, 0xff, 0xfc,
0x00, 0x01, 0xfc,
0x00, 0x01, 0xfc,
0x00, 0x01, 0xfc,
0x00, 0x01, 0xfc,
0x00, 0x01, 0xfc,
0x00, 0x01, 0xfc

};
```

在头文件中，由脚本处理的每个 BMP 都会在十六进制输出前附加一个文件名作为注释。我们的 4.bmp 数据显示在 3 列 30 行的字节中。这与我们寻求的 24×30 宽高比相匹配。如果你有一个比这个大得多的输出，你要么没有使用 1 位索引图像，要么当脚本要求你输入列宽时出现了错误。

**从头文件中访问数据:**

如何使用这个头数据超出了本教程的范围。下面是我们用来写入本文顶部图像显示的代码。我们的屏幕是通过声明我们想要写入的区域，然后发送该区域的位数据流来写入的。我们提供此信息仅供参考:

```
#include my_header.h

void Other_Num(unsigned char num, unsigned char x, unsigned char y)
{
 //Setup screen area for writing:
 LCD_Out(0x2A, 1);
 LCD_Out(x, 0);
 LCD_Out(x+23, 0);
 LCD_Out(0x2B, 1);
 LCD_Out(y, 0);
 LCD_Out(y+29, 0);
 LCD_Out(0x2C, 1);

 unsigned char temp;
 for (unsigned char i=0; i&lt;90; i++)                //Read one column of char at a time
 {
 temp = pgm_read_byte((char *)((int)my_header + (i + (90*num))));    //Get column from progmem

 for (unsigned char k=0; k&lt;8; k++)
 {
 if (temp &amp; 1&lt;&lt;(7-k)) LCD_Out(blue, 0);
 else LCD_Out(white, 0);
 }
 }
}

```

**结论**

使用这种方法可以使字体集的生成变得更加容易。我们能够在大约 45 分钟内生成五个不同的数字集合(0-9)。我们希望这对你的下一个项目有所帮助。不要忘记在评论中加入新字体的图片。