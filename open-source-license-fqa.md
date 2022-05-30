# 开源许可证常见问题解答

## 1、关于GPL的传染性
### 问：用GPL的编译器编译代码，该代码必须用GPL吗？
答：GPL的传染是基于“衍生作品”的。“如何证明不是衍生作品” 唯一被认可的方式是建立 address space boundary。被承认的 ASD 包括：
（1）基于 MMU 的内存空间隔离（进程隔离，用户态，内核态隔离）。
（2）程序、数据隔离。比如 GCC 不会感染被编译的源文件。
（3）虚拟机隔离。两种语言并不使用同样的 IP（instruction counter）。比如 Lua 虚拟机和其上的 Lua 代码，JVM 和 Java byte code。VM 使用硬件的 IP，而 byte code 采用 VM 提供的虚拟 IP。Byte code 到 VM 之间的控制权切换并不是简单的 IP 附值。
### 问：用GPL的编译器编译后的代码，需要遵循什么样的许可要求？
答：这须要检查编译器生成的可执行代码a的源码A是在哪一种开源许可证下，例如:A在Apache-2.0下，它要求其源码和可执行代码都要添加修改声明。有少数的开源许可证对可执行代码没有要求，如MPL-2.0。
### 问：我有参与另外一个开源项目叫ST，LICENSE是MPL或者GPLv2。有个人给ST提了Patch，但看起来是从glibc中拷贝的一段代码，glibc是LGPL。请问这个Patch有违反glibc的协议么？
- Patch：https://github.com/ossrs/state-threads/pull/25
- Glibc的代码：https://sourceware.org/git/?p=glibc.git;a=blob;f=sysdeps/riscv/setjmp.S;h=0b92016b311b11aa9eeb62b38c670a262f1924c9;hb=1d9764aba8c00754fbf8299e48afbe222245ee3e
- ST的授权：https://github.com/ossrs/srs/wiki/LicenseMixing#state-threads
- GLIBC: https://en.wikipedia.org/wiki/Glibc

答：如果patch的代码是复制glibc（而非调用），ST可以合并该patch，但合并后的ST须要遵循GPLv2+(只能选择双重许可中的GPLv2+来分发后续版本)。原因：ST采用双重授权，后续版本可以采用MPL或GPLv2+中任一许可证授权，glibc采用LGPL-2.1+授权，LGPLv2.1 允许把代码重新按照 GPLv2 及新版本发布，因此合并该patch的后续版本只能选择GPLv2+.

### 问：我们要开源一个Linux内核工具，其中用到了GPL的开源项目。使用木兰协议的哪一个版本比较合适？华为的欧拉是基于Linux内核项目，为什么可以用木兰？
答：Linux内核的GPL传染性有个特例，可以通过系统调用的方式隔离，这是因为Linux 内核的作者 Linus Torvalds 在Linux内核源码文件中澄清了普通系统调用为非 GPL 的作用范围。这个“Linux内核工具”使用的GPL组件如果不属于上述情况，须要证明该工具不是GPL组件的衍生作品，否则只能用GPL，因为GPL还没有兼容木兰协议。

## 2、关于贡献者协议
### 问：CLA、DCO与开源许可证的区别？
| 特征 | CLA | DCO| 开源license |
| ---- | ---- | ---- | ---- |
| 签署方式 | 与社区一次性签署 | 每次提交的commit中签署 | 伴随源码 |
| 内容 | 社区或组织可自行定义 | 由Linux Foundation提出并定义，全文仅4条内容 | 由许可证发布方定义 |
| 目标 | 明确参与贡献的有关法律义务，是开源license的补充 | 确保贡献者遵守开源license | 明确开源项目中授予的权利和义务 |

## 3、关于公共领域
### 问：什么叫做将代码放入公共领域？
答：“公共领域”或者说“公有领域”是在著作权法理论中被广泛使用的概念。著作权法保护的著作权是一种专有权，在这种专有权之外的部分则处于公有领域—通常是指没有被著作权法纳入保护范围的作品、保护期限届满的作品以及权利人已放弃的著作权。
有2种情况软件可以进入到公共领域：1、软件超过了著作权保护的时限（作者有生之年及死亡后50年）；2、作者声明软件放入公共领域（例如CC0、Unlicense等,作者通过对特定作品声明，在法律允许的最大范围内，放弃其在该作品上的全部著作权和邻接权，将作品贡献于公共领域）。

## 4、关于木兰宽松开源许可证

### 问：木兰宽松许可证，第2版（Mulan PSL v2）与业界主流许可证兼容情况如何？

许可证的兼容性评判并无统一标准。我们从Mulan PSL v2的条款及目的出发，认为Mulan PSL v2与BSD类许可证类似，兼容性很好。BSD、MIT类宽松许可证兼容Mulan PSL v2许可证；Mulan PSL v2兼容Apache License v2.0、L/GPLv2、L/GPLv3等许可证。即，许可在BSD、MIT类许可证下的代码可以贡献到Mulan PSL v2的项目中，许可在Mulan PSL v2下的代码可以贡献到Apache License V2.0、L/GPLv2或L/GPLv3等的项目中。

注意，许可证A兼容许可证B（A许可证是B许可证 Compatible）是指，A授权的作品与B授权的作品经过修改或合并，可以使用B对作品的整体进行授权。兼容性是有方向的，A兼容B，但B不一定兼容A。

### 问：一个软件用Apache license，直接替换成MulanPSL-2.0可以吗？
答：如果这个软件没有其他贡献者，软件的作者可以直接将许可证由Apache替换为MulanPSL-2.0；
如果软件有其他贡献者，需要征得所有贡献者同意，软件的作者才能将软件的许可证由Apache替换为MulanPSL-2.0；
如果贡献者修改软件或者将软件集成到自己项目中，可以使用MulanPSL-2.0对衍生软件的整体进行授权（因为Apache组合兼容MulanPSL-2.0），但需要满足衍生软件中原Apache授权部分仍然遵循Apache的约束。


## 5、关于各种开源软件及其许可证的问题

### 问：开源软件会断供吗？
答：软件一旦开源（如图中v1），社区便存在该软件的开源版本，即使该软件在将来某个版本闭源（如图中v4），也不影响之前的开源版本，即您可以使用v1、v2、v3版本的源码并遵循其所采用的开源许可证。    
因此，开源软件因闭源而断供，断的“供”仅指闭源版本（相较于开源版本）的新功能或新改进，您仍然可以基于往期的开源版本进行开发。
![image](https://user-images.githubusercontent.com/24621557/171010239-54df1223-350d-4f10-9141-380ac9f85934.png)
### 问：常见开源软件的授权与使用？
- （1）mySQL的使用？   
答：mySQL采用双重授权(dual license)(<https://dev.mysql.com/doc/refman/8.0/en/what-is-mysql.html>)。MySQL社区版使用GPL-2.0 授权，意味着任何人都可以使用和修改软件，而无需支付任何费用，您还可以研究源代码并更改它以满足您的需要。如果您对GPL不满意，或者需要将MySQL代码嵌入到一个商业应用程序中，您可以购买一个商业许可证版本(<http://www.mysql.com/company/legal/licensing/oem/>)。     
- （2）mongDB的使用？     
答：MongoDB 社区版在2018年10月16日之后发布的所有版本采用SSPL授权；MongoDB社区版在2018年10月16日之前发布的版本仍采用AGPL-3.0授权(<https://www.mongodb.com/community/licensing>)。
SSPL-1.0与AGPL-3.0都规定，如果使用MongoDB软件或使用基于MongoDB源码制作的软件，通过交互的方式为第三方提供服务，则必须根据其授权条款，通过网络下载向每个人免费提供该服务源代码（即MongoDB软件或基于MongoDB源码制作的软件）。      
不同的是，SSPL-1.0的13条还规定，向第三方提供服务，当该服务的价值全部或主要来源于MongoDB（或基于MongoDB制作的软件），或者该服务是为第三方使用MongoDB（或基于MongoDB制作的软件）提供帮助，那么该服务的源码也须要根据SSPL-1.0免费提供（<https://www.mongodb.com/licensing/server-side-public-license>）。      
也就是说，AGPL-3.0对提供SAAS的程序具有免费公开源码的限制性，而SSPL-1.0对提供SAAS、PAAS、IAAS的程序都有免费公开源码的限制性（只要该服务的价值主要源于SSPL-1.0授权的软件）。     
值得注意的是，SSPL-1.0未经OSI认证通过。     
- （3）Linux kernel的使用？     
答：Linux内核采用GPL-2.0授权，基于（全部或部分）Linux内核代码的程序（与linux内核代码运行在同个进程地址空间）须要根据GPL-2.0开源。但有一种例外情况，即如果程序是通过系统调用的方式使用了Linux内核代码，则该程序不需要根据GPL-2.0开源（<https://docs.kernel.org/process/license-rules.html>）。然而，该例外仅针对Linux内核（Linus在Linux内核的COPYING文件中作出的澄清），不包括其他根据GPL-2.0授权的软件。     
![image](https://user-images.githubusercontent.com/24621557/171004960-56943e2d-5250-4ac6-a127-89b8fbbd8ae2.png)
