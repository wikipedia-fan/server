

# **Active Directory\(AD\)**

**定义**:是[微软](https://zh.wikipedia.org/wiki/%E5%BE%AE%E8%BB%9F)[Windows Server](https://zh.wikipedia.org/wiki/Windows_Server)中，负责架构中大型[网络](https://zh.wikipedia.org/wiki/%E7%B6%B2%E8%B7%AF)环境的集中式[目录管理服务](https://zh.wikipedia.org/wiki/%E7%9B%AE%E9%8C%84%E6%9C%8D%E5%8B%99)（Directory Services），在[Windows 2000 Server](https://zh.wikipedia.org/wiki/Windows_2000_Server)开始内置于Windows Server产品中.



**功能**：处理在组织中的网络对象，对象（AD中最小的存储单位）可以是用户，组群，计算机，网域控制站，邮件，配置文件，组织单元（OU），树系（forest）等；只要是在活动目录结构定义档（schema）中定义的对象，就可以存储在活动目录数据档中；



**AD结构：**以[树状](https://zh.wikipedia.org/wiki/%E6%A0%91_%28%E5%9B%BE%E8%AE%BA%29)的数据结构来组成网络服务的信息，在简单的网络环境中（例如小公司），通常网域都只有一个，在中型或大型的网络中，网域可能会有很多个。



**对象：**AD中最小的存储单位，每个对象均有自己的schema属性，可以存储不同的数据，像是用户、组群、计算机、邮箱或其他的基本对象等。

**组织单元**（Organization Unit，简称OU）：组织单元是一个具有收纳能力的活动目录对象；可以在OU之中存放AD的对象，包括用户，组群，计算机等，让组织结构在AD中可以被真实的反映出来，而且也方便AD中的另一个功能——组策略（Group Policy）的应用与集中管理；在AD中可以创建多个OU。

**对象的访问方式：**利用[活动目录Service Interface](https://zh.wikipedia.org/wiki/Active_Directory_Service_Interface)来访问，实际上，许多活动目录的管理工具都是利用这个接口来调用并使用活动目录的数据。





**网域**：一个AD网域底下的基本对象：

·Domain Controllers，存储网域所属的网域控制站（简称DC、域控）。

·Computers，存储加入网域的计算机对象。

·Builtin，存储内置的账户组群。

·Users，存储AD中的用户对象。



**多网域：**在AD中存在数个网域；网域内还是可以再创建不同的网域

**树系：**若需要在网域中共享数据或是做委派管理与配置设置时，便需要创建彼此间的组织关系，微软将AD中多网域相互的关系层次结构化，称为网域树

![](file:///C:\Users\wiki\AppData\Local\Temp\msohtmlclip1\01\clip_image001.png "https://upload.wikimedia.org/wikipedia/commons/thumb/5/50/ActiveDirectory\_DomainTree\_WithSubDomain.png/300px-ActiveDirectory\_DomainTree\_WithSubDomain.png")

Forest：在多个网域的环境下，负责在不同的网域之间负责交换与共享数据的角色，同时又必须要匹配AD树状结构的规范。一个组织中最多只能有一个Forest，在Forest下则是各自的网域树系，而在Forest下的网域或网域树系间，可以共享信息。

![](file:///C:\Users\wiki\AppData\Local\Temp\msohtmlclip1\01\clip_image002.png "https://upload.wikimedia.org/wikipedia/commons/thumb/9/91/ActiveDirectory\_Forest.png/300px-ActiveDirectory\_Forest.png")

## 实体结构

活动目录背后，则是一个植基于Windows Server网络基础结构（infrastructure）的网络服务与通信方式所组成。

AD的实体结构：只有DC（域控制站）和Member Server两种角色

DC：都可以负责处理来自客户端的网域查询

在以往的[Windows NT](https://zh.wikipedia.org/wiki/Windows_NT)网域环境中，网域的实体结构分为三种角色，即主要网域控制站（Primary Domain Controller, PDC）、备份网域控制站（Backup Domain Controller, BDC）以及成员服务器（Member Server）三种，网域的数据都存储在PDC和BDC中，并且在PDC和BDC间交换数据，但PDC和BDC的部署方式并不方便（一个网域只能有一个PDC），在不同的地理环境中也不能设置PDC，而且所有网域的查询都会被导向PDC，如此很容易造成网域登录和访问的塞车情况

Global Catalog（全域目录，简称GC）：存储了最完整的活动目录的结构数据，也是以目录为主（directory-enabled）的应用程序对AD的查询的主要标的。

Operation Masters（[营运主机](https://zh.wikipedia.org/w/index.php?title=%E7%87%9F%E9%81%8B%E4%B8%BB%E6%A9%9F&action=edit&redlink=1)）：被设置为担任提供特定角色信息的网域控制站，在每一个活动目录网域中，至少会存在三种营运主机的角色。

·Primary Domain Controller Emulator Master：设置作为这个角色的网域控制站，可以被目前仍存在网域中的Windows NT Backup Domain Controller（备份网域控制站）当做Primary Domain Controller（主要网域控制站）来调用使用，同时它也是树系中提供Windows Time Service时间同步的主机。

·RID Master：在网域控制站中会存储AD对象的relative ID（关系识别码），可分散以RID为主的查询的流量。

·Infrastructure Master：负责处理对目前网域的对象引用，以及对应其他网域的对象引用，并可负责处理针对AD对象的变更（例如删除与更名）。



**Site（活动目录站台）：**一个可能会有很多个网域控制站的实体的网络位置；

**功用**：在一个站台中，AD网域数据的复制，就是以站台为主，实际处理复制作业的工具称为KCC（Knowledge Consistency Checker，知识一致性检查器），它会在特定时间对站台设置中的网域进行数据的同步化，复制活动则分为对内复制（intra-site replication）与对外复制（或站间复制，inter-site replication）

默认情况下，站台的通信方式是使用IP（即RPC over IP）来通信，这个方式是最快的，且可以利用[TCP/IP](https://zh.wikipedia.org/wiki/TCP/IP)来运行远程调用以及处理，但若是非网域数据（架构、设置和通用类别目录更新，亦即没有AD对象）的复制，则可以利用[SMTP](https://zh.wikipedia.org/wiki/SMTP)通信方法

在中大型的网络环境中，适当的分散网络流量以及设计网络拓朴是很重要的事，KCC会利用设置好的网络通信成本（cost）来选择要用哪一条网络来进行复制

### DNS

活动目录极度依赖[DNS](https://zh.wikipedia.org/wiki/DNS)，因为DNS可以让AD表现出层次结构化的树状结构，同时也可以和开放的目录标准接轨，因此在建置网域时，DNS服务（或另有架设DNS Server）一定要存在于网络或该网域控制站中，AD以SRV记录（SRV Record）来识别网域控制站，以提供网域处理的服务，而和Windows NT网域不同的是，Windows NT使用的是[NetBIOS](https://zh.wikipedia.org/wiki/NetBIOS)通信协议，但AD使用的则是[TCP/IP](https://zh.wikipedia.org/wiki/TCP/IP)，但AD仍然提供可以在Windows NT账户格式（DOMAIN\User）和AD账户格式（user@domain）的格式互转。

### 实体存储

**存储量**：活动目录使用强化过的[Microsoft Jet Database Engine](https://zh.wikipedia.org/wiki/Microsoft_Jet_Database_Engine)（基于Microsoft Jet Blue项目），即[Extensible Storage Engine](https://zh.wikipedia.org/w/index.php?title=Extensible_Storage_Engine&action=edit&redlink=1)（ESE98），可存储16TB的数据量，理论上可容纳十亿个网域对象；

**存储位置&形式：**文件名称为NTDS.dit，它存储在%system\_root%\NTDS目录中（这个目录所在的磁盘也必须要是[NTFS](https://zh.wikipedia.org/wiki/NTFS)格式），内含了对象数据表以及链接数据表，在Windows Server 2003中加入了一个描述安全信息的新数据表。

而在AD更新数据时的记录，都被存储在edb\*.log，默认的名称为edb.log，其他的文件使用"edb" +数字 + ".log"来记录，另搭配了edb.chk作为检查点日志，以及Res1.log和Res2.log作为系统的保留文件。

**AD实体存储的组件有：**

·上层接口（interface）：作为目录服务客户端或目录服务中的其他服务器的连接接口，像是LDAP、REPL、MAPI与SAM等。

·目录服务代理人（Directory Service Agent）：实现于NTDSA.DLL，负责接收与处理来自客户端的要求或其他服务器的要求（例如KCC的要求）。

·数据库访问层：内含于ntdsa.dll中，负责直接访问数据库。

·延伸存储引擎（Extensible Storage Engine）：负责处理数据库与其名称（DN）的记录对应。

·数据库文件：即NTDS.dit，以及负责处理未认可交易的日志。

**NTDS重组方式：**网域控制站会定时（默认为12小时）对NTDS.dit做重组（defragment），并清除数据档中的垃圾，在重组前会检查磁盘空间是否有大于数据库文件1.5倍的空间可用。若数据库所在的目录没有足够的可用空间，就要把数据库移往其他地方去。然而，由于Windows 2000与Windows Server 2003在[卷影复制服务](https://zh.wikipedia.org/wiki/%E7%A3%81%E7%A2%9F%E5%8D%80%E9%99%B0%E5%BD%B1%E8%A4%87%E8%A3%BD%E6%9C%8D%E5%8B%99)（VSS）的机制有所不同，使这移动过程有可能失败。对于Windows 2000，log files与数据库可以分别存放在不同的磁盘上，但Windows Server 2003则必须放在同一个磁盘上。要移动数据库，必须重新启动服务器，并进入活动目录 Restore Mode里，利用[ntdsutil](https://zh.wikipedia.org/wiki/Ntdsutil)工具进行移动。

### `只读网域控制站（Read-Only Domain Controller，简称RODC）：在Windows Server 2008中加入的一个新的网域控制站角色，RODC可以作为组织的分部、分公司、办公室或是临时单位等，将网域控制站放在该处时会有安全性疑虑或风险时使用，顾名思义，RODC不会写入任何数据到活动目录，与其他网域的复写也是有限度的，并且只会以系统管理员定义的Password Replication Policy（密码复制原则）控制下的账户才会缓存密码等功能。`

## 安全性

活动目录的安全性可分为对象的安全性识别、层次结构的安全性以及森林之间的信任关系等。

**对象的安全性识别：**AD以[Kerberos](https://zh.wikipedia.org/wiki/Kerberos)V5作为其安全验证的主要架构，并且每个AD对象都拥有一个独一无二的安全性识别码（Security Identifier，SID），其格式示例为S-1-5-21-7623811015-3361044348-030300820-1013，每组代码均有其意义，这组识别码存储在AD的objectSid属性中。

层次结构的安全性：在AD中，不同层次结构的OU可以定义不同的安全性信息，以及不同的用户权限，而不同的网域层次结构之间也可以定义不同的用户权限，管理员也可以利用安全性管理模板（Secutiy Template）来定义不同的安全性信息，或者使用组策略（Group Policy）来定义，在大型网络之中，使用组策略会比安全性模板要来的方便，将两者合并使用更可达到事半功倍之效（例如和Microsoft Base Security Analyzer的集成）。

两个Forest间的信任关系：需要在两个Forest间共享或授权访问时，可以利用信任关系（trust relationship）来创建Forest间的信任，以授权在彼此树系间的访问权

在Windows Server 2003以后版本的AD环境可支持四种信任关系：

·**快捷方式式信任（shortcut trust）**，此为加速验证流程所设计的信任法，在多层次的网域中，用户只要连接到最近的网域即可登录，无需要将消息转到授权的根服器。

·**外部式信任（external trust）**，此为跨森林的授权方法。

·**领域式信任（realm trust）**，作为与非Kerberos验证的LDAP目录服务与Windows网域的信任模式。

·**森林式信任（forest trust）**，此为强化型的外部式信任法，可以经由一个中介的森林信任来获取信任关系，例如acme.com.tw信任aspvendor.com，而contoso.com.tw也信任aspvendor.com，则acme.com.tw可以获取和contoso.com.tw的信任关系。

**信任关系方向：**信任关系的设置可以分为单向（one-way）和双向（two-way）两种，单向信任表示被信任的一方可以访问信任的一方的资源，而双向信任则是可以访问各自的资源。

**信任关系的传递**：分为可递移（transitive）与不可递移（non-transitive）两种。

**可递移**：表示创建信任关系的网域在同一树系内的其他网域也可以使用在创建信任关系网域中的信任信息。

**不可递移**：则表示只有创建信任关系的网域（不论是否有层次结构）才可以使用信任信息。

## 名称系统

**活动目录支持的的命名格式：**LDAP和NT时代的UNC格式。

**默认格式：**[LDAP](https://zh.wikipedia.org/wiki/LDAP)（轻量级目录访问协议）版本的[X.500](https://zh.wikipedia.org/wiki/X.500)协议为主（由ADSI LDAP Directory Service Provider），对于AD这种如此规模的目录服务而言，LDAP这种具有层次结构识别能力的协议，非常适合作为目录服务的访问协议AD NT**时代的UNC格式**：由ADSI Windows NT Directory Service Provider提供

在UNC与LDAP名称间的转换则由ADSI的`IADsNameTranslate`接口来提供。

### 识别名：每个AD对象均有一个以LDAP组成的名称（Distinguished name，简称DN）

### 这个识别名是作为使用LDAP查询AD目录中识别对象的名称，其格式类似下列：

```
LDAP://cn=John Smith, ou=Software Engineering, dc=engineering, dc=acme, dc=com, dc=tw
```

```
LDAP://cn=COMP1024, ou=Computers, dc=acme, dc=com, dc=tw
```

在LDAP字符串中经常使用的代字有：

·**DC**：domainComponent

·**CN**：commonName

·**OU**：organizationalUnitName

·**O**：organizationName

·**STREET**：streetAddress

·**L**：localityName

·**ST**：stateOrProvinceName

·**C**：countryName

·**UID**：userid

### 一般名称（Canonical Name）：每个AD中的对象都会有一个一般的名称

### 在Schema中的属性为cn（Common Name），但组织单元（OU）基本上是例外，它自己有一个代字ou作为识别符。

## 功能层次

**功能层次定义：**为了要能够容纳不同版本的Windows操作系统以及其网域，因此特别在AD中使用了一种版本控制的机制，定义了目前在网域环境中可以使用的最大版本层次，同时这个修改是单向无法撤消的修改。

**举例：**若网域中有不同版本操作系统的网域控制站，则为了最大的兼容性，功能层次的设置应要以最低版本为主，例如一个网域中有Windows Server 2003和Windows 2000时，则网域的功能层次应该设为Windows 2000混合模式（Mixed Mode），若设为Windows Server 2003原生模式（Native Mode）时，Windows 2000的网域控制站会失效。

若要在网域中安装新版本的操作系统（例如在Windows Server 2003网域中要安装Windows Server 2008）作为网域控制站时，必须要先将活动目录中的Schema信息做扩充以兼容于较新版本的操作系统，因此微软在安装光盘中都会提供一个活动目录准备工具 \(adprep.exe），它可以让系统管理员以简单的方式升级活动目录中的数据结构，包含树系以及网域的数据结构（使用首选项），以兼容于新版本操作系统。

## 对象结构

由于微软在设计活动目录是使用开放型的目录服务为方针，且目录服务的最基本特性之一就是要能“广纳百川”，除了基本的网络服务数据外，还需要能够和其他异质型服务连接与集成，因此微软在AD之中实现了一个对象的存储单位，称为“对象结构”（schema），对象结构可以视为AD对象的[元数据](https://zh.wikipedia.org/wiki/%E5%85%83%E6%95%B0%E6%8D%AE)（metadata）。每一个对象（不论是单元或是容器对象）都有各自的schema，用以存储识别该对象的不同数据，schema是由class和attribute所组成，attribute是最小的存储单元，class则是包含attribute的集合体。

## 服务

活动目录本身除基本的网络目录服务外，微软也应用这个基础架构设计了不同的服务，并且在Windows Server 2003不同的版次中加入，以提升活动目录的应用范围。

### 联合服务\[[编辑](https://zh.wikipedia.org/w/index.php?title=Active_Directory&action=edit&section=25)\]

由于AD本身具有可分布式的身份验证与授权能力，且在2003年时Web正吹起了单一签入（single-sign on）的架构研究风，微软也开始利用AD来设计一个可支持多个网站（或应用程序）的单一签入功能，其实现品即为活动目录Federation Services（AD联合服务，简称ADFS），它显露了几个主要成员[\[5\]](https://zh.wikipedia.org/wiki/Active_Directory#cite_note-5)：

·Federation Service：负责在ADFS的SSO架构中处理验证的服务器。

·Federation Service Proxy：在外部网络或是WS-I服务中，扮演Federation Service的代理角色，并支持WS-Federation规格的验证设置。

·Claim-aware client：由ADFS开放的Claim-aware（宣告感知）组件的Web客户端，或是[ASP.NET](https://zh.wikipedia.org/wiki/ASP.NET)应用程序，可直接支持ADFS的SSO架构。

·Windows Token-based Agent：以Windows验证为主的Web应用程序，ADFS可支持AD权仗与Windows NT权仗的模拟与交换。

此服务在Windows Server 2003 R2版本中首次出现，并在Windows Server 2008中升级为活动目录Federation Service角色。

### 轻量级服务

轻量级服务（Lightweight Directory Service）[\[6\]](https://zh.wikipedia.org/wiki/Active_Directory#cite_note-6)在Windows Server 2003中被称为活动目录Application Mode（ADAM），它是一个不需要与AD基础架构集成就可以独立运作的目录服务，适合用来表现企业的层次结构化概念与对象的管理，而且开发人员只要把使用ADSI的经验搬过来即可使用，不必另外学习ADAM的操作方法，它也可以做为ADFS的外部验证提供者。轻量级目录可以在同一台计算机中安装多个运行个体，因此也很适合用ADAM来实现Directory-Enabled的应用程序，尤其是与组织结构相关的（例如人事或人力资源系统），ADAM本身也可以延伸schema，开发人员可以将ADAM视为另一种型式的数据库，也可以由AD中复制数据到ADAM，不过ADAM不会对AD进行站台复制，开发人员需要自行撰写程序来复制数据。

轻量级服务在Windows Server 2008中改名为活动目录Lightweight Directory Service（简称AD LDS），并提升为AD的应用角色之一。

### 证书服务

证书服务（Certificate Service）[\[7\]](https://zh.wikipedia.org/wiki/Active_Directory#cite_note-7)是在Windows Server 2008中首次纳入活动目录体系的服务，它原本是在Windows 2000与Windows Server 2003的证书服务器（Certificate Server），用来创建企业中的[公开密钥基础建设](https://zh.wikipedia.org/wiki/%E5%85%AC%E9%96%8B%E9%87%91%E9%91%B0%E5%9F%BA%E7%A4%8E%E5%BB%BA%E8%A8%AD)，在Windows Server 2008中，证书和AD对象有了更强更紧密的集成，所以有了活动目录Certificate Service（AD CS）的角色，这个角色还可以和权限管理的Right Management Service（RMS）集成在一起，提供对文件或应用程序层次的权利管理。

### 权利管理服务

权利管理服务（Right Management Service）[\[8\]](https://zh.wikipedia.org/wiki/Active_Directory#cite_note-8)也是在Windows Server 2008中首次纳入活动目录体系的服务，最早的时候，它是在[Microsoft Office 2003](https://zh.wikipedia.org/wiki/Microsoft_Office)开始提出的信息权利管理（Information Right Management）功能，可利用它来控制Office文件散布时的权限，例如打印以及存储文件等，接着微软发表了Right Management Server以及RMS SDK，供Windows Server 2003平台使用，而在Windows Server 2008中即将它集成到活动目录中，变成AD服务的一部分。

## 集成Unix到活动目录中

活动目录互通的多样性层次得以透过匹配标准的LDAP客户端在大多数的[类Unix操作系统](https://zh.wikipedia.org/wiki/%E7%B1%BBUnix%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F)记录，但这些系统通常缺乏与Windows组件像是组策略与单向信任关系的许多属性的自动直译，目前也有许多第三方软件厂商提供了将Unix平台（包含[UNIX](https://zh.wikipedia.org/wiki/UNIX)、[Linux](https://zh.wikipedia.org/wiki/Linux)、[Mac OS X](https://zh.wikipedia.org/wiki/Mac_OS_X)与数个[Java](https://zh.wikipedia.org/wiki/Java)与Unix-based应用程序）集成活动目录方法，这些供应商的一部分，包含Thursby Software System（ADmitMac）, Quest Software（Vintela Authentication Services）, Centrify（DirectControl），与Likewise Software（Likewise Open and Likewise Enterprise）。Microsoft也在这个市场中拥有为UNIX产品所设计的免费Microsoft Windows服务（即Windows Service for Unix）。

这些额外的对象结构在Windows Server 2003 R2版本中被发布，包含完全对应到RFC 2307的一般用途的属性。这些RFC 2307、nss\_ldap与pam\_ldap的引用实现均提供自PADL.com，包含直接使用这属性以及填充信息的支持。默认组群成员（group membership）的活动目录Schema与被提议的RFC 2307bis延伸功能一起编译。RFC 2307bis使用LDAP成员属性存储Unix的组群成员数据，与基础RFC 2307，以存储组群成员为以逗号分隔的用户识别码菜单有所不同。Windows Server 2003 R2包含了一个[MMC](https://zh.wikipedia.org/wiki/Microsoft_Management_Console)snap-in以创建与编辑这些属性。

一个替代选项是使用其他的目录服务，像是[Fedora](https://zh.wikipedia.org/wiki/Fedora)Directory Server（之前的Netscape Directory Server）或是[Sun](https://zh.wikipedia.org/wiki/Sun)的Java System Directory Server，它可以运行与活动目录双向同步化，进而在需要使用FDS验证的Unix与Linux平台与需要使用Windows验证的Windows客户端之间，提供一个与活动目录之间**转向**（deflected）的集成。另一个选项是使用[OpenLDAP](https://zh.wikipedia.org/wiki/OpenLDAP)以及它的透通覆盖（translucent overlay）功能得以延伸项目于使用额外属性存储在本地数据库的任何远程LDAP服务器上。在本地数据库中指示的客户端将会看到包含在远程和地的属性，当远程数据库仍保持完整不变的情况下。



