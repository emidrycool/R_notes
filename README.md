# R_notes

## R语言介绍
R 语言是为数学研究工作者设计的一种数学编程语言，主要用于统计分析、绘图、数据挖掘。

## R环境安装
### base

用于基础分发的二进制文件。

### contrib

为过时版本的 R 提供的 CRAN 包的二进制文件（适用于 R < 4.0.x）。

### old contrib

提供的 CRAN 包的二进制文件（适用于 R >= 4.0.x）。

### Rtools

用于构建 R 和 R 包的工具。Rtools是Windows系统下用于编译和安装R语言拓展包（尤其是C/C++/Fortran代码的包）的必要工具集。Rtools是Windows下R包的“编译工具箱”，*无它无法安装或开发含C/C++代码的R包！*

**核心功能**

1. 编译源代码包：许多R包包含非R代码（如C++），需要Rtools编译成Windows可用的二进制文件（.dll）。
2. 开发R包：提供make、gcc、g++等工具，支持R包的本地构建和调试

**主要组件**

- MinGW/GCC：C/C++/Fortran编译器
- GNU Make：自动化构建工具
- 命令行工具（如bash、grep）
- R开发工具（R.exe、Rscript.exe）

### RGui

RGui是R语言自带的基本图形用户界面。它提供了一个简单的窗口，包含R控制台和脚本编辑器。通过RGui，你可以输入和执行R代码，并查看输出结果。

### RStudio

RStudio 是一个 R 编程语言的集成开发环境（IDE）。RStudio是建立在RGui之上的一个更高级的集成开发环境（IDE）。它通过提供更多功能和增强的用户界面，提升了在R中进行编码、调试和运行代码的体验。

这个软件有两种格式：

- RStudio Desktop 作为常规的桌面应用
- RStudio Server 运行在远端服务器上，通过 Web 浏览器来使用。
