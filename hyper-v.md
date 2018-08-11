Hyper-v：

定义：

分类：Windows server上一个组件；独立的虚拟化服务器

区别：Hyper-v作为独立的虚拟化服务器直接运行在硬件之上，没有GUI图形化不能直接管理安装和管理虚拟机，只能通过win8专业版或企业版和win server 2012 的Hyper-v管理工具进行管理（默认没有开启，专门用来管理Hyper-v 2012）

Hyper-v角色添加：win server2012上手工添加hyper-v角色以及hyper-v所需的其它组件：windows管理程序、hyper-v虚拟街管理服务、虚拟化WMI提供程序、虚拟机总线（VMBUS）虚拟化服务提供商（VSP）的VID；Hyper-v server本身就自带Hyper-v角色。

硬件要求：64位支持虚拟化（Inter VT和AMD-v）的CPU支持硬件强制实施的数据执行保护（DEP）技术，即启用InterXD位和AMD的XD位

存储规划

内存规划：

Hyper-v server 部署流程：

1、启用服务器CPU虚拟化技术（进入BIOS）

![](/assets/启用CPU虚拟化.png)

2、使用Hyper-V Server 2012 RC光盘引导，出现如下画面

![](/assets/hyper-v安装起始界面.png)

3、接下来选择“安装语言”、“时间和货币格式”、“键盘和输入法”（注：RC现只有英文版），然后点击“next”

![](/assets/语言时间.png)

然后点击“Install now”

![](/assets/Hyper-v安装界面.png)

选择“i accept this license terms”

![](/assets/Hyper-v同意协议.png)

安装类型选择：高级自定义安装

![](/assets/Hyper-v高级自定义安装.png)

选择驱动器类型自行分区

![](/assets/驱动器类型并分区.png)

安装完成重新启动后更改计算机名称后重新启动，进入系统后服务器加入域：

![](/assets/Hyper-v服务器加入域.png)

![](/assets/加域.png)

加入域完成后，不修改计算机名称重新启动

开启Hyper-v远程管理服务，以使用Hyper-v管理器进行挂你，输入“4

选择“Enable Remote Management”输入“1”，回车

然后为Hyper-v设备IP地址和DNS服务器地址

设置完毕后，选“11”注销账号后，就可以使用Hyper-v管理器进行管理了



