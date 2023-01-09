# 廉价的 XY 工作台使用业余爱好伺服

> 原文：<https://hackaday.com/2008/09/30/cheap-xy-table-using-hobby-servos/>

[CarlS]想做一个低成本的 x y 工作台在 teletoyland.com 的[展示。他意识到，为了保持低成本，他可以使用业余爱好伺服电机，而不是步进电机。精确的精度在这里不是一个大问题，所以业余爱好伺服将完全可以接受。](http://www.teletoyland.com/)

虽然线性业余爱好伺服系统是可用的，但他认为成本太高。他使用正常的业余爱好伺服系统，但必须修改其内部结构，以获得所需的准确行程。许多人修改业余爱好伺服连续旋转，但这将导致精确定位能力的损失。相反，他用一个 10 圈的电位计代替了测量伺服位置的电位计。这让他有了 10 倍的行程。

利用同步带和抽屉导轨，他构建了框架和运动组件。选择同步带是因为它们便宜的价格和无滑动的结构，由定制的滑轮牵引。

这个单元是通过一些 PHP 脚本控制的，他没有展开，通过一个到 SSC-32 板的串行连接。伺服系统直接连接到 SSC-32。去试一试吧，或者观看视频，看看它是如何工作的。

[https://www.youtube.com/embed/hLkY4V-H80w?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent](https://www.youtube.com/embed/hLkY4V-H80w?version=3&rel=1&showsearch=0&showinfo=1&iv_load_policy=1&fs=1&hl=en-US&autohide=2&wmode=transparent)