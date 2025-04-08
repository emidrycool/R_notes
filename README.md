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

## 基本操作

### 工作目录

对于文件操作，我们需要设置文件的路径，R 语言可以通过以下两个函数来获取和设置当前的工作目录：

- `getwd()` : 获取当前工作目录
- `setwd()` : 设置当前工作目录

### 赋值变量

最新版本的 R 语言的赋值可以使用左箭头 **<-**、等号 **=** 、右箭头 **->** 赋值。

查看已定义的变量可以使用 **ls()** 函数

`ls.str()`函数【`ls()`和`str()`的组合函数】

`str()`函数可以列出变量的详细信息

`rm()`函数用于删除当前环境中的某个对象

```R
> rm (x)
> x
Error:object 'x' not found
```

删除多个对象：

```R
rm (y,z)
```

删除工作空间中所有对象:

```R
rm (list=ls())
```



### 交互式编程

在命令行中执行 **R** 命令就可以进入交互式的编程窗口：

```R
R
```

执行完这个命令后会调出 R 语言的解释器，我们在 > 符后面输入代码即可。

![img](https://www.runoob.com/wp-content/uploads/2020/07/AA89F11A-9180-4BD0-8A6A-4BE2FD5F1E8E.jpg)

交互式命令可以通过输入 **q()** 来退出：

### 注释

R 语言只支持单行注释，注释符号为 **#**。其实如果有多行注释我们只需要在每一行添加 **#** 号就好了。

## R包

### R包的安装

在[CRAN Task Views](https://cran.r-project.org/web/views/)网站上可以浏览R包的分类

在线安装（推荐：会自动安装依赖的包）

```R
install.package(vcd)
```

源代码安装（适合不能访问互联网的情况）

### R包的使用

```R
install.packages('shiny') # 安装包
library('shiny') # 加载包
```

R软件本身也是由几个独立的包构成的

- base 基础
- datasets 存放R内置的数据集
- utils 工具
- grDevices 绘图设备
- graphics 绘图相关的函数存放于这个包下
- stats 存放与统计相关的函数
- methods 一般定义方法和类
- splines
- stats4
- tcltk

## 数据类型

数据类型指的是用于声明不同类型的变量或函数的一个广泛的系统。

### 变量类型

变量的类型决定了变量存储占用的空间，以及如何解释存储的位模式。

R 语言中的最基本数据类型主要有三种：

- 数字
- 逻辑
- 文本

### 对象类型

按对象类型来分是以下 6 种：

- 向量（vector）
- 列表（list）
- 矩阵（matrix）
- 数组（array）
- 因子（factor)
- 数据框（data.frame)

<img src="https://www.runoob.com/wp-content/uploads/2020/07/52988954-D570-42FD-9CFC-90CD78D361C3.jpg" alt="img" style="zoom:150%;" />

### 变量

向量从数据结构上看就是一个线性表，可以看成一个数组。

`c()`是一个创造向量的函数。

> a = c(3, 4)
> b = c(5, 0)
> a + b
> [1] 8 4

**注意：**R 语言中的"下标"不代表偏移量，而代表第几个，也就是说是从 1 开始的！

#### 列表

列表是 R 语言的对象集合，可以用来保存不同类型的数据，可以是数字、字符串、向量、另一个列表、矩阵、数据框等，当然还可以包含矩阵和函数。

```R
list_data <- list("runoob", "google", c(11,22,33), 123, 51.23, 119.1)
print(list_data)
```

#### 矩阵

这种数据结构很类似于其它语言中的二维数组，但 R 提供了语言级的矩阵运算支持。

以下是一个由 6 个数字元素构成的 2 行 3 列的矩阵：

![img](https://static.jyshare.com/images/mix/61f786996bcfb75972dd77712c90122bc8765269.svg)

R 语言的矩阵可以使用 matrix() 函数来创建，语法格式如下：

```
matrix(data = NA, nrow = 1, ncol = 1, byrow = FALSE,dimnames = NULL)
```

**参数说明：**

- **data** 向量，矩阵的数据
- **nrow** 行数
- **ncol** 列数
- **byrow** 逻辑值，为 FALSE 按列排列，为 TRUE 按行排列
- **dimname** 设置行和列的名称

#### 数组

R 语言数组创建使用 array() 函数，该函数使用向量作为输入参数，可以使用 dim 设置数组维度。

array() 函数语法格式如下：

```R
array(data = NA, dim = length(data), dimnames = NULL)
```

**参数说明：**

- **data** - 指定数组的数据源，可以是一个向量、矩阵或列表。
- **dim** - 指定数组的维度，可以是一个整数向量或一个表示维度的元组，默认是一维数组。例如，**dim = c(2, 3, 4)** 表示创建一个 **2x3x4** 的三维数组。
- **dimnames** - 可选参数，用于指定数组每个维度的名称，可以是一个包含维度名称的列表。

**实例：**

e.g.1

```R
# 创建两个不同长度的向量
vector1 <- c(5,9,3)
vector2 <- c(10,11,12,13,14,15)

# 创建数组
result <- array(c(vector1,vector2),dim = c(3,3,2))
print(result)

#==================执行以上代码输出结果为==================
, , 1

     [,1] [,2] [,3]
[1,]    5   10   13
[2,]    9   11   14
[3,]    3   12   15

, , 2

     [,1] [,2] [,3]
[1,]    5   10   13
[2,]    9   11   14
[3,]    3   12   15
```

e.g.2

```R
# 创建两个不同长度的向量
vector1 <- c(5,9,3)
vector2 <- c(10,11,12,13,14,15)
vector3 <- c(1,2,3,4,5,6,7,8,9)

# 创建数组
result <- array(c(vector1,vector2,vector3),dim = c(3,3,2))
print(result)

#==================执行以上代码输出结果为==================
, , 1

     [,1] [,2] [,3]
[1,]    5   10   13
[2,]    9   11   14
[3,]    3   12   15

, , 2

     [,1] [,2] [,3]
[1,]    1    4    7
[2,]    2    5    8
[3,]    3    6    9
```

#### 因子

R 语言创建因子使用 factor() 函数，向量作为输入参数。

factor() 函数语法格式：

```
factor(x = character(), levels, labels = levels,
       exclude = NA, ordered = is.ordered(x), nmax = NA)
```

参数说明：

- x：向量。
- levels：指定各水平值, 不指定时由x的不同值来求得。
- labels：水平的标签, 不指定时用各水平值的对应字符串。
- exclude：排除的字符。
- ordered：逻辑值，用于指定水平是否有序。
- nmax：水平的上限数量。

**实例：**

```R
x <- c("男", "女", "男", "男",  "女")
sex <- factor(x)
print(sex)
print(is.factor(sex))

#==================执行以上代码输出结果为==================
[1] 男 女 男 男 女
Levels: 女 男
[1] TRUE
```

#### 数据框

数据框（Data frame）可以理解成我们常说的"表格"。

数据框每一列都有一个唯一的列名，长度都是相等的，同一列的数据类型需要一致，不同列的数据类型可以不一样。

R 语言数据框使用 data.frame() 函数来创建，语法格式如下：

```R
data.frame(…, row.names = NULL, check.rows = FALSE,
           check.names = TRUE, fix.empty.names = TRUE,
           stringsAsFactors = default.stringsAsFactors())
```

- **…**: 列向量，可以是任何类型（字符型、数值型、逻辑型），一般以 tag = value 的形式表示，也可以是 value。
- **row.names**: 行名，默认为 NULL，可以设置为单个数字、字符串或字符串和数字的向量。
- **check.rows**: 检测行的名称和长度是否一致。
- **check.names**: 检测数据框的变量名是否合法。
- **fix.empty.names**: 设置未命名的参数是否自动设置名字。
- **stringsAsFactors**: 布尔值，字符是否转换为因子，factory-fresh 的默认值是 TRUE，可以通过设置选项（stringsAsFactors=FALSE）来修改。

**实例：**

```R
table = data.frame(
    姓名 = c("张三", "李四"),
    工号 = c("001","002"),
    月薪 = c(1000, 2000)
    
)
print(table) # 查看 table 数据

#==================执行以上代码输出结果为==================
  姓名 工号 月薪
1 张三  001 1000
2 李四  002 2000
```

### 数据重塑



### Excel



## 贝叶斯网络
