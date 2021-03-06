## 开源硬件许可证
### 问：常见的开源硬件许可证有哪些？
&emsp;&emsp;OSI关于开源许可证分类的“Special purpose licenses”类别中包含一些用于特殊领域的开源许可证，其中CERN Open Hardware Licence Version 2 - Permissive，CERN Open Hardware Licence Version 2 - Weakly Reciprocal，CERN Open Hardware Licence Version 2 - Strongly Reciprocal是用于开源硬件的开源许可证。
### 问：开源硬件许可证与开源软件许可证的区别？
&emsp;&emsp;开源硬件许可证和开源软件许可证在内容表述上基本相似，但由于硬件和软件的基本表现形式不同，适用于软件的法律概念(如版权和copyleft)不适用于硬件产品以及用于创建它们的文档。因此，硬件许可证和软件许可证的根本不同在于：软件许可证面向的是作品的版权（源码或设计文件），硬件许可证面向的是作品专利（物理设备内置的设计文档，专利在这些文档中起主要作用）。例如，TAPR开放硬件许可证（与GPL类似，旨在保证您共享和创建的自由），明确允许任何人为其在开源硬件中的发明申请专利，但不能阻止第三方执行他们的专利权（允许他人使用其发明），且不能提起专利诉讼。
### 问：开源硬件只能使用开源硬件许可证授权吗？
&emsp;&emsp;广泛意义上的开源硬件包括软件、电路原理图、材料清单、设计图等，它们都可以使用开源协议进行开源。其中：（1）一些开源硬件项目也使用开源软件许可证进行授权，例如开源硬件涉及的软件、固件、可加载到可编程设备中的代码等，面向版权的开源软件许可证更适合；（2）开源硬件许可证主要用于具体的硬件问题（硬件设计，有形的物理设备相关文档），例如CERN 开放硬件许可证，TAPR开源硬件许可证，Free HDL license等。
### 问：CERN Open Hardware Licence Version 2 – Permissive和Apache2.0的对比
相同之处有：   
&emsp;&emsp;（1）允许复制、修改、转让/分发；   
&emsp;&emsp;（2）转让/分发时保留通知；   
&emsp;&emsp;（3）修改后有修改声明；   
&emsp;&emsp;（4）都有免责声明；   
&emsp;&emsp;（5）都不允许专利诉讼；   
主要区别在于：   
&emsp;&emsp;（1）定义。Apache定义的“source” 指进行修改的首选形式，包括但不限于软件源代码、文档源和配置文件。CERN定义的“source”指用于制作（“make”）、测试、使用、转让或销售一个产品（“product”）所需要的设计材料或数字代码；产品（“product”）是指在覆盖源（“source”）的使用、应用或处理过程中产生的任何设备、组件、作品或物体，无论是成品或中间形式。CERN中的“making of product”类似于Apache中的“Derivative Works”。   
&emsp;&emsp;（2）授权。Apache分别授予版权和专利权。CERN没有对版权进行说明，直接表述为授予任何权利，且有专门的专利声明。
