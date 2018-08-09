# hypervisor

**定义：虚拟机器监视器**（英语：virtual machine monitor，缩写为 VMM），是用来建立与执行[虚拟机器](https://zh.wikipedia.org/wiki/虛擬機器)的软件、固件或硬件；Hypervisor是一种运行在物理服务器和操作系统之间的中间软件层,可允许多个操作系统和应用共享一套基础物理硬件。

**宿主机（host machine；主体机器）：**被Hypervisor用来执行一个或多个虚拟机器的电脑

**客体机器（guest machine）：**运行在宿主机上的虚拟机器。

**功用：**hypervisor提供虚拟的作业平台来执行客体操作系统（guest operating systems），负责管理其他客体操作系统的执行阶段；这些客体操作系统，共同分享虚拟化后的硬件[资源](https://zh.wikipedia.org/wiki/資源_%28計算機科學%29)。

**分类：**本地或裸机Hypervisor（裸金属架构）和Hosted Hypervisor（宿主型）

裸机Hypervisor（裸金属架构）：在虚拟化中Hypervisor直接管理调用硬件资源，不需要底层操作系统

特点

1. 需要硬件支持

2. 虚拟机监视器作为主操作系统
3. 运行效率高

举例

1. [VMware](https://zh.wikipedia.org/wiki/VMware) 5.5及以后版本
2. [Xen](https://zh.wikipedia.org/wiki/Xen) 3.0以后版本
3. [Virtual PC](https://zh.wikipedia.org/wiki/Virtual_PC) 2005
4. [KVM](https://zh.wikipedia.org/wiki/Kernel-based_Virtual_Machine)





