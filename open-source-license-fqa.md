#开源许可证常见问题解答
## 1、关于GPL的传染性
### 问：用GPL的编译器编译代码，该代码必须用GPL吗？
答：GPL的传染是基于“衍生作品”的。“如何证明不是衍生作品” 唯一被认可的方式是建立 address space boundary。被承认的 ASD 包括：
（1）基于 MMU 的内存空间隔离（进程隔离，用户态，内核态隔离）。
（2）程序、数据隔离。比如 GCC 不会感染被编译的源文件。
（3）虚拟机隔离。两种语言并不使用同样的 IP（instruction counter）。比如 Lua 虚拟机和其上的 Lua 代码，JVM 和 Java byte code。VM 使用硬件的 IP，而 byte code 采用 VM 提供的虚拟 IP。Byte code 到 VM 之间的控制权切换并不是简单的 IP 附值。
### 问：用GPL的编译器编译后的代码，需要遵循什么样的许可要求？
这须要检查编译器生成的可执行代码a的源码A是在哪一种开源许可证下，例如:A在Apache-2.0下，它要求其源码和可执行代码都要添加修改声明。有少数的开源许可证对可执行代码没有要求，如MPL-2.0。
### 问：我有参与另外一个开源项目叫ST，LICENSE是MPL或者GPLv2。有个人给ST提了Patch，但看起来是从glibc中拷贝的一段代码，glibc是LGPL。请问这个Patch有违反glibc的协议么？
- Patch：https://github.com/ossrs/state-threads/pull/25
- Glibc的代码：https://sourceware.org/git/?p=glibc.git;a=blob;f=sysdeps/riscv/setjmp.S;h=0b92016b311b11aa9eeb62b38c670a262f1924c9;hb=1d9764aba8c00754fbf8299e48afbe222245ee3e
- ST的授权：https://github.com/ossrs/srs/wiki/LicenseMixing#state-threads
- GLIBC: https://en.wikipedia.org/wiki/Glibc

如果patch的代码是复制glibc（而非调用），ST可以合并该patch，但合并后的ST须要遵循GPLv2+(只能选择双重许可中的GPLv2+来分发后续版本)。原因：ST采用双重授权，后续版本可以采用MPL或GPLv2+中任一许可证授权，glibc采用LGPL-2.1+授权，LGPLv2.1 允许把代码重新按照 GPLv2 及新版本发布，因此合并该patch的后续版本只能选择GPLv2+.
### 问我们要开源一个Linux内核工具，其中用到了GPL的开源项目。使用木兰协议的哪一个版本比较合适？华为的欧拉是基于Linux内核项目，为什么可以用木兰？
Linux内核的GPL传染性有个特例，可以通过系统调用的方式隔离，这是因为Linux 内核的作者 Linus Torvalds 在Linux内核源码文件中澄清了普通系统调用为非 GPL 的作用范围。这个“Linux内核工具”使用的GPL组件如果不属于上述情况，须要证明该工具不是GPL组件的衍生作品，否则只能用GPL，因为GPL还没有兼容木兰协议。
## 2、关于贡献者协议
### 问：CLA、DCO与开源许可证的区别？
| 特征 | CLA | DCO| 开源license |
| ：----：| ：----：| ：----：| ：----：|
| 签署方式 | 与社区一次性签署 | 每次提交的commit中签署 | 伴随源码 |
| 内容 | 社区或组织可自行定义 | 由Linux Foundation提出并定义，全文仅4条内容 | 由许可证发布方定义 |
| 目标 | 明确参与贡献的有关法律义务，是开源license的补充 | 确保贡献者遵守开源license | 明确开源项目中授予的权利和义务 |

