# C#笔记

## 1. 介绍

### C# vs .Net

#### 什么是C#和.Net？

C#是编程语言，`.Net`是一个用于开发构建Windows程序的框架，它包括公共语言运行时（Commo Lauguage Runtime，CLR）和类库（Class Library）。

#### C#和.Net有什么用途？

C#作为一门面向对象高级语言，可以让我们很方便的编写各种程序代码。`.Net`则拓展了C#本身的功能，提供更强大的拓展代码以及有效的运行时处理。

参考链接：<br>[什么是 CLR ？ ](https://zhuanlan.zhihu.com/p/68158037)<br>[公共语言运行时 (CLR) 概述 - .NET | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/standard/clr)

### 1.1 C#程序结构

#### 什么是程序结构？

程序结构是一门语言最基础的代码结构，他是一个书写程序的模板框架。其中C#的程序结构包含以下几种：

+ 类（Class）：C#中最基础的结构是类，一个类由属性（字段）及方法（函数）构成，一个类通常负责一个功能。[C# 类型系统中的类。 - C# | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/fundamentals/types/classes)
+ 命名空间（Namespace）：命名空间是一系列相关类的容器，如对图像处理的命名空间、对数据处理的命名空间等。[整理命名空间中的类型 - C# | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/fundamentals/types/namespaces)
+ 程序集（Assembly）：程序集则负责管理相关的命名空间，保证程序安全性，他的物理表现为DLL或exe。
+ 程序应用（Application）：在对所写的代码进行编译连接生成可执行的应用，它通常会包含数个程序集。

#### 程序结构有什么用？

熟悉程序结构能让我们对自己所写程序的构成有一个细致地了解，并且在很大程度上也对我们编写程序时不同代码所书写的位置起到一种规范性作用。

### 1.2 Visual Studio中的项目结构

#### 什么是项目结构？

如同程序结构，每个项目也有他自己的一个功能分类的结构，对我们代码所处位置、资源文件所处位置等进行了详细划分。Visual Studio中的项目划分为了以下几个板块：

+ 解决方案：项目结构中最顶层的为解决方案，解决方案只是一个容器，用于包含一个或多个相关项目，以及生成信息、Visual Studio 窗口设置和不与特定项目关联的任何杂项文件。
+ 项目：项目包含所有编译为可执行文件、库或网站的文件。 这些文件可以包括源代码、图标、图像、数据文件等。 除此之外，项目还包含编译器设置以及程序与各种服务或组件通信可能需要的其他配置文件。
+ 项目属性配置（Properties）：该目录包含了对项目的相关属性设置，其中对项目的描述、版本等内容保存在`Assemblylnfo.cs`文件中。
+ 引用（References）：它包含了一系列项目中所使用的程序集依赖。
+ 项目配置（App.config）：包含对项目的设置如编译版本等。
+ 代码文件`.cs`：即我们进行代码书写的地方。

#### 一定要按照这个板块划分进行程序书写吗？

在编写程序时建议按照统一规范进行划分编码，这样程序结构更具有规范性，也更加方便我们自己和他人读懂项目。

参考链接：[什么是 Visual Studio 解决方案和项目？ - Visual Studio (Windows) | Microsoft Learn](https://learn.microsoft.com/zh-cn/visualstudio/ide/solutions-and-projects-in-visual-studio?view=vs-2022)

### 1.3 一个代码文件的基本结构

#### 什么是代码的基本结构？

代码文件的基本结构是书写该语言代码的基础框架，他对我们在什么地方可以写什么样的代码进行了详细划分。一个代码文件模板形如以下样式：

```c#
//命名空间引用
using System;	//C# 应用程序的基本命名空间，包含了C#程序所需的所有基本类和基类

//命名空间，名称具有唯一性，不可重复，在同一个命名空间内可以访问该命名空间的所有类
namespace WindowsApp1	//命名空间，名称为WindowsApp1
{
    //C#类
    class Program
    {
        //函数，包含访问权限、返回值、函数名、参数等
        static void Main(string[] args)	//主函数，应用程序入口函数
        {
        }
    }
}
```

#### 以定要按照这个结构书写代码吗？

除开部分可选内容外，其他必须严格按照该结构进行书写，否则会出现报错编译失败等问题。

参考链接：[C# 程序结构 | 菜鸟教程 (runoob.com)](https://www.runoob.com/csharp/csharp-program-structure.html)

### 1.4 标识符

#### 什么是标识符？

标识符是我们对函数、变量等命名的符号名称，它指向该函数或变量在硬盘中的具体地址以便于我们对它进行操作。

#### 怎么对标识符进行命名？

C#中常用的标识符命名方法包含两种：

+ 小驼峰命名：作为标识符的单词首个单词全小写，后续单词首字母大写，通常用于给变量命名，如`firstName`。
+ 大驼峰命名：所有单词首字母均大写，通常用于命名常量，如`FirstName`。

### 1.5 关键字

#### 什么是关键字？

C#关键字是C#中预定义的保留字符，它代表了C#中的一些编译功能或语法结构。

#### 关键字可以作为标识符使用吗？

关键字代表着编程语言的一些编译功能和语法，从另一个角度讲他也是一个固定的语法或功能的标识符，所以它不能直接作为我们编码时的标识符使用（即对函数、类等的命名），例如在命名时对一个整型不能直接命名为`int`，但我们可以命名为`intValue`或`@int`等。

具体关键字参考：[C# 关键字 | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/)



## 2. C#变量（Variables）与常量（Constants）

### 2.1 变量与常量的基本概念

#### 什么是变量？

变量是我们手动名命名的一个供程序操作的存储区的名字，是用于存储和表示数据的标识符。每个变量都有一个特定的类型，类型决定了变量的内存大小和布局，范围内的值可以存储在内存中，可以对变量进行一系列操作。

#### 如何使用变量？

创建变量的基本语法为`(访问权限) 变量类型 变量名( = 初始值);`，具体语法见后文。注意，标识符不能以数字开头，不能在其中包含空格。

在声明变量时，您需要指定变量的类型，并且可以选择性地为其分配一个初始值。

参考链接：[C# 变量 | 菜鸟教程 (runoob.com)](https://www.runoob.com/csharp/csharp-variables.html)

#### 什么是常量？

常量也是一个指向存储区的标识符，不同的是它所指向的存储区无法被修改，只允许读取。

#### 如何定义常量？

常量与变量基本相同，但它的值必须在创建时进行赋值，且在程序运行时不可以被修改，只能在编码时手动进行修改。

常量创建的基本语法为在变量类型前加上`const`关键字。

参考链接：[C# 常量 | 菜鸟教程 (runoob.com)](https://www.runoob.com/csharp/csharp-constants.html)

### 2.2 常见数据类型

#### 什么是数据类型？

在自然语言中我们详细的划分了语句、文字、数字、符号等，在计算机中也对这些内容进行了详细的划分，便于计算机理解我们所需要或所使用的数据是什么、怎么处理等等的问题，这就是数据类型。

#### 必须使用吗？

在C#中，数据类型无处不在，基础的输入输出使用的`Console`是特殊数据类型`类class`，控制台打印的文字是`字符串String`，在编码中我们随时都在跟各种各样的数据打交道，不用是不行滴。

#### 有哪些数据类型？

常用数据类型分为以下几种：

##### 整型：代表自然语言中的整数

| C#类型 | .Net类型 | 描述                | 范围                                                         | 默认值 |
| ------ | -------- | ------------------- | ------------------------------------------------------------ | ------ |
| sbyte  | SByte    | 8 位有符号整数      | -2^7^~2^7^-1（-128 到 127）                                  | 0      |
| byte   | Byte     | 8 位无符号整数      | 0~2^8^-1（0 到 255）                                         | 0      |
| short  | Int16    | 16 位有符号整数类型 | -2^15^~2^15^-1（-32,768 到 32,767）                          | 0      |
| ushort | UInt16   | 16 位无符号整数类型 | 0~2^16^（0 到 65,535）                                       | 0      |
| int    | Int32    | 32位有符号整数类型  | -2^31^~2^31^-1（-2,147,483,648 到 2,147,483,647）            | 0      |
| uint   | UInt32   | 32位无符号整数类型  | 0~2^32^（0 到 4,294,967,295）                                | 0      |
| long   | Int64    | 64为有符号整数类型  | -2^63^~2^63^-1（-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807） | 0      |
| ulong  | UInt64   | 64为无符号整数类型  | 0~2^64^（0 到 18,446,744,073,709,551,615）                   | 0      |

##### 浮点型：代编自然语言中的小数

| C#类型  | .Net类型 | 描述                                 | 范围                                    | 默认值 |
| ------- | -------- | ------------------------------------ | --------------------------------------- | ------ |
| float   | Float    | 32 位单精度浮点型                    | -3.4 x 1038 到 + 3.4 x 1038             | 0.0f   |
| double  | Double   | 64 位双精度浮点型                    | (+/-)5.0 x 10-324 到 (+/-)1.7 x 10308   | 0.0d   |
| decimal | Decimal  | 128 位精确的十进制值，28-29 有效位数 | (-7.9 x 1028 到 7.9 x 1028) / 100 到 28 | 0.0m   |

注意：浮点型直接赋值数字时，数字后面必须加上对应类型的标识符（f，d，m），否则会按照默认类型double处理。

##### 布尔类型：用于判断逻辑正误的数据类型，常用于逻辑判定语句中

| C#类型 | .Net类型 | 描述                   | 范围                | 默认值     |
| ------ | -------- | ---------------------- | ------------------- | ---------- |
| bool   | Boolean  | 布尔值（占1个字节8位） | True和False（1和0） | False（0） |

##### 字符型：代表我们自然语言中的单个文字

| C#类型 | .Net类型 | 描述               | 范围               | 默认值 |
| ------ | -------- | ------------------ | ------------------ | ------ |
| char   | Char     | 16 位 Unicode 字符 | U +0000 到 U +ffff | ‘/0’   |



参考链接：[Types - C# language specification | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/language-specification/types#835-simple-types)

### 2.3 数据溢出

#### 什么是数据溢出？

数据溢出是由于计算机数据存储问题导致的在操作数据时产生的数据越界。

#### 计算机中数据是怎么存储的？

在计算机中，数据并非像我们肉眼所见的形式进行存储，而是通过二进制进行储存，例如前面所提到的`byte`类型，自然语言中它的大小为 0 到 255 ，但是更加符合计算机中的形式表达应该为 `00000000`到`11111111`。

计算二进制数的值的方式即为从右到左依次记为2的n次方，其中n为位数-1，若该位为1则进行相加，不为1则不进行计算，例如`1010`他的值为0\*2^0^+1\*2^1^+0\*2^2^+1\*2^3^，即10.

而对于有符号类型数据，最高位为符号位（即最左边的二进制数），若为1则为负数，而他的值的计算则涉及到补码及反码的知识（[二进制数的原码、反码、补码（详解）](https://blog.csdn.net/u011429167/article/details/129264625)）。

#### 如何理解溢出？

因为在计算机中数据长度是固定的，所以在已经达到最大值时若我们还对他进行`+`操作，将会导致数据溢出，例如byte最大为`11111111(255)`，如果在对其进行+1操作，它的值理应变为`1 00000000`，但因为长度仅有8位，所以会将高位抛弃，数值变为`00000000`。

==数据溢出将会对内存产生严重影响，严重时会导致程序及系统崩溃。==

#### 如何检查是否存在数据溢出？

可以使用**`checked`检测数据溢出**。因为在编译时，编译器并不会检测到数据的溢出（溢出发生在执行到该语句的时候），所以如果不确定自己的操作是否会导致数据溢出的话，可以使用`checked`语句包裹操作的代码，他将会在发生溢出时抛出异常。

```c#
byte data = 255;
checked
{
    data += 1;	//发生未经处理的异常：System.OverflowException:“Arithmetic operation resulted in an overflow.”
}
```

### 2.4 类型转换（Type Conversion）

#### 什么是类型转换？

在实际编码中进行数据处理等行为时，通常会存在将小数作为整数处理、将字符串拆分为单个字符处理的情况，这些情况下的转换就是类型转换。

#### 有哪些类型转换？

在编码过程中，通常会有对数据类型进行转换的情况，其中分为三类：隐式转换（Implicit Type Conversion）、显示转换（Explicit Type Conversion）、不兼容数据类型转换（Non-compatible Types Conversion）。

##### 隐式转换（Implicit Type Conversion）

**什么是隐式转换？**

隐式转换是在不经意之间发生的转换，如我们创建了一个short变量，而在后续操作中我们将它与一个int变量进行运算并复制给int变量时，发生了将short隐式转换为int的过程。

**通常什么情况下会发生隐式转换？**

+ 小数据转换为大数据：在发生隐式转换时，如果将小数据转换为大数据（如short转换为int），编译器通常不会进行提示，而是将小数据所包含的数直接赋值给大数据类型，而对于缺少的高位数字则全部补为小数据的符号位。

  ```c#
  short a = 255;
  int b = a;	//b的值为255，二进制为00000000 00000000 00000000 01111111
  ```

+ 大数据转换为小数据：将一个大数据转换为小数据，编译器将直接报错，除非我们使用显式强制数据类型转换。

  ```c#
  int b = int.MaxValue;
  short c = b;//错误：无法将类型“int“隐式转换为"short”。存在一个显式转换(是否缺少强制转换?)
  ```

##### 显示转换（Explicit Type Conversion）

**什么是显示转换？**

显式转换也叫强制数据转换，他是我们在需要处理数据时手动进行的数据类型转换。

**为什么要使用强制数据转换？**

在实际开发中，我们可能需要将某一个数据强制转换为一个较小数据类型，这个时候使用强制数据转换可以避免编译报错，同时也能得到我们预期的结果。

**如何进行强制转换？**

强制转换在被转换类型前用括号写入目标转换类型即可，举例如下：

```c#
int b = int.MaxValue;
short c = (short)b;//编译通过，可以运行
```

但是需要注意的是，强制转换后小数据只会截取对应位数的二进制码，比如上面的代码中，`c`将会被赋值为-1，因为b的二进制码为`01111111  11111111 11111111 11111111`，而转换后为`11111111 11111111`，作为补码计算后结果为-1.

##### 不兼容数据类型转换（Non-compatible Types Conversion）

**什么是不兼容数据类型？**

不兼容类型即本身在计算机中存储的方式有很大不同的类型，例如字符和整型，字符是存储的Unicode编码，而整型则存储的对应二进制，这类数据在进行转换的时候可能会出现不可控情况，所以被称为不兼容数据类型。

**如何进行不兼容的类型的转换？**

进行不同类型转换时所使用的方法通常会有很大的区别，下面是将字符串转换为浮点数的方法，实际编码中需要自行修改为对应的转换语句：

```c#
//double dPi = Convert.ToDouble(pi);
float dPi = float.Parse(pi);
Console.WriteLine(dPi);;
```

### 2.5 操作符

**什么是操作符？**

顾名思义，操作符就是对数据进行操作的符号，如对数据进行赋值、加减乘除运算等等。

**操作符的类型有哪些？如何进行使用？**

操作符类型有赋值运算符、算术运算符、比较运算符、逻辑运算符及位运算符，他们具体描述和用法见下：

#### 赋值运算符（Assignment Operators）

| 运算符 | 举例   | 解释                         |
| ------ | ------ | ---------------------------- |
| =      | a = b  | 基础赋值运算符，将b的值赋给a |
| +=     | a += b | 等同于 a = a + b             |
| -=     | a -= b | 等同于 a = a - b             |
| *=     | a *= b | 等同于 a = a * b             |
| /=     | a /=b  | 等同于 a = a / b             |

#### 算术运算符（Arithmetic Operators）

| 运算符 | 举例    | 解释                                                         |
| ------ | ------- | ------------------------------------------------------------ |
| +      | a + b   | 加法运算符，将`a`和`b`进行做加法                             |
| -      | a - b   | 减法运算符，将`a`和`b`进行做减法                             |
| *      | a * b   | 乘法运算符，将`a`和`b`进行做乘法                             |
| /      | a / b   | 除法运算符，将`a`和`b`进行做除法，最终会舍弃余数，如`5 / 3 `为`1` |
| %      | a % b   | 取余运算符，将`a`和`b`进行取余操作，只保留余数，如`5 % 3 `为`2` |
| ++     | a++,++a | 递增运算符，等同于`a = a + 1`                                |
| --     | a--,--a | 递减运算符，等同于`a = a - 1`                                |

前置递增/递减和后置递增/递减：

+ 代码书写区别：前置递增/递减和后置递增/递减在书写上的区别表现为前置运算符在被操作数之前，后置运算符在操作数之后。

+ 单独书写运行结果：若果单独书写前置或后置运算符，其效果相同，均为递增或递减。

+ 赋值中的前置与后置：在赋值运算中，前置运算会先进行递增/递减操作，再进行赋值，后置运算则会先进行赋值，在进行递增/递减操作，举例如下：

  ```c#
  int a = 1;
  int b = a++;//后置递增，先进行赋值后递增，结果为b=1，a=2
  ```

  ```c#
  int a = 1;
  int b = --a;//后置递减，先进行递减后赋值，结果为b=0，a=0
  ```

#### 比较运算符（Comparison Operators）

| 运算符 | 举例   | 解释                                                        |
| ------ | ------ | ----------------------------------------------------------- |
| ==     | a == b | 比较a和b是否相等，若相等则值为`True`，不相等则值为`False`   |
| !=     | a != b | 比较a和b是否不相等，若不相等则值为`True`，相等则值为`False` |
| >      | a > b  | 比较a与b的大小，若a大于b则为`True`，否则为`False`           |
| >=     | a >= b | 比较a与b的大小，若a大于等于b则为`True`，否则为`False`       |
| <      | a < b  | 比较a与b的大小，若a小于b则为`True`，否则为`False`           |
| <=     | a <= b | 比较a与b的大小，若a小于等于b则为`True`，否则为`False`       |

#### 逻辑运算符（Logical Operators）

| 运算符 | 举例     | 解释                                                         |
| ------ | -------- | ------------------------------------------------------------ |
| &&     | a && b   | 逻辑与，若a和b同时为`True`则结果为`True`，否则为`False`      |
| \|\|   | a \|\| b | 逻辑或，若a和b有任何一个为`True`则结果为`True`，否则为`False` |
| !      | !a       | 逻辑非，若a为`True`则结果为`False`，否则为`True`             |

#### 位运算符（Bitwise Operators）

位运算符是较为底层的运算操作符，直接针对二进制位进行的操作。

| 运算符 | 举例   | 解释                                                         |
| ------ | ------ | ------------------------------------------------------------ |
| &      | a & b  | a和b按位与运算，若对应二进制位全为1则结果中该位为1，如`1010 & 0110 = 0010` |
| \|     | a \| b | a和b按位或运算，若对应二进制位有一个为1则结果中该位为1，如`1010 | 0110 = 1110` |
| ^      | a ^ b  | a和b按位异或运算，若对应二进制位两位不相同则结果中该位为1，如`1010 ^ 0110 = 1100` |

#### 三目运算符（Ternary Operator）

三目运算符非常适用于对于一个结果为`True`或`False`时分别对应一种返回值的情况，他的基础语法为`a ? b : c`，含义为当`a`为`True`则返回结果为`b`，否则则为`c`。下面是一个简单示例：

```c#
string res = 1 > 2 ? "1是大于2的" : "1小于2";	//最终res将被赋值为"1小于2"
```

#### 运算优先级

**什么是运算优先级？**

当同一个式子中含有多个操作符的时候，存在运算优先级的概念，在运行时会先执行高优先级运算，后执行低优先级运算，在同级运算中，执行顺序为从左到右依次执行。例如：

+ `1 & 2 - 3`计算时，减法优先度高于与运算，所以结果为1.
+ `1 + 2 * 3 - 4`计算时，乘法计算优先度高于加法，所以先进行乘运算，再依次进行其他运算，结果为3.

**如何手动改变运算顺序？**

想要更改计算顺序，可以手动对其添加括号（圆括号或方括号），程序将会优先执行括号中的内容，例如：

+ `(1 & 2) - 3`计算时，将会优先执行与运算，后执行减法运算结果为-3.
+ `(1 + 2) * 3 - 4`计算时，将会先执行加法运算，结果变为5.

运算优先级参考链接：[C# 运算符 | 菜鸟教程 (runoob.com)](https://www.runoob.com/csharp/csharp-operators.html)



## 3. 特殊数据类型

### 3.1 值类型（Value Types）与引用类型（Reference Types）

C#中数据类型分为值类型和引用类型，在前面所使用到的如`int`、`float`等均为值类型，而类（`class`）、数组（`array`）等则属于引用类型。

#### 概述：什么是值类型和引用类型？

**值类型**：值类型是指我们进行声明时变量标识符指向的是该类型的具体值的类型，他的数据存储于栈区。

值类型包括基本数据类型（如`int`、`float`等）和结构体（`struct`），在赋值和函数传参时将会传入一个自身的新的副本，对参数的操作将不会直接作用于原来的数据。

**引用类型**：引用类型是我们进行变量声明时标识符指向的是该类型数据所在堆地址的数据类型。

引用类型包括类（`class`）、接口（`interface`）、字符串（`string`）、数组（`array`），在赋值和传参时将会传入对物理内存的引用而不是本身的副本，所以对参数的修改会直接影响到原本的数据。

#### 什么是堆栈？

栈是由系统自动分配的一片内存，它具有容量小访问快的特点。

堆是由我们手动申请，它的容量大但是访问速度完全比不上栈内存访问速度，在C/C++语言中，堆内存必须要我们手动进行释放，在C#中由CLR中的垃圾回收机制进行自动释放或手动调用GC（垃圾回收器）进行释放。

#### 值类型和引用类型的区别是什么？

**值类型：**

+ 值类型存储于计算机栈区（少数值太大的情况会存储于堆区），由系统自动分配内存，在出现内存溢出的情况时系统将会舍弃掉溢出部分。
+ 值类型变量存储的为具体数据。
+ 值类型在传参时会构建一个新的副本，副本的值等于该变量，对参数的改变并不会修改原来变量的值。

**引用类型：**

+ 引用类型存储于计算机堆区，需要我们手动告诉计算机分配内存，如果出现内存溢出将会污染损坏堆区。
+ 引用类型变量存储的是该类型实例的引用，而非实例本身。
+ 引用类型在传参时会直接传入对实例的引用，对该参数引用进行修改会直接影响到原本的数据。

```c#
Console.WriteLine("值类型变量赋值操作");
int a = 3;
int b = a;
b -= 1;
Console.WriteLine($"a:{a},b:{b}");	//a:3,b:2
Console.WriteLine("引用类型变量赋值操作");
Person person1 = new("小明");
Person person2 = person1;
person2.name = "小红";
Console.WriteLine($"person1.name:{person1.name},person2.name:{person2.name}");	//person1.name:小红,person2.name:小红
```

参考链接：<br>[值类型 - C# reference | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/value-types)<br>[引用类型 - C# reference | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/reference-types)<br>[c# 值类型和引用类型的区别-CSDN博客](https://blog.csdn.net/lizhong2008/article/details/138910120)

### 3.2 结构体（struct）

#### 什么是结构体？

结构体是一种特殊的值类型数据类型，它的基本用法与类相近，但是它所占用的内存比类对象要小，所以在专注于数据存储而不是操作的情况下采用结构体将会更加节省内存。

#### 结构体和类的区别？

- struct 是值类型，class 是引用类型
- struct 不能被继承，class 可以被继承
- struct 默认的访问权限是public，而class 默认的访问权限是private.
- struct总是有默认的构造函数，即使是重载默认构造函数仍然会保留。这是因为struct的构造函数是由编译器自动生成的，但是如果重载构造函数，必需对struct中的变量全部初始化。并且struct的用途是那些描述轻量级的对象，例如点、线等，并且效率比较高。class在没有重载构造函数时有默认的无参数构造函数，但是一被重载，默认构造函数将被覆盖。
- struct的new和class的new是不同的。struct的new就是执行一下构造函数创建一个新实例再对所有的字段进行复制。而class则是在堆上分配一块内存然后再执行构造函数，struct的内存并不是在new的时候分配的，而是在定义的时候分配

#### 如何使用结构体？

结构体定义语法如下：

```c#
struct Point
{
    public int x;
    public int y;
    public string getPointString() { return $"({x},{y}"; }
}
```

在使用时，首先通过`<struct_type> name = new();`进行声明，通过`.`操作符进行内部数据及函数的调用：

```C#
 Point p = new Point();
 p.x = 10;
 p.y = 20;
 Console.WriteLine(p.getPointString());//(10,20)
```



参考链接：<br>[结构类型 - C# reference | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/struct)<br>[教程：使用 struct 数据类型和 ref 语言功能减少内存分配。 - C# | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/advanced-topics/performance/ref-tutorial#change-classes-to-structs)<br>[【C#】Struct和Class区别 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/358825256)

### 3.3 字符串（string）和StringBuilder

#### 什么是字符串？

+ 字符串是一个用于存储多个有序字符（`char`）的只读集合（即在创建后无法进行修改），他的赋值拼接等操作都会新创建一个字符串并将内容写入这个字符串，再更改变量名的指向，并不会修改原来字符串实例的值。
+ 是一个类，所以它是一个具有值类型特征的特殊的引用类型。
+ 没有最大容量限制，即在创建时可以书写任意长度的字符。与其他语言中的字符串不同，他并不会以`\0`结尾。

#### 如何声明字符串？

字符串声明语法如下：

```C#
string str = "Hello World!";
```

#### 什么是转义字符？

转义字符是将一些编译器规定的功能性符号转换为实际可显示的普通符号或将普通符号转换为具有系统功能的符号的字符。

#### 为什么使用转义字符？

在定义字符串时，对于一些特殊符号（如`\`、`''`、`“”`等），我们无法将其直接填入字符串的值当中，这是需要使用转义字符。

#### 转义字符如何使用？有哪些转义字符？

转义字符的基本使用方法即为在需要填入的符号前加上`\`即可，常见的转义字符如下：

| 转义序列 | 字符名称   | Unicode 编码 |
| :------- | :--------- | :----------- |
| \\'      | 单引号     | 0x0027       |
| \\"      | 双引号     | 0x0022       |
| \\\      | 反斜杠     | 0x005C       |
| \0       | null       | 0x0000       |
| \b       | Backspace  | 0x0008       |
| \n       | 换行       | 0x000A       |
| \r       | 回车       | 0x000D       |
| \t       | 水平制表符 | 0x0009       |

例如我们想要在字符串中书写`他对我说："你这个年龄段怎么睡得着的"`，直接填写进字符串会报错，因为他会将内容中的双引号视为字符串结束的标志：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240903145055064.png" alt="image-20240903145055064" style="zoom:50%;" />

而如果我们给他加上`\`，他则会被视为一个普通字符，不会报错并且能够正常输出：

```c#
string str = "他对我说：\"你这个年龄段怎么睡得着的\"";
Console.WriteLine(str);
```

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240903145248029.png" alt="image-20240903145248029" style="zoom:67%;" />

而如果想要禁用转义字符，只需要在字符串定义时双引号前加上`@`即可，例如在上面可以运行的字符串定义前加上`@`，将会再次报错：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240903145455182.png" alt="image-20240903145455182" style="zoom:50%;" />

#### 字符串插入及拼接

**为什么要进行字符串的插入或拼接？**

字符串在声明后不一定一直不变，在实际开发中可能经常要对字符串进行操作，这事就会涉及到字符串的拼接插入等。

**有哪些方法进行拼接插入操作？如何进行拼接插入？**

**方法一`+`拼接：**虽然字符串不是值类型，但他也可以使用`+`和`+=`操作符，并且它可以拼接非字符类型的内容，具体效果如下：

```c#
string str2 = "name:" + "zhangsan" + " age:" + 18;	//拼接结果为str2 = "name:zhangsan age:18"
```

**方法二`Format`函数：**String类提供了一个`Format`静态函数(`public static string Format( string format, Object arg0 )`)让我们可以对字符串进行插入的操作其中`format`为被插入字符串，`arg0`则为插入的数据列表（可以为任何类型，在插入时都会转换为String再进行插入），需要注意的是，`format`字符串中被插入位置必须要用花括号和索引进行占位，且但索引值大于后面列表时程序将会报错，小于列表时未使用的数据将会直接舍弃（索引从前往后不一定必须为从0到n）：

```c#
//下面的str3拼接后的值为 姓名：张三, 年龄：18, 性别：男
//后面列表中第四个”666“因为并没有被索引应用，所以被直接舍弃
string str3 = string.Format("姓名：{0}, 年龄：{2}, 性别：{1}", "张三", "男", 18, 666);

//直接使用控制台输出该内容时，可以直接舍弃string.Format，输出结果相同
Console.WriteLine("姓名：{0}, 年龄：{2}, 性别：{1}", "张三", "男", 18)；
```

**方法三`Concat`函数拼接：**`Concat`函数同样是String类中的一个静态函数，他会将参数中的数据依次进行拼接：

```c#
string str4 = string.Concat("姓名：", "张三", " 年龄：", 18);	//姓名：张三 年龄：18
```

**方法四`$`字符格式化：**在`format`中使用索引进行占位，但并不便于我们直接阅读，如果索引顺序较为混乱，在出现错误是将会难以定位错误位置，而`$`拼接将直接使用花括号`{}`和前面的变量名进行占位，便于阅读：

```c#
string name = "张三";
char sex = '男';
string str5 = $"姓名：{name}，性别：{sex}";	//姓名：张三，性别：男
```

**方法五`join`拼接：**该函数同样为静态函数，`public static string Join( string separator, string[] value )`，其中，`separator`为拼接时没个拼接字段之间的分隔符号，`value `为需要进行拼接的字符串数组：

```c#
int[] num = { 1, 2, 3, 4, 5 };
string str = string.Join(",", num); //1,2,3,4,5
```

#### 字符串的一些特殊方法

**ToUpper()**：将字符串中所有小写字母转换为大写字母。

**ToLower()**：将字符串中所有大写字母转换为小写字母。

**Trim()**：删除字符串中的前置和后置空格。

**LastIndexOf(char/str)**：返回最后一次出现该字符或字符串的位置索引。

**Replace(char/str， char/str)**：将指定字符或字符串替换为另一字符或字符串。

**String.IsNullOrEmpty(str)**：判断字符串是否为空或`null`。

**String.IsNullOrWhiteSpace(str)**：判断字符串是否为`null`或空格。

**Split(char)**：以某一字符为标准将字符串进行拆分。

**Substring(startIndex[,length])**：获取字符串从起始的索引（到目标长度）的子字符串。

参考链接：<br>[C# 字符串（String） | 菜鸟教程 (runoob.com)](https://www.runoob.com/csharp/csharp-string.html)<br>[字符串 - C# 编程指南 | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/programming-guide/strings/)

#### 什么是StringBuilder？

`StringBuilder`是`.Net`提供的可以在不新建新的字符串而对字符串进行修改的公共类，他位于`System.Text`中，本质是一个封装好的动态字符数组。

#### 为什么需要StringBuilder？

C#原本的字符串是一个常量，不能进行修改，再进行对字符串的大量操作时将会产生大量内存垃圾，引起程序卡顿，使用`Stringbuilder`可以避免垃圾过多。

#### StringBuilder如何分配空间/为什么相比于string更节省内存？

`StringBuilder`类似于动态字符数组，在最开始就额外分配了多余空间供我们使用，在空间不足时会申请当前空间一倍的新空间并将当前数组搬入新内存。

相比于`string`每次修改都会产生内存垃圾，`StringBuilder`则只会在容量不足时产生垃圾，频率更低，所以一般情况下更加节省空间。

#### `StringBuilder`有哪些函数，如何使用？

在使用时，首先要**引入命名空间**`System.Text`，并声明`StringBuilder`变量，申请空间。

**获取容量**：通过`Capacity`属性获取当前`StringBuilder`对象的容量。

**获取字符串长度**：通过`Length`属性直接获取长度。

**增加字符**：`Append(str/char[,repeat])`，将指定字符（串）添加到末尾（并重复）。

```c#
var str = new StringBuilder("test");
str.Append(" StringBuilder");		//str变为 "test StringBuilder"
str.Append('*', 6);					//str变为 "test StringBuilder******"
```

**插入字符**：`Insert(index, str)`在指定位置插入字符：

```c#
str.Insert(0, "Reihi is ");			//str变为 "Reihi is test StringBuilder******"
```

**删除字符**：`Remove(startIndex, length)`删除指定位置指定长度的字符：

```c#
str.Remove(27, 6);					//str变为 "Reihi is test StringBuilder"
```

**获取指定索引字符**：`StringBuilder`不能直接获取某一字符所在位置，只能通过索引器获得指定位置字符：

```c#
char c = str[0];					//c 为 `R`
```

**修改字符**：可以直接通过索引器修改对应字符的值。

**替换字符**：使用`Replace(str1, str2)`将包含的str1替换为str2：

```c#
str.Replace("Reihi", "泠曦");			//str变为 "泠曦 is test StringBuilder"
```

**清除字符串**：通过`Clear()`清空所有字符：

```c#
str.Clear();						//str 被清空，不包含任何内容
```



### 3.4 枚举（Enum）

#### 什么是枚举？

+ 枚举类型是一组被命名的整型常量的集合，在默认情况下它的大小从0开始并且按照文本顺序依次+1，如果有需要也可以手动显式给它赋值，后续未赋值常量将会依次+1（无情的+1机器）。
+ 枚举声明通常在`namespace`语句块或`class`语句块中，不可以声明在函数体中。
+ 在声明的枚举类型中不可以添加方法。

#### 为什么要使用枚举？

在编码过程中，我们可能需要对一系列的状态、类别等进行判断，如果单纯使用数字并不利于我们理解，而如果单独创建常量并不便于我们在后续需要对某一些类型进行删改时的操作，定义枚举可以使这些类型常量处于一个固定的集合内，并且便于我们查找和删改。

#### 如何声明枚举类型？

声明的基本语法如下：

```c#
enum <enum_name>
{ 
    enumeration list 
};
```

例如，我们声明一个类型为`Season`的枚举：

```c#
enum E_Season
{
    Spring,	//默认值为0
    Summer,	//默认值为1
    Autumn,	//默认值为2
    Winter	//默认值为3
}
```

#### 如何创建枚举变量？

声明枚举变量与声明值类型变量一致，语法如下：

```c#
<声明的枚举名> <变量名> = <初始值>; 
```

例如，声明一个名称为`season`的`E_Season`枚举变量，并且打印他直接输出的值和转换为整型后输出的值：

```c#
E_Season season = E_Season.Spring;
Console.WriteLine(season);		//输出结果为 Spring	(默认调用toString()方法)
Console.WriteLine((int)season);	//输出结果为 0
```

#### 枚举相关的数据类型转换？

因为枚举本身为一个整型常量集合，所以它可以直接显示转换为相关的值类型：

```c#
float fs = (float)season;
short ss = (short)season;
```

同时也可以将其转换为字符串，只需要使用`toString()`方法：

```c#
string str = season.ToString();
```

额如果有对应的一个字符串，我们也可以将其转化为枚举变量，语法如下：

```c#
<enumType> <name> = (<enumType>)Enum.Parse(typeof(<enumType>), <string>);
```

例如将`"Winter"`转换为`E_Season`枚举变量：

```c#
E_Season season = (E_Season)Enum.Parse(typeof(E_Season), "Winter");
```

参考链接：<br>[枚举类型 - C# reference | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/enum)<br>[C# 枚举（Enum） | 菜鸟教程 (runoob.com)](https://www.runoob.com/csharp/csharp-enum.html)

#### 用枚举实现摩斯电码转码

```C#
namespace MorseCode
{
    internal class MorseCode
    {
        enum E_MorseCode
        {
            dh = 'A', hddd = 'B', hdhd = 'C', hdd = 'D', d = 'E', ddhd = 'F', hhd = 'G', dddd = 'H', dd = 'I', dhhh = 'J', hdh = 'K', dhdd = 'L', hh = 'M', hd = 'N', hhh = 'O', dhhd = 'P', hhdh = 'Q', dhd = 'R', ddd = 'S', h = 'T', ddh = 'U', dddh = 'V', dhh = 'W', hddh = 'X', hdhh = 'Y', hhdd = 'Z', dhhhh = '1', ddhhh = '2', dddhh = '3', ddddh = '4', ddddd = '5', hdddd = '6', hhddd = '7', hhhdd = '8', hhhhd = '9', hhhhh = '0', ddhhdd = '?', hddhd = '/', hdhhdh = '(', hddddh = '-', dhdhdh = '.',
            hdhdh = '@',//开始符
            dddddd = '\t',//错误符
            dddhd = '\0',//结束符
            e = ' ',//空格
        }

        /// <summary>
        /// 将单个摩斯电码转换为对应字符
        /// </summary>
        /// <param name="code">单个摩斯电码的字符串形式，可以为".-"或"dh"格式</param>
        /// <returns>转换后的字符</returns>
        public static char GetCharOfMorseCode(string code)
        {
            return (char)(E_MorseCode)Enum.Parse(
                typeof(E_MorseCode),
                code.Replace('.', 'd').Replace('-', 'h').Replace('=', 'e'));
        }

        /// <summary>
        /// 将字符转换为摩斯电码
        /// </summary>
        /// <param name="c">
        /// 需要转换的字符其中：<br/>
        /// 开始符为 '@'<br/>
        /// 错误符为 '\t'<br/>
        /// 结束符为 '\n'
        /// </param>
        /// <returns>对应摩斯电码字符串 (".-"格式)</returns>
        public static string GetMorseCodeOfChar(char c)
        {
            return ((E_MorseCode)((int)c)).ToString()
                .Replace('d', '.')
                .Replace('h', '-')
                .Replace('e', '=');
        }

        /// <summary>
        /// 将指定字符分割的摩斯电码翻译为语句
        /// </summary>
        /// <param name="code">摩斯电码字符串</param>
        /// <param name="split">分隔符（可以有多个分隔符，默认为空格）</param>
        /// <returns>翻译后的句子</returns>
        public static string GetSentenceOfMorseCode(string code, params char[] split)
        {
            if (split == null || split.Length == 0) split = [' '];
            var codeList = code.Split(split);
            var resultList = new List<char>();
            bool flag = false;
            foreach (string c in codeList)
            {
                var t = GetCharOfMorseCode(c);
                if (t == '(')
                {
                    if (flag)
                    {
                        flag = false;
                        resultList.Add(')');
                        continue;
                    }
                    else
                        flag = true;
                }
                resultList.Add(t);
            }
            return string.Join("", resultList.ToArray()).Replace('e', ' ');
        }

        /// <summary>
        /// 将语句转换为对应摩斯电码
        /// </summary>
        /// <param name="sentence">需要转换的语句</param>
        /// <param name="split">转换为摩斯电码时使用的分隔符（应该避免'.' '-' '='），默认为'|'</param>
        /// <returns>对应的摩斯电码</returns>
        public static string GetMorseCodeOfSentence(string sentence, char? split)
        {
            sentence = sentence.Trim().ToUpper();
            var resultList = new List<string>();
            foreach (char c in sentence)
            {
                if (c == ')' || c == '（' || c == '）')
                    resultList.Add(GetMorseCodeOfChar('('));
                else if (c == '？')
                    resultList.Add(GetMorseCodeOfChar('?'));
                else
                    resultList.Add(GetMorseCodeOfChar(c));
            }
            if (split == null || split == '.' || split == '-' || split == '=') split = '|';
            return string.Join((char)split, resultList);
        }
    }
}
```



### 3.5 数组（Arrays）

#### 什么是数组？

+ 数组是一个存储一组相同类型数据的集合。
+ 数组可以分为一维数组、二维数组、交叉数组（多维数组）。
+ 他是一个引用变量。

#### 为什么需要数组？

对于少量数据，我们通过定义少量的变量就可以解决，但是如果对于大量同类型数据我们是无法真的去定义那么多的变量来处理的，例如我们需要统计全国十四亿人的平均年龄，不可能去创建十四亿个整型变量进行运算，直接创建对应长度的数组进行运算会更加方便。

#### 如何使用数组/数组的声明？

基础语法（如果在声明时未进行赋值操作，则仅创建了一个数组名，并未分配实际内存空间）：

+ 一维数组声明：`<变量类型>[] <数组名> (= {<具体内容>});`
+ 二维数组声明：`<变量类型>[][] <数组名> (= {{<第一行具体内容>}...{<第n行具体内容>}});`
+ 交叉数组声明：`<变量类型>[]...[] <数组名> (= {...});`

手动申请空间：

+ 申请空间但不设置初始值（默认按照对应数据类型初始化初始值）：`<变量类型>[] <数组名> = new <变量类型>[申请大小];`
+ 申请空间并赋值：`<变量类型>[] <数组名> = new <变量类型>[申请大小]{<具体值>};`
+ 赋值但不明确申请大小（大小将被设置为赋值的数据个数）：`<变量类型>[] <数组名> = new <变量类型>[]{<具体值>};`

#### 可以对数组进行哪些操作？

数组的使用可以直接通过`<数组名>[index]`进行元素访问，其中`index`为元素下标（下标从0开始，最大为数组大小size-1），如果下标越界则会引起报错。

**获取数组大小：**当不知道数组具体大小时，我们可以通过`array.Length`获取当前操作数组的大小

```c#
int[] arr1 = { 1, 2, 3 };
int size = arr1.Length;		//size = 3
```

**获取元素值：**直接通过`<数组名>[index]`进行访问，例如在`arr1`中，`arr1[0]`的值为1，`arr1[2]`的值为3.

**获取某一元素下标：**使用`Array`类中的`IndexOf(Array, Object)`函数，如获取`2`的下标：

```c#
int index = Array.IndexOf(arr1, 2);//index = 1
```

**遍历数组：**（遍历即为获得从某一位置开始一直到某一位置结束的数组中的所有元素值）

+ 如果要对整个数组进行遍历，我们可以使用`foreach`语句，例如我们想要遍历`arr1`中的所有元素，可以只用如下方法：

  ```c#
  foreach (int i in arr1)
  {
      Console.WriteLine(i);
  }
  ```

+ 如果需要指定某一位置开始到某一位置结束时的所有元素，可以使用`for`循环：

  ```c#
  for (int i = 1; i < arr1.Length; i++)
  {
      Console.WriteLine(i);
  }
  ```

+ 对于`for/foreach`语句，参考[C# for/foreach 循环 | 菜鸟教程 (runoob.com)](https://www.runoob.com/csharp/csharp-for-loop.html)。

**数组增加/删除元素：**数组初始化后不可以直接进行增加或删除元素的操作，如果需要进行增加元素的操作，只能新建一个比他大小更大的新数组并将原来的值添加到新数组，删除同理（也可以单独设置一个数组大小变量，删除时将未删除元素前移并将代表大小的变量修改为新的值）。

**清除数组元素：**清除数组元素可以使用`Clear`函数，他又有两种用法，第一种为清理整个数组元素`Clear(array)`，第二种为清理从某一下标开始的所有元素`Clear(array, index, length)`，清理结果为将元素置为`0`、`null`或`false`：

```c#
int[] arr = { 1, 2, 3, 4, 5 };
Array.Clear(arr, 0, 2);//将从0开始的2个元素置为0，数组变为 { 0, 0, 3, 4, 5 }
Array.Clear(arr);//清除所有元素，数组变为{ 0, 0, 0, 0, 0 }
```

**复制数组：**使用`Copy`函数可以将一个数组的元素复制到另一个数组中，它的语法为`Array.Copy(源数组, 复制起始下标, 目标数组, 粘贴起始下标, 复制长度)`：

```c#
int[] arr1 = { 1, 2, 3, 4, 5 };
int[] arr2 = new int[9];
Array.Copy(arr1, 3, arr2, 4, 2);//arr2 = { 0, 0, 0, 0, 4, 5, 0, 0, 0 }
Array.Copy(arr1, arr2, arr1.Length);//arr2 = { 1, 2, 3, 4, 5, 0, 0, 0, 0 }
```

**数组排序`Sort`：**使用`Sort`函数可以快速对数组排序，默认为递增排序：

```c#
int[] arr3 = { 1, 5, 6, 7, 2, 45, 5 };
Array.Sort(arr3);//arr3 = { 1, 2, 5, 5, 6, 7, 45 }
```



参考链接：<br>[数组 - C# reference | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/arrays)<br>[Array 类 (System) | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/api/system.array?view=net-8.0)<br>[Array.Sort 方法 (System) | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/api/system.array.sort?view=net-8.0)<br>[C# 数组（Array） | 菜鸟教程 (runoob.com)](https://www.runoob.com/csharp/csharp-array.html)

### 3.6 时间结构（DateTime）

#### 什么是时间结构？

时间结构是C#类库提供的用于存储和处理时间数据的结构体，它可以让我们更方便的对时间数据进行处理。

#### 如何使用？

首先要创建对应数据实例，然后再对其进行对应操作。

#### 如何创建时间实例？

直接实例化并赋值：

```C#
var dateTime = new DateTime(2024, 9, 4, 15, 45, 0);
Console.WriteLine(dateTime);	//2024/9/4 15:45:00
```

实例化后赋值当前时间：

```c#
var dateTime = new DateTime();
dateTime = DateTime.Now;
Console.WriteLine(dateTime);	//2024/9/4 15:52:54
```

若实例化后未进行赋值操作，它的默认值为`0001/1/1 0:00:00`。

#### 如何获取不同的时间？

```c#
//获取现在的时间
var now = DateTime.Now;     //2024/9/4 16:02:45
//获取今天的日期，仅会获取日期，小时及以下单位不会获取
var today = DateTime.Today; //2024/9/4 0:00:00
//获取当前所处小时
var nowHour = now.Hour;     //16
//获取当前分钟数
var nowMinute = now.Minute; //2
```

#### 如何对时间进行修改？

```c#
//在当前日期上增加一天
var tomorrow = now.AddDays(1);//2024/9/5 16:02:45
//在当前日期上减少一天
var yesterday = today.AddDays(-1);//2024/9/3 0:00:00
```

#### 如何按照不同格式输出日期？

```c#
Console.WriteLine(now.ToLongDateString());  //2024年9月4日
Console.WriteLine(now.ToShortDateString()); //2024/9/4
Console.WriteLine(now.ToLongTimeString());  //16:13:59
Console.WriteLine(now.ToShortTimeString()); //16:13
Console.WriteLine(now.ToString());          //2024/9/4 16:15:10

//自定义格式输出
Console.WriteLine(now.ToString("yyyy-MM-dd-dddd HH:mm"));   //2024-09-04-星期三 16:19
```

格式化日期字符参考：[标准日期和时间格式字符串 - .NET | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/standard/base-types/standard-date-and-time-format-strings)|[自定义日期和时间格式字符串 - .NET | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/standard/base-types/custom-date-and-time-format-strings)

参考链接：[DateTime 结构 (System) | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/api/system.datetime?view=net-8.0)

#### 什么是时间跨度`TimeSpan`？

时间跨度是一种特殊时间结构，它用来计算某一个时间点到另一个时间点之间的时间段长度（时间跨度）。

```c#
//创建时间跨度并赋值为1:00:00
var timeSpan = new TimeSpan(1, 0, 0);   //01:00:00
//以小时为单位创建
timeSpan = TimeSpan.FromHours(2);       //02:00:00

//将字符串转化为时间跨度
timeSpan = TimeSpan.Parse("01:20:00");

//获取两个时间点中的跨度
var start = DateTime.Now;
var end = start.AddHours(2).AddMinutes(33);
timeSpan = end - start;                 //02:33:00

//按照不同格式输出时间跨度
Console.WriteLine(timeSpan);            //02:33:00
//获取部分内容
Console.WriteLine(timeSpan.Minutes);    //33
//输出总共需要的分钟数
Console.WriteLine(timeSpan.TotalMinutes);//153

//修改时间跨度
timeSpan = timeSpan.Add(TimeSpan.FromMinutes(7));//02:40:00
timeSpan = timeSpan.Subtract(TimeSpan.FromMinutes(40));//02:00:00
```

参考链接：[TimeSpan 结构 (System) | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/api/system.timespan?view=net-8.0)

## 4. 函数

### 4.1 函数基础

#### 什么是函数？

+ 函数又称方法，本质是一个具有名称的代码块。

+ 可以通过函数的名称去执行该代码块。
+ 函数是方便对代码重复使用的一种机制。

#### 为什么要使用函数？

+ 它可以将一系列相关语句封装起来。
+ 可以重复调用，减少冗余代码的书写。
+ 代表类中的一些抽象行为，如实现简单的吃饭、睡觉方法行为。

#### 函数基本语法是什么？

一个函数的基本形式为：

```c#
<访问修饰符> <其他修饰符> <返回值类型> <函数名>(<参数类型1> <参数名1>,..., <参数类型n> <参数名n>)
{
    代码逻辑1;
    ...
    代码逻辑n;
    
    return <返回值>;
}
```

对于每一部分解释如下：

+ **访问修饰符**：访问修饰符作用为设置该函数对其他类的可用性，常见的有`public(对所有类可用)`、`private(仅自己所在类可用)`、`protected(对自己和子类可用)`，具体见[C# 封装 | 菜鸟教程 (runoob.com)](https://www.runoob.com/csharp/csharp-encapsulation.html)|[访问修饰符 - C# reference | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/access-modifiers)。
+ **其他修饰符**：可选内容，如`static(静态方法)`、`virtual(虚方法)`等，参考[abstract 关键字| Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/abstract)|[override 修饰符| Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/override)|[static 修饰符| Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/static)|[virtual 关键字| Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/virtual)|[async 关键字| Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/async)。
+ **返回值类型**：返回值类型包含`void(无返回值类型)`和其他所有数据类型（如`int`、`float`、自定义类等等），他表示这个函数执行完毕后将会返回的数据类型。
+ **函数名**：该函数调用时所使用的标识名称，一般采用大驼峰命名法。
+ **参数列表**：数量可选，类型可以是任何数据类型，表明执行该函数所需要的参数类型及数量。
+ **代码逻辑**：函数中的处理逻辑。
+ **返回值**：在执行结束后，对于非`void`返回值类型函数，必须返回一个对应类型的数据，对于`void`，可以不写`return`语句，也可以写上`return`后直接加分号结束而不返回任何值。

例如，我们书写一个返回值为`int`的两个整数相加的方法函数`AddTwoNum`:

```c#
/// <summary>
/// 两整数相加获取结果
/// </summary>
/// <param name="num1">第一个整数</param>
/// <param name="num2">第二个整数</param>
/// <returns>两数之和</returns>
public int AddTwoNum(int num1, int num2)
{
    int res = num1 + num2;//计算结果
    return res;//返回结果
}
```

对于上面的函数，因为它的逻辑比较简单，可以直接将里面的语句缩短为一句，即`return num1 + num2;`，这样可以省去函数调用时对于结果数据申请的额外空间。

#### 如何进行函数调用？

对于同一个类或结构体中的函数，我们可以直接通过函数名进行调用，例如调用上面的`AddTwoNum`函数计算1+2的结果：

```c#
int res = AddTwoNum(1, 2);
```

对于不同类的非静态函数，需要通过对应类的实例对象进行调用，如对`People`类中的`void SayHello()`进行调用，需要先创建该类的对象，再进行函数调用：

```C#
People alice = new People;//创建实例化对象
alice.SayHello();//调用函数
```

对于不同类的静态函数，可以直接通过对应类名进行调用，如调用`Calculator`类中的`public static int Add(int num1, int num2)`：

```c#
int res = Calculator.Add(1, 2);//直接调用获取结果
```

### 4.2 `ref`和`out`关键字

#### 什么是`ref`和`out`？

+ **ref**：`ref`用于添加在参数类型前，它可以将传入的参数作为引用类型使用，使用时必须在传入参数前加上`ref`关键字。
+ **out**：`out`同样用于添加到参数类型前，添加了`out`关键字的参数可以作为函数内部所需参数使用，也可以仅作为返回值的接收对象。

#### 为什么要使用`ref`和`out`？

在实际编码中，我们可能需要同时使用多个变量参数并希望他的值随着函数运行而修改，但普通值类型变量传参时函数内对该参数进行修改并不会引起原来变量的数值产生任何变化，通过`ref`可以让他像引用类型一样进行函数内值的修改。

而面对函数有多个返回值的情况，使用`out`关键字可以解决原本函数只能有一个返回值的问题，他让我们的函数功能性更加强大。

#### 它们的区别是什么？

+ `ref`参数必须要进行初始化，`out`可以不进行初始化
+ `ref`参数在函数内部可以不做任何处理，`out`参数必须要进行赋值

参考链接：<br>[ref 关键字 - C# reference | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/ref)<br>[out 关键字 - C# reference | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/out)

#### 如何进行使用？

通过`ref`关键字将值类型变为引用类型处理：

```c#
public void NumAddOne(ref int num)
{
    num++;
}

//调用
int num = 0;
NumAddOne(ref num);//调用结束后原本的值+1
```

使用`out`关键字实现多值返回：

```c#
//获取num的平方和开方
public void Num(int num,out int pow2,out double sqt)
{
    pow2 = (int)Math.Pow(num, 2);
    sqt = Math.Sqrt(num);
}

//调用函数
int num = 4;
Num(num,out int pow,out double sqt);
Console.WriteLine($"{num}的平方为{pow},开方为{sqt}");//4的平方为16,开方为2
```

### 4.3 变长参数`params`

#### 什么是变长参数？

+ 变长参数函数的传入参数，他可以为任意数量的同种类型参数的集合。
+ 关键字为`params`，使用时后面必须修饰一个数组而非一个元素。
+ `params`关键字修饰的参数数组必须位于最后一个参数的位置，在她的后面不允许有其他任何参数。

#### 为什么要使用变长参数？

在做一些处理时，我们可能并不知道实际需要处理的参数数量，这种情况下无法直接在声明时定义下来对应的参数，使用变长参数则可以解决这个问题。

#### 如何使用变长参数？

语法为`params <数据类型>[] arr`，例如获取一系列整数之和：

```c#
public int SumOfNum(params int[] arr)
{
    int sum = 0;
    for (int i = 0; i < arr.Length; i++)
    {
        sum += arr[i];
    }
    return sum;
}
```

调用时可以传入任意数量的整数，如：

```C#
int sum = SumOfNum(1, 2, 3, 4, 5, 65);//sum = 80
```

也可以直接传入数组：

```c#
int[] arr = { 1, 2, 3, 4 };
sum = SumOfNum(arr);//sum = 10
```

参考链接：[方法参数 - C# reference | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/method-parameters#params-modifier)

### 4.4 可选参数/参数默认值

#### 什么是可选参数？

+ 在实际应用中，存在某些情况下逻辑处理必须要用到某参数，但实际调用时不一定会包含该参数的传入，这时可以使用可选参数。
+ 可选参数含有一个默认值，在没有传入参数时将会直接使用该默认值，有参数传入时则以世纪传入数据为准。
+ 书写可选参数是直接在参数声明时赋值即可。
+ 可选参数之后不能有任何普通参数声明，但可以为变长参数或其他可选参数。

#### 为什么需要可选参数？

函数编码时，存在一些情况下使用函数者可以对某一些参数进行忽略的情况，例如在求圆的面积的时候，我们默认会写上一个较为精细的圆周率参数，而使用者有时候不会需要这么精细的结果，这是他可以选择直接修改传入圆周率参数或将结果自行进行修改。

#### 如何进行使用？使用举例

声明可选参数即在参数列表进行赋值，如下函数所示：

```c#
public void Say(string name, string str = "无话可说")
{
    Console.WriteLine(name + str);
}
```

调用时不进行可传参数传递：

```c#
Say("Alice");//Alice无话可说
```

调用时传入具体参数：

```c#
Say("Alice", "并非无话可说");//Alice并非无话可说
```

### 4.5 递归函数

#### 什么是递归函数？

递归函数简单来说就是在自己函数内部调用自己本身的函数。

#### 使用递归函数的注意事项？

+ 递归函数必须要有停止条件。
+ 函数的停止条件应该为一个可达成的条件，否则将会导致无限递归最终内存溢出。
+ 递归函数书写简单，但是对内存和性能消耗非常大。

#### 如何使用递归函数？使用举例

用递归函数实现求取斐波那契数列中第n个数的值：

```c#
public int Fibonacci(int num)
{
    if (num == 1 || num == 2) return 1;
    else if (num > 2) return Fibonacci(num - 1) + Fibonacci(num - 2);
    else return 0;
}

Console.WriteLine(Fibonacci(10));//输出结果为55（1 1 2 3 5 8 13 21 34 55）
```

## 5. 面向对象——封装

### 5.1 面向对象编程

#### 什么是面向对象编程？

面向对象是一种对**现实世界理解和抽象**的编程方法，他把**相关数据和方法当作一个整体来看待**，通过程序来形容对象，从更高的层次来进行程序开发，更加贴近事物的自然运行模式。

#### 为什么要学习面向对象？

使用面向对象的思路进行编程，可以提高代码复用率，提高开发效率，提高程序的可拓展性，同时能够让程序有更清晰的逻辑关系。

#### 面向对象三大特征？

+ **封装**：将一些属性和相关方法封装在一个类中，对外隐藏内部具体实现细节。外界不需要关心内部函数实现，只需要根据提供的接口去使用即可。他使得代码使用更加方便、内部数据更加安全，同时也让代码更加利于维护。

+ **继承**：如同现实中子女可以继承父母部分财产一样，面向对象中存在父类和子类的关系，子类可以共享父类的部分资源，提高了代码复用率，其中，父类也叫做基类、超类，子类也叫做派生类。

  ```c#
  //Animal基类
  class Animal
  {
      public virtual void Eat() { Console.WriteLine("动物在吃饭"); }
  }
  //Cat子类
  class Cat : Animal
  {
      public new void Eat() { Console.WriteLine("猫猫在吃饭"); }
  }
  //Dog子类
  class Dog : Animal
  {
      public new void Eat() { Console.WriteLine("狗狗在吃饭"); }
  }
  ```

  ```c#
  Animal animal = new();  //指向基类对象
  animal.Eat();           //调用基类方法
  animal = new Cat();     //指向子类对象
  animal.Eat();           //访问子类函数
  animal = new Dog();     //指向另一子类对象
  animal.Eat();           //访问子类函数
  ```

  输出结果为：

  ```
  动物在吃饭
  猫猫在吃饭
  狗狗在吃饭
  ```

+ **多态**：多态基于继承关系，他让一个变量可以调用多个继承于同一基类的子类的同一个方法，如基类为`动物`类，含有`吃`的功能，子类`猫`、`狗`继承于`动物`类，我们可以通过`动物`类的变量，通过更改他的指向为`猫`或`狗`来调用不同类中的`吃`方法。

参考链接：<br>[什么是面向对象，它的三个基本特征：封装、继承、多态-CSDN博客](https://blog.csdn.net/weixin_51201930/article/details/122652397)<br>[如何理解面向对象编程三大特性------封装、继承、多态 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/45445817#:~:text=面向对象的三个基本特)

#### 面向对象七大原则

设计目标：开闭原则、里氏替换原则、迪米特原则
设计方法：单一职责原则、接口隔离原则、依赖倒置原则、合成复用原则

**开放封闭原则（OCP）**：

+ 扩展开放：某模块的功能是可扩展的，则该模块是扩展开放的。软件系统的功能上的可扩展性要求模块是扩展开放的。
+ 修改关闭：某模块被其他模块调用，如果该模块的源代码不允许修改，则该模块修改关闭的。软件系统的功能上的稳定性，持续性要求模块是修改关闭的。

**里氏替换原则（LSP）**：

+ 如果对每一个类型为S的对象o1，都有类型为T的对象o2，使得以T定义的所有程序P在所有的对象o2都代换成o1时，程序P的行为没有变化，那么类型S是类型T的子类型。
+ 所有引用基类（父类）的地方必须能透明地使用其子类的对象。

**迪米特法则（LOD）/最少知识原则**：

+ 每一个类都应该尽可能跟较少的类进行通讯，避免类与类之间的耦合。

**单一职责原则（SRP）**：

+ 是一个对象应该只包含单一的职责，并且该职责被完整地封装在一个类中。

**接口隔离原则（ISP）**：

+ 对于不同的功能，应该使用专门的接口，尽可能将接口细化。
+ 一个类所依赖的接口不应该出现该类所使用不到的功能。

**依赖倒置原则（DIP）**：

+ 高层模块不应该依赖低层模块，它们都应该依赖抽象。
+ 抽象不应该依赖于细节，细节应该依赖于抽象。
+ 要针对接口编程，不要针对实现编程。

**合成复用原则（CRP）**：

+ 尽量使用对象组合，而不是继承来达到复用的目的。

参考链接：[深入浅出精讲面向对象设计七大原则-CSDN博客](https://blog.csdn.net/m0_49028841/article/details/128164531)

### 5.2 类（class）

#### 什么是类？

+ 类的关键词为`class`。
+ 类是对一类具有相同特征或行为的事物的抽象，例如我们可以将人、车称为类，单独的一个人称为人的对象。
+ 类是对象的模板，可以通过类创建出对象。

#### 如何声明一个类？

```c#
访问修饰符 class 类名
{
    //属性/字段/特征——成员变量
    //行为——成员方法
    
    //构造函数和析构函数
    //索引器
    //运算符重载
    //静态成员
}
```

例如一个`Person`类声明：

```c#
public class Person
{
    private string name;
    private bool sex;
    public int age;
    
    public Person(string name, bool sex)
    {
        this.name = name;
        this.sex = sex;
        this.age =0;
    }
    public Person(string name, bool sex, int age)
    {
        this.name = name;
        this.sex = sex;
        this.age =age;
    }
    public string GetName(){ return name; }
    public bool GetSex(){ return sex; }
    public void SayHello()
    {
        Conaole.WriteLine($"Hello, my name is {name}.");
    }
}
```

#### 什么是（类）对象？

+ 类的声明不等同于类对象的声明，类的声明与结构体、枚举的声明相似，而类对象的声明则是申请了一个自定义变量类型。
+ 类对象是由类创建而来，是一个指定类类型的变量。
+ 对象的声明的过程一般又称为实例化对象。
+ 类对象是引用类型。

#### 如何实例化对象？

实例化对象原理为先申请对应大小的类空间，再调用构造函数对类中属性进行初始化，最后将类地址存入我们的对象变量中。

他的基础语法为`类名 对象名 = new 类名(参数);`（在`.Net`高i版本中可以省略`new`后面的类名），例如实例化上面的`Person`类：

```c#
Person person1 = new Person("张三", true);
Person person2 = new Person("李四", false, 30);
```

除此之外，在申明类对象变量时也可以不进行实例化，而是赋值为空（`null`）或不进行赋值（默认为空），如：

```C#
Person person3;
Person person4 = null;
```

### 5.3 成员变量

#### 什么是成员变量？

+ 成员变量是用来描述对象特征的变量，如人的年龄、性别等，它可以是任何数据类型。
+ 成员变量声明在类语句块中，一个类中包含的成员变量的数量没有任何限制。
+ 成员变量声明时是否赋值进行初始化按照需求来确定。
+ ==如果成员变量为与自己相同的类，声明时一定不要进行实例化，否则会导致栈内存溢出，程序崩溃。==

#### 成员变量的作用？

使用成员变量，可以让属于某一类的特征值存储于类中，如将年龄、性别等存储于人这个类中，实现对数据的封装保存，相对于在外面显式定义这些变量，更加利于我们使用和维护。

#### 如何声明与访问成员变量？

声明成员变量与普通的声明变量相同，唯一区别是要加上访问修饰符（默认为`private`），例如在上面`Person`类中声明了三个成员变量：

```c#
private string name;	//姓名，私有
private bool sex;		//性别，私有
public int age;			//年龄，私有
```

访问成员变量需要先对对象进行实例化，然后才可以访问他的公有变量（未实例对象不可以访问非静态变量及方法）：

```c#
Person p1 = new Person("name", true);
p1.age = 20;		//可以访问 age 成员变量并对其进行操作
p1.name = " ";		//不可进行操作，也不能直接获取对应值，其为私有变量
string name = p1.GetName();//可以通过定义公有方法进行取值操作，同理也可以通过公有方法进行赋值操作

Person p2;
p2.age = 20;		//不可进行操作，p2并非实例化对象
```

#### 访问修饰符是什么？

+ 访问修饰符在类中的成员变量和函数方法等最前面加上的一个关键字，它表明了这个类、函数、变量等的可以被访问到的范围，在C#中，类默认是私有的，类中属性和方法也默认是私有的，但结构体中的属性和方法则默认为公有。
+ 访问修饰符常见的有三种，分别为`public`、`private`、`protected`：
  + `public`：公共的，自己内部和其他地方（外部）均能访问和使用。
  + `private`：私有的，默认访问属性，只有自己内部可以访问，外部不可以进行任何直接操作。
  + `protected`：受保护的，自己内部和子类可以进行访问，其他位置不能进行直接操作。

#### 访问修饰符有什么用？

使用访问修饰符可以对被修饰的实现一种保护效果，例如使用`private`修饰的变量，他将不能被其他类所使用，保证了变量的安全性。

### 5.4 成员方法

#### 什么是成员方法及如何声明？

+ 成员方法是用来描述对象行为的函数，如人的吃饭、睡觉等都可以看作一个成员方法。
+ 他的声明规则与函数相同，声明在类语句块中。
+ 成员方法的参数数量、返回值数量及本身在类中的数量不做任何限制。
+ 成员方法必须通过实例化对象访问（不可以使用`static`关键字修饰），相当于某一个对象的具体行为。

#### 成员方法的使用

成员方法通过对象名加`.`操作符加对应方法名进行使用，例如调用前面`Person`类的`GetName`方法：

```c#
Person p1 = new Person("name", true);
string name = p1.GetName();//返回name

Person p2;
p2.GetName();//无法调用，未进行实例化
```

### 5.5 构造函数

#### 什么是构造函数？

+ 构造函数时在类进行实例化时会直接调用的函数，他可以对对象进行初始化（如实例化一个人并直接初始化他的名称及年龄），函数名与类名相同，他没有返回值，不需要声明返回值类型，可以使用构造函数来对类中的属性进行初始化赋值等操作。
+ 每一个类都会有一个默认无参构造函数。
+ 手动书写的构造函数可以设置任意数量的参数，并且构造函数可以进行重载（可以有同名不同参数的多个函数，每个函数都可以进行独立使用），但如果手动写了有参构造函数，默认无参构造函数将不可以进行使用。
+ 通常情况下构造函数可访问限制为`public`，但也可以针对具体逻辑进行具体设置。
+ 在低版本中允许构造函数中只对部分属性进行初始化，高版本中则必须对所有属性进行初始化。

#### 必须要写构造函数吗？

构造函数并不一定必须写上，写不写构造函数取决于需不需要进行对象的一些初始化逻辑，但不写构造函数时系统会默认生成无参构造函数。当然初始化逻辑也不一定写在构造函数中，可以写成其他函数进行初始化。

#### 如何声明构造函数？

构造函数语法与普通函数一致，唯一区别为函数名比喻为类名且不能声明任何返回值，例如如下的一个类：

```c#
public class Person
{
    public string name;
    public int age;
    public char sex;
    public Person()
    {
        name = "无名";
        age = 0;
        sex = '男';
    }
    public Person(string name)
    {
        this.name = name;
        age = 0;
        sex = '男';
    }
    public Person(string name, int age)
    {
        this.name = name;
        this.age = age;
        sex = '男';
    }
    public Person(string name, int age, char sex)
    {
        this.name = name;
        this.age = age;
        this.sex = sex;
    }
}
```

构造函数的使用如下：

```c#
Person p1 = new Person();//无参构造，name = "无名" age = 0 sex = '男'
Person p2 = new Person("张三");//name = "张三" age = 0 sex = '男'
Person p3 = new Person("李四", 20);//name = "张三" age = 20 sex = '男'
Person p4 = new Person("王五", 21, '女');//name = "王五" age = 21 sex = '女'
```

除了直接写一个方法去初始化之外，还可以用`this`来调用已有的函数，执行时会优先调用`this`相关函数，在执行函数内部语句块，这样可以简化代码书写量，例如上面的`Person`类，我们可以对他进行修改简写，修改后功能相同但是代码量会减少许多：

```c#
namespace ClassStudy
{
    public class Person
    {
        public string name;
        public int age;
        public char sex;
        public Person()
        {
            name = "无名";
            age = 0;
            sex = '男';
        }
        public Person(string name) : this()
        {
            this.name = name;
        }
        public Person(string name, int age) : this(name)
        {
            this.age = age;
        }
        public Person(string name, int age, char sex) : this(name, age)
        {
            this.sex = sex;
        }
    }
}
```

参考链接：[构造函数 - C# | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/programming-guide/classes-and-structs/constructors)

#### 什么是静态构造函数？

+ 静态构造函数是一个特殊的构造函数，用于初始化函数中的静态变量。
+ 静态构造函数语法为`static className(){ ... }`，他不能拥有任何参数。
+ 静态函数与普通无参构造函数相互独立，不存在重载的说法。

#### 静态构造函数的作用？

静态构造函数是初始化静态变量的函数，如果类中具有静态变量且需要进行初始化，则一定要写静态构造函数。

#### 静态构造函数和普通构造函数调用的时机

+ 普通构造函数在对象进行实例化时调用，每次实例化都会调用对应的构造函数。
+ 静态构造函数在类首次进行实例化或首次访问类中静态变量或静态方法时进行调用，==整个程序运行中只会调用一次==。

### 5.6 析构函数与垃圾回收机制GC

#### 什么是析构函数？

+ 析构函数是在申请的内存被回收时会调用执行的函数，通俗来讲就是在对象使用完成后对他进行清理的函数，可以在析构函数内写入对数据的最后处理逻辑。
+ C#中有自动垃圾回收机制GC，他会帮我们堆内存进行回收处理，所以不太会实际应用到析构函数，除非需要做一些特殊的处理。
+ 析构函数的语法为：`~类名(){}`。

#### 什么是垃圾，什么是垃圾回收机制（Garbage Collector, GC)？

+ 垃圾指没有被任何变量、对象所引用的无用内存，即申请使用后已经没有任何一个变量存储的地址指向他的堆内存。
+ 垃圾回收机制则是`.Net`对堆（Heap）内存进行自动化管理，他会对堆进行遍历，在确定某些对象为垃圾时，会自动进行内存释放的机制。
+ 垃圾回收有多种算法，如引用计数（Reference Counting）、标记清除（Mark Sweep）、标记整理（Mark Compact）、复制集合（Copy Collection）。

#### GC如何进行垃圾回收原理？

+ 在垃圾回收机制中，不同对象会被使用分带算法划分到不同的内存代中（0代内存、1代内存、2代内存），新分配的对象会被配置在第0代内存中，大对象（内存超过85000字节）则始终被认为存在于第二代内存（目的为减少性能损耗，提高性能）。
+ 每一次分配内存时，当第0代内存满时会触发垃圾回收进行内存释放，垃圾回收器将会先将所有对象视为垃圾，再从根（静态字段、方法参数）进行检查引用对象，并将其标记为可达对象，而未被标记的对象则会被视为垃圾进行释放处理；可带对象将会被搬迁移入高一级内存代，并尽可能清理内存碎片，并修改其对应的引用地址（不会对大对象进行搬迁）。
+ 1代或2代内存满时会触发低代的内存回收。
+ 除等待GC自动回收内存之外，也可以手动触发避免软件运行时突然卡顿（通常会在加载新内容时进行释放而避免在正常运行时释放内存），手动释放方法为调用`GC.Collect()`。

参考链接：[.NET 垃圾回收 | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/standard/garbage-collection/)

### 5.7 成员属性（Property）

#### 什么是成员属性？

成员属性时用于保护成员变量的字段，他可以在对属性的获取或赋值的时候添加逻辑处理（如加密解密或逻辑判断）；属性可以设置只可访问不可修改或只可修改不可访问，解决了原有的访问限制的局限性。

#### 成员属性的声明？

成员属性声明在类代码块中，一般采用大驼峰命名法则，具体形式如下：

```c#
public type Name
{
    set { ... }
    get { ... }
}
```

+ 成员属性代码块中可以仅保留`set`代码块或`get`代码块，`get`代码块必须要具有一个返回值。
+ 成员属性进行修改时，传入数据被存储在变量名为`value`的变量之中，可以直接使用该变量，如在`set`中处理逻辑为将传入值赋值给成员变量`money`：`set { money = value; }`。
+ 如果将其赋值给其他成员变量，它本身仍然会被赋值：<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240905154214608.png" alt="image-20240905154214608" style="zoom:50%;" />
+ 属性中`get` `set`方法前可以添加访问修饰符，当修饰符级别不能大于属性本身访问级别且至少一个方法不进行级别设置，采用属性本身级别。

#### 什么是自动属性？

当我们不需要对某一属性进行任何特殊处理时，可以使用自动属性，即`set`和`get`不书写任何代码块，类似于`public int Money { get; set; }`，这时可以将属性当作成员变量来使用，但若无仅可读等设置，应该尽量使用成员变量而非自动属性，这将节约程序内存占用并提高性能。

对自动属性进行`set`赋值操作的结果：<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240905153432244.png" alt="image-20240905153432244" style="zoom:50%;" />

参考链接：[使用属性 - C# | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/programming-guide/classes-and-structs/using-properties)

### 5.8 索引器（Indexer）

#### 什么是索引器？

+ 索引器类似于属性，他让类或结构的实例化对象可以像数组一样进行访问，我们可以使用索引器来自定义不同索引可以访问的函数或成员变量等内容，实现我们自己的客制化访问。
+ 类似于重载`[]`运算符。
+ 索引器中`get` `set`也可以加入逻辑处理语句。
+ 索引器可以像普通函数一样进行重载（修改`[]`中的参数类型或数量）。

#### 索引器基本语法是什么？

```c#
element-type this[int index] 
{
   // get 访问器
   get 
   {
      // 返回 index 指定的值
   }

   // set 访问器
   set 
   {
      // 设置 index 指定的值 
   }
}
```

例如我们在一个`Person`类中让他可以通过`[属性名]`获取对应属性值的字符串，可以将索引写为：

```c#
public string this[string name]
{
    get
    {
        switch(name)
        {
            case "name":
                return this.name;
            case "age":
                return age.toString();
            case "sex":
                return sex.toString();
        }
        return string.Empty;
    }
}
```



参考链接：<br>[索引器 - C# 编程指南 | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/programming-guide/indexers/)<br>[C# 索引器（Indexer） | 菜鸟教程 (runoob.com)](https://www.runoob.com/csharp/csharp-indexer.html)

### 5.9 拓展方法

#### 什么是拓展方法？

+ 拓展方法指的是对已有的变量类型添加自定义新方法（该类型的私有属性不可访问），通过定义拓展方法可以让我们更方便的使用某一类型变量，以实现开发中个人的需求。
+ 拓展方法一定是在静态类中的静态函数，第一个参数必须用`this`修饰，代表被拓展的类型及调用该方法的具体实例。
+ 拓展方法第一个参数还可以使用`ref`修饰，他与`this`关键字位置可以任意排序。

#### 拓展方法有什么作用？

+ 提升程序的拓展性。
+ 可以不通过继承来添加方法。
+ 不需要在对应类中去书写方法。
+ 对别人封装的类添加自己认为有用的额外的方法，如给string添加获取最长重复字符的方法等。

#### 拓展函数的语法是什么？

```c#
public static 拓展类类名
{
    public static 返回值类型 拓展方法名(ref this 被拓展类型 name, ...)
    {
        //拓展方法处理语句
    }
}
```

例如，为int拓展修改值为平方并打印的功能：

```c#
public static class TestClass
{
    public static void GetPow2(ref this int num)
    {
        int temp = num * num;
        Console.WriteLine($"{num}的平方为{temp}");
        num = temp;
    }
}
```

声明一个`int`变量并调用该方法：

```c#
int i = 2;
i.GetPow2();
```

输出结果为：

```
2的平方为4
```

参考链接：[扩展方法 - C# | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)

### 5.10 运算符重载

#### 什么是运算符重载？

运算符重载即针对某一类型数据将他对应的操作符进行操作语义的重载，例如自定义水果类实现他们的`+`操作相加的是水果的价格这样，用来实现我们需要的一些特殊的功能。

#### 为什么使用运算符重载？

在使用自定义类型时，无法直接通过`+`或`-`或其他运算符来对对象进行直接的操作，例如我们无法对自定义点坐标进行直接`+`或`-`的操作，这时我们可以对运算符进行重载让运算符可以实现我们所需的功能。

#### 重载运算符语法？

操作符重载使用`operator`关键字，重载函数位置必须在该类之中且为静态公有函数，它的语法如下：

```c#
public static 类名 operator 操作符(对应参数)
{
    //逻辑语句
    return 返回值;
}
```

例如在`Point`类中重载`+`运算符使得两点坐标相加：

```c#
public class Point
{
    public int x;
    public int y;

    public static Point operator +(Point a, Point b)
    {
        return new Point()
        {
            x = a.x + b.x,
            y = a.y + b.y
        };
    }

    public Point()
    {
        x = 0;
        y = 0;
    }
}
```

在其他位置使用：

```c#
Point point1 = new() { x = 2, y = 1 };
Point point2 = new() { x = 1, y = 2 };
Point point3 = point1 + point2;
Console.WriteLine(point3.x + " " + point3.y);
```

结果为`3 3`。

#### 可重载运算符和不可重载运算符

参考官方文档：[运算符重载  - C# reference | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/operator-overloading)

除运算符外，还可以自定义转换运算：[用户定义的显式和隐式转换运算符 - 提供对不同类型的转换 - C# reference | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/user-defined-conversion-operators)

## 6. 面向对象——继承

### 6.1 继承概念

#### 什么是继承?

继承是面向对象中三大特征之一，它允许类像父子一样存在继承关系，继承类可以继承被继承类中的所有成员及方法，其中被继承的类称为`父类`、`基类`、`超类`，继承类称为`子类`或`派生类`，在`C#`中只允许单类继承。

#### 继承有什么作用?

如同后代继承现代资产和手艺等，使用继承可以提高代码复用，同时在子类中还可以对父类方法进行进一步的拓展或修改。

#### 继承的基本语法是什么？

`C#`中的继承与`C++`、`Java`不同，它不需要使用任何关键字，只需要使用`:`并在后面写上所继承的父类，形式如下：

```csharp
访问修饰符 class 子类 : 父类 {}
```

#### 父类中不同访问修饰符的作用或影响是什么？

+ `public`可以让内外部均可以访问该属性或方法。
+ `private`只有父类内部可以进行访问，子类和外部都无法访问该属性和方法。
+ `protected`只有父类及其子类可以访问，外部无法访问。
+ `internal`只有在同一个程序集中的文件才可以进行访问。

#### 子类和父类允许有同名成员吗？

子类和父类中可以有同一个名称的成员，子类中的成员将会覆盖掉父类中原有的成员。通常来讲不建议在子类中声明父类中同名的成员，如果不得不声明，需要在变量名或返回值前加上`new`关键字。

#### 使用示例

```csharp
class Food
{
    public string name = "";
    public int price;
    public void GetNameAndPrice()
    {
        Console.WriteLine(name + ":" + price);
    }
}
class Apple : Food
{
    public string color = "red";
    //覆盖父类成员方法
    public new void GetNameAndPrice()
    {
        //调用父类中公有成员
        Console.WriteLine(color + name + ":" + price);
    }
}
```

### 6.2 子类当中的构造函数

#### 父类中含有构造函数子类中是否还可以书写构造函数？

可以，子类当中可以书写构造函数。

#### 调用子类构造函数执行顺序是什么？

在执行时，先会寻找到父类中的对应同参构造函数，再执行子类构造函数。

#### 为什么父类当中没有无参构造函数会导致继承报错？

因为在实例化子类对象时，会默认调用父类的无参构造函数初始化被继承的部分，没有无参构造函数将导致无法被正常初始化，所以会无法继承，但是可以通过`base`调用父类中其他构造函数来解决。

#### 如何使用没有无参构造的父类继承？

使用`base`关键字调用父类中的其他构造函数，可以解决父类没有无参构造时的继承问题。

例如父类如下：

```csharp
public class Animal
{
    public Animal(string name)
    {
        Console.WriteLine("The Animal`s name is " + name);
    }
}
```

子类直接继承会有报错提示：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240918112339030.png" alt="image-20240918112339030" style="zoom:67%;" />

将子类构造定向调用父类构造，可以解决这个问题：

```csharp
public class Cat : Animal
{
    public Cat(string name) : base(name)
    {
        Console.WriteLine("The Cat`s name is " + name);
    }
}
```

在实例化子类时，他的调用如下：

```
The Animal`s name is neko
The Cat`s name is neko
```

### 6.3 万物之父Object

#### 什么是万物之父Object？

`Object`是所有类型的基类，C#中任何类型都可以向上转换为`object`类，它本身是一个引用类型。

#### object有什么用处？

因为所有类型都是基于Object，所以在不确定参数类型时可以使用Object来进行参数接收，但是需要注意的是使用时需要先转换为对应类型才可以进行使用。

#### 如何使用？

在创建Object变量或参数时，使用的方法与其他类型相同，但是使用时需要进行类型转换，转换的方式有两种，第一种为强制转换即在前面加上括号并写入目标类型，第二种为对引用类型使用`as`关键字进行转换，如下代码：

```csharp
object p1 = new Person();//用object接收类
if (p1 is Person)
    (p1 as Person).Speak();//转换为对应类实例

object i = 10;//用object接收值类型
Console.WriteLine((int)i);//转换为对应值类型

object str = "12345";//用object接收接收特殊数据类型
Console.WriteLine(str.ToString());//进行类型转换
Console.WriteLine(str as string);

object arr = new int[5] { 1, 2, 3, 4, 5 };//用object接收接收数组
Console.WriteLine((int[])arr);
Console.WriteLine(arr as int[]);
```

#### 什么是装箱拆箱？

装箱拆箱本质即在使用Object接收值类型数据时产生的内存迁移。

值类型本身存储于栈区，再通过object接收时会将栈区内存迁移至堆区，即为`装箱`；在使用时需要转换为值类型使用，需要将堆区内存移回栈区，即为`拆箱`。

#### 装箱拆箱有什么弊端？

装箱拆箱存在内存迁移，每一次迁移CPU都会对迁移地址进行运算，大量的装拆箱将会浪费大量CPU资源。

#### Object中的静态方法`bool Equals(Object? objA, Object? objB)`

该方法用于比较两个数据的值是否相同，对于引用类型如果调用这个函数，他比较的将是这个变量所指向的内存地址是否相同而非内存值是否相同，例如如下代码：

```csharp
int i1 = 1;
int i2 = 1;
Console.WriteLine("object.Equals(1,1):" + Equals(i1, i2));

object o1 = new();
object o2 = new();
Console.WriteLine("object.Equals(o1,o2):" + Equals(o1, o2));

object o3 = o1;
Console.WriteLine("object.Equals(o1,o3):" + Equals(o1, o3));
```

执行结果为：

```
object.Equals(1,1):True
object.Equals(o1,o2):False
object.Equals(o1,o3):True
```

#### Object中的静态方法`bool ReferenceEquals(Object? objA, Object? objB)`

`ReferenceEquals`用于比较两个对象实例是否相等（是否指向同一块内存），如果两个内存相同则返回`true`，不同则返回`false`。他仅可以比较两个引用类型的数据，不可以用来比较值类型数据，比较值类型数据时会始终返回`false`。

```csharp
Console.WriteLine("ReferenceEquals(o1, o2):" + ReferenceEquals(o1, o2));//比较两个不同实例
Console.WriteLine("ReferenceEquals(o1, o3):" + ReferenceEquals(o1, o3));//比较相同实例

Console.WriteLine("ReferenceEquals(1, 1):" + ReferenceEquals(1, 1));//比较值类型
```

执行结果为：

```
ReferenceEquals(o1, o2):False
ReferenceEquals(o1, o3):True
ReferenceEquals(1, 1):False
```

#### Object中的成员方法`public Type GetType()`

这个方法用于获取实例的类型，它会返回一个Type类型的对象，直接进行打印会获得该实例的类所属的命名空间及类名称：

```csharp
object obj = new Person(new People());
Console.WriteLine("obj.GetType().ToString():" + obj.GetType().ToString());
obj = new People();
Console.WriteLine("obj.GetType().ToString():" + obj.GetType().ToString());
```

运行结果：

```
obj.GetType().ToString():CSharp.Person
obj.GetType().ToString():CSharp.People
```

#### Object中的成员方法`protected Object MemberwiseClone()`

这个方法实现了对象的浅拷贝，使用它拷贝出来的对象会是一个新的对象，但是示例中的引用变量与原来的对象相同。但是这个方法可访问性为`protected`，因此只能在被拷贝的类中使用，无法在外部使用，如果需要在外部使用需要用函数进行包裹。

例如有一个`Person`类对象`p1`，其中包含一个`People`对象成员`people`，对`p1`使用浅拷贝得到`p2`，会发现`p2`中的非引用变量与`p1`不同，但引用变量指向的是同一个实例（内存地址）：

```csharp
class Person
{
    public bool sex;
    public People people;
    public Person(People people, bool sex)
    {
        this.people = people;
        this.sex = sex;
    }
    public Person GetCopy()//用函数进行包裹，让外部可以使用浅拷贝函数
    {
        return (Person)MemberwiseClone();
    }	
}
public class People
{
    public int age = 0;
}
```

```csharp
People p = new();
Person p1 = new(p, true);
p.age = 10;
Person p2 = p1.GetCopy();
Console.WriteLine("p1.people.age:" + p1.people.age);
Console.WriteLine("p1.sex:" + p1.sex);
Console.WriteLine("p2.people.age:" + p2.people.age);
Console.WriteLine("p2.sex:" + p2.sex);

p1.people.age = 99;//改变p1的成员对象的成员变量值
Console.WriteLine("p2.people.age:" + p2.people.age);

Console.WriteLine(ReferenceEquals(p1.people, p2.people));
```

输出结果：

```
p1.people.age:10
p1.sex:True
p2.people.age:10
p2.sex:True
p2.people.age:99
True
```

#### Object中的虚方法`public virtual bool Equals(Object? obj)`

这个方法适用于比较与传入实例值是否相等，并且对于所有值类型变量，官方已经对这个方法进行了重写。

对于我们自己的类，默认执行会比较是否指向同一实例，而我们可以对其进行重写让其实现我们自己的判断逻辑。

默认比较是否指向同一实例：

```csharp
object obj1 = new int[1, 2, 3];
object obj2 = new int[1, 2, 3];
Console.WriteLine(obj1.Equals(obj2));
```

```C#
False
```

自定义重写方法比较：

```csharp
class Animal
{
    public string name;
    public Animal(string name)
    {
        this.name = name;
    }
    public override bool Equals(object? obj)
    {
        if(obj!=null&&((Animal)obj).name == this.name)
            return true;
        return false;
    }
}
```

```csharp
Animal a1 = new("Cat");
Animal a2 = new("Cat");
Console.WriteLine(a1.Equals(a2));
```

```
True
```

#### Object中的虚方法`public virtual int GetHashCode()`

该函数用于返回对象的哈希编码，即一种通过哈希算法计算而得的对象编码，如果两个对象是同样的，那么他们的哈希码一定相同，但哈希码一定相同的不一定会是同一个对象。

一般而言该函数使用频率非常低，通常不会使用该方法。

[Object.GetHashCode 方法 (System) | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/api/system.object.gethashcode?view=net-8.0)

#### Object中的虚方法`public virtual string? ToString()`

这个方法即将对象转换为字符串形式的方法，默认情况下会打印出来对象所在命名空间即对象的类型，但是可以通过在类里面进行重写实现我们自己的功能，例如下面的直接打印数组和重写`Animal`后进行打印：

```csharp
class Animal
{
    public string name;
    public Animal(string name)
    {
        this.name = name;
    }
    public override bool Equals(object? obj)
    {
        if (obj != null && ((Animal)obj).name == this.name)
            return true;
        return false;
    }
    public override string ToString()
    {
        return "The Animal`s Name is " + name;
    }
}
```

```csharp
object obj = new int[1, 2, 3];
Console.WriteLine(obj.ToString());

Animal animal = new("Cat");
Console.WriteLine(animal);
```

输出结果：

```
System.Int32[,,]
The Animal`s Name is Cat
```

### 6.4 密封类sealed class

#### 什么是密封类？

密封类即在`class`关键字前加上`sealed`关键字的类，它可以让这个类不能被继承（断子绝孙）。

#### 密封类有什么用处？

密封类可以让底层子类不能被继承，保证代码规范性、结构性和安全性，主要用于复杂程序或程序框架之中。

#### 如何声明密封类？

声明密封类只需要在`class`关键字前加上`sealed`关键字即可，例如下面的代码：

```csharp
sealed class Cat : Animal{...}
```

## 7. 面向对象——多态

### 7.1 多态

#### 什么是多态？

多态即“多种状态”，它可以让继承于同一父类的子类在执行相同方法时有不同的行为状态（不同的函数执行方式），例如同一个爹的不同儿子有着不同的性格行为，但他们都是这个爹的儿子。

#### 多态有什么用？

多态可以让继承同一父类的每一个对象调用同一方法时有唯一的方法执行逻辑，实现每一个子类均为独立个体，拥有独立行为（用父类接收的子类对象可以调用自己的函数而非父类中的函数）。

#### 如何使用多态进行代码书写？

首先要记住三个关键字vob(`virtual`、`override`、`base`)，其中`virtual`关键字用于定义父类方法，他将该方法声明为虚方法，子类可以进行重写以实现子类的特殊执行，在子类重写父类虚方法时，需要加上`override`关键字，代表这个方法为重写的父类方法，如果需要调用父类中的代码逻辑，在函数中可以用`base`来进行调用。

例如有父类`GameObject`和子类`Player`、`Enemy`：

```csharp
public class GameObject
{
    public string name;
    public GameObject(string name)
    {
        this.name = name;
    }
    public virtual void Attack(GameObject gameObject)//父类中的虚方法
    {
        Console.WriteLine(name + "进行了攻击");
    }
}
public class Player : GameObject
{
    public Player(string name) : base(name) { }
    public override void Attack(GameObject gameObject)//对父类虚方法进行重写
    {
        Console.WriteLine(name + "对" + gameObject.name + "进行了攻击");
    }
}
public class Enemy : GameObject
{
    public Enemy(string name) : base(name) { }
    public override void Attack(GameObject gameObject)//对父类虚方法进行重写
    {
        base.Attack(gameObject);//调用父类方法
        Console.WriteLine(gameObject.name + "受到了攻击");
    }
}
```

对他们进行实例化并调用：

```csharp
GameObject player = new Player("泠曦");
GameObject enemy = new Enemy("老战士格雷特");
player.Attack(enemy);
enemy.Attack(player);
```

运行结果：

```C#
泠曦对老战士格雷特进行了攻击
老战士格雷特进行了攻击
泠曦受到了攻击
```

### 7.2 抽象类和抽象函数abstract

#### 什么是抽象类和抽象函数？

简单来讲抽象类是一个不能被实例化的类，只允许被其他类继承，而抽象函数则只能写在抽象类中，他不能有任何实现。例如人类和每个单独的人，人类一般不会拿来代指某一个个体。

#### 为什么需要抽象类和抽象函数？

抽象类和抽象函数可以用于定义一些比较宽泛的概念如人、水果、动物等，他们不是用来描述单一个体，而是用来描述一系列的对象，不能进行具体实例化的类和函数。使用抽象类和抽象函数可以用于定义这些较为抽象的概念而不必去具体的实现他（例如我们无法直接描述动物是怎么进食的，也无法直接描述水果应该如何食用，但他们确实具备这样的功能或方法），这样可以对一系列类进行方法函数的规范，保证继承后的对象表面特征的一致性，具体实现的多样性。

#### 已经有虚函数为什么还需要抽象函数？

虚函数可以有函数体，可以在函数体中写入一些基础的处理逻辑，但虚函数在被子类继承时，可以不对其进行重写，如果写了一个空虚函数，在未进行重写的情况下运行将会出现错误，对于已经写了预处理逻辑的函数，如果子类改变了部分处理方法，运行时也可能会出现错误，并且因为子类中没有重写该函数而出现难以排查的结果。

抽象函数没有函数体，只需要定义方法名及参数，不关心具体实现，子类必须对其进行重写，避开了前面虚函数的未重写错误或难以排查问题所在的问题（实现函数必定会在子类当中）。

#### 如何书写抽象类和函数？

抽象类和函数都由`abstract`关键字修饰，抽象类在`class`前加上关键字，抽象函数则在返回之前添加，但是需要注意抽象函数不能有具体函数体实现：

```csharp
//抽象类
public abstract class Fruits
{
    public int price;//抽象类中可以定义变量、属性等
    public Fruits(int price)
    {
        this.price = price;
    }
    //抽象方法  不能有具体实现
    public abstract void EatFruit();
}
```

#### 如何实现抽象类及抽象函数？

实现抽象类只需要继承该类即可，继承后如果含有抽象函数将会报错，此时可以手动添加抽象函数或右键报错位置，选择`实现抽象类`VS将会自动实现所有抽象函数，只需要填充对应函数体即可：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240918154508774.png" alt="image-20240918154508774" style="zoom:50%;" />

```csharp

//继承抽象类
public class Orange : Fruits
{
    public Orange(int price) : base(price) { }
    //进行方法重写
    public override void EatFruit()
    {
        Console.WriteLine("吃了一个价值为" + price + "的橘子");
    }
}
public class Durian : Fruits
{
    public Durian(int price) : base(price) { }

    public override void EatFruit()
    {
        Console.WriteLine("打开了一个价值" + price + "的榴莲并将榴莲壳作为了防具");
    }
}
```

进行实例化并调用：

```csharp
Fruits fruit = new Orange(3);
fruit.EatFruit();
fruit = new Durian(100);
fruit.EatFruit();
```

```C#
吃了一个价值为3的橘子
打开了一个价值100的榴莲并将榴莲壳作为了防具
```

### 7.3 接口interface

#### 什么是接口？

接口（interface）是多态的一种体现，他可以看成一种特殊的只包含抽象函数和属性的抽象类，但是与抽象类不同，接口是一种行为方式的集合，代编着一种特殊的行为，例如`飞行 `这个行为，它可以是鸟的行为，也可以是飞机的行为，这里可以将飞行作为接口来定义。

#### 接口有什么用？

接口定义了行为，继承并实现该接口的类相当于具有了这样的行为，通过接口可以对这些行为函数进行规范，同时接口又可以当成他们的基类使用，同一种接口可以接收飞机和鸟这两个除了能飞之外完全不同的类对象，实现了按功能区分不同类。

#### 如何让定义接口/定义接口时需要注意什么？

定义接口关键字为`interface`，默认访问修饰符为`public`并且只能为`public`，接口当中的字段可以为`public`或`protected`，默认为`public`，接口中的函数不能进行定义，只能在实现接口的类中进行定义。

例如书写一个飞行接口：

```csharp
public interface IFly
{
    public float Speed { get; set; }
    public void Fly();
}
```

#### 如何实现接口？

实现接口与继承抽象类大致相同，但不同的是需要实现接口内的所有字段，并且只能为`public`，实现的函数可以为虚函数，子类继承是可以再次进行重写。

例如实现上面的接口：

```csharp
public class Flight : IFly
{
    public float Speed { get; set; }

    public virtual void Fly()//时限为虚函数
    {
        Console.WriteLine("飞机以时速为" + Speed + "的速度在飞行。");
    }
}
public class Bird : IFly
{
    public float Speed { get; set; }

    public void Fly()
    {
        Console.WriteLine("小鸟正在飞行。");
    }
}
```

#### 一个类最多可以实现多少接口？

与继承类这种一个孩子只能由一个父母不同，一个对象它可以有多种行为方法，所以一个类可以实现多个接口。

#### 接口可以继承接口吗？

接口就可以继承接口，并且不用进行函数等的实现，他仅仅相当于继承了对应的行为。

同一个接口可以继承多个不同的接口，例如：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240918165843728.png" alt="image-20240918165843728" style="zoom: 50%;" />

#### 如果不同接口中出现了同名函数，应该如何进行实现和访问？

当不同接口中出现同名函数时，实现接口需要使用显式实现的方法，语法为`接口名.方法名`，但是显示实现的函数不能有访问修饰符，并且不能通过类实例进行访问。例如有两个接口包含同名函数：

```csharp
interface IWalk
{
    public void Move();
}
interface IRun
{
    public void Move();
}
```

实现这个接口时，显式实现：

```csharp
public class People : IWalk, IRun
{
    void IWalk.Move()//实现IWalk
    {
        Console.WriteLine("Walk");
    }

    void IRun.Move()//实现IRun
    {
        Console.WriteLine("Run");
    }
}
```

访问显式实现后的函数，需要通过接口而不是通过类对象：

无法通过实例找到方法：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240918170732733.png" alt="image-20240918170732733" style="zoom:67%;" />

可以通过接口访问：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240918170921737.png" alt="image-20240918170921737" style="zoom:67%;" />

访问时结果与分别对应的实现一致：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240918171010008.png" alt="image-20240918171010008" style="zoom:67%;" />

#### 可以不显式实现同名函数吗？

可以直接书写一个函数进行实现，但如果不显式实现对应函数，将会导致不同接口调用执行效果一致，违背了接口设计时对不同行为进行分离的初衷。

### 7.4 密封方法Sealed Function

#### 什么是密封方法？

密封方法就是对父类函数进行重写时使用`sealed`关键字修饰的函数，他让这个函数不可以再次被重写。

#### 什么时候会用到密封方法？

当我们重写一个函数后不希望子类对他再次重写破坏掉原有逻辑时，可以使用蜜蜂方法。

#### 如何定义密封方法？

定义密封方法只需要在重写关键字前加上sealed关键字即可：

```csharp
public class Boeing : Flight
{
    public sealed override void Fly()
    {
        base.Fly();
    }
}
```

重写后如果再有类继承该类，将无法进行重写：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240918173228831.png" alt="image-20240918173228831" style="zoom: 50%;" />

## 8. 命名空间namespace

### 8.1 命名空间namespace

#### 什么是命名空间？

命名空间类似于Java中的包，它包含了一系列不同名称的类和其他命名空间，可以看作是对类和功能的一个分类，不同的命名空间下的程序需要使用这些功能时需要引用该命名空间才能使用。例如在C#中`System`命名空间就包含了一系列常用的类和函数，除了这些，它内部还包含了常用集合的命名空间`Collections`及其他命名空间。

#### 命名空间的作用是什么？

一个命名空间可以装入许多不同的类、接口等等，它就像一个工具箱，包含了许多各种各样的工具。在不同的命名空间中，可以实现同样名称的类、接口等，因为他们相当于存在不同的工具箱内；同一命名空间则不允许出现同名的类、接口等，就宛如同一个工具箱中出现多个一摸一样的工具是无意义的。

#### 内部类和命名空间都可以往其中写入不同的类、接口等，为什么不使用内部类的写法替换命名空间？

内部类一般是与外围类有着一定逻辑关系的类，访问内部类通常必须要通过外围类实例进行访问，他的可访问性也与外围类相关，并且内部类只能书写在外围类之中，所以通常而言只能写在一个文件内（除分部类的情况外）；命名空间则一般包裹着同一类或具有一系列相近功能的类、接口等，他没有可访问性的概念，命名空间的类可以写在同一文件或不同文件中，只需要处于同一命名空间即可，使用命名空间中的类只需要引入命名空间即可，使用命名空间也更加便于管理相关类和接口等。

在具体使用上，命名空间就像是文件夹，文件夹中可以放各种各样不同文件，而内部类则相当于文件中的一部分内容，例如Excel文件中的一个分页，他无法替代命名空间就如一个文件无法替代一个文件夹一样。

#### 如何声明命名空间？

C#命名空间的声明有两种方式，一种是用大括号`{}`包裹，另一种则是直接使用分号`;`将整个文件看作一个命名空间。

用括号包裹使用举例：

```csharp
namespace NamespaceStudy
{
    public class TestNamespace1
    {
        public TestNamespace1()
        {
            Console.WriteLine("TestNamespace1");
        }
    }
}
```

上面代码也等价于用分号结尾的声明：

```csharp
namespace NamespaceStudy;

public class TestNamespace1
{
    public TestNamespace1()
    {
        Console.WriteLine("TestNamespace1");
    }
}
```

但是使用分号结尾将使这个文件不能声明其他任何的命名空间，是用圆括号结尾则可以在命名空间内嵌入新的命名空间：

```csharp
namespace NamespaceStudy
{
    public class TestNamespace1{ ... }

    //新的命名空间
    namespace NamespaceStudy2
    {
        public class TestNamespace2
        {
            public TestNamespace2()
            {
                Console.WriteLine("TestNamespace2");
            }
        }
    }
}
```

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240920162715114.png" alt="image-20240920162715114" style="zoom: 67%;" />

#### 如何使用命名空间中的类和接口？

使用命名空间中的类和接口的方法同样有两种，一种是通过`using`关键字引入后直接使用，另一种则是显式使用，需要用`命名空间名.类名或接口名`进行使用，例如使用上面代码中的`TestNamespace1`类进行实例化，可以有以下两种写法：

```csharp
using NamespaceStudy;//引入命名空间
namespace CSharp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            TestNamespace1 testNamespace1 = new();//进行实例化
        }
    }
}
```

```csharp
namespace CSharp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            NamespaceStudy.TestNamespace1 testNamespace1 = new();//直接进行显式使用
        }
    }
}
```

但是对于==不同命名空间中出现的同名类或接口，必须显式使用==，否则编译器将无法理解他需要具体使用那个命名空间中的类或接口。

### 8.2 using关键字

#### using关键字除了单纯引入命名空间外还有什么用处？

`using`最常用的就是为当前文件引入命名空间，但除此之外，它还具有全局引入`global using`（在整个程序集当中所有的文件都引入该命名空间）、静态引入`using static`（使用该方法引入的命名空间中的静态类和嵌套类型等可以直接进行访问）、`using 别名`（可以对引入的命名空间或类型取一个别名，让这个文件中任何地方都可以通过别名访问对应内容）。

#### global using全局引入

全局引入的命名空间只需要在一个位置引入，整个程序集都可以使用，例如将命名空间视为饮水机，全局引用则是小区直接购入公共饮水机，整个小区居民都可以使用，普通引用则是小区某一居民单独买一台饮水机回家，只有他家里人才能使用。

在VS创建项目时，许多的命名空间已经被自动设置为全局引入（如`System`、`System.Collections.Generic`等等），只需要在我们程序中点击小箭头就可以看见自动全局引入的命名空间：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240920165357246.png" alt="image-20240920165357246" style="zoom:50%;" />

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240920165435991.png" alt="image-20240920165435991" style="zoom:50%;" />

同时可以进行手动引入，例如我们在任意文件中写入全局引用`global using NamespaceStudy;`，此时会发现即使没有在文件中引入这个命名空间，依然可以访问里面的类型：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240920165730328.png" alt="image-20240920165730328" style="zoom:50%;" />

#### using static静态引入

静态引入命名空间可以让我们不用通过指定名称就i可以访问内部静态成员，例如静态引入`System.Console`，可以不显式的制定`Console`类就可以访问其中的函数：

```csharp
using static System.Console;

namespace CSharp_interface
{
    internal class Program
    {
        static void Main(string[] args)
        {
            WriteLine("Hello World!");
        }
    }
}
```

他等效于直接显式访问`WriteLine`函数：

```csharp
Console.WriteLine("Hello World!");
```

#### using 取别名

取别名可以简单理解为创建一个常量名，它的值为我们引入的命名空间或类型，基础的语法为`using 别名 = 命名空间或其中的类;`，例如将`System.Console`取别名为`CS`：`using CS = System.Console;`，此时我们可以直接通过别名来使用他，效果与直接使用相同：

```csharp
using CS = System.Console;
namespace CSharp_interface
{
    internal class Program
    {
        static void Main(string[] args)
        {
            CS.WriteLine("Hello World!");
        }
    }
}
```

## 9. 泛型Generic

### 9.1 泛型

#### 什么是泛型？

泛型相当于一个类型的占位符，它可以实现在编写代码时不进行显式的类型定义，而是在编译运行时进行自动类型定义。使用泛型可以很大程度提高代码复用率，再出现逻辑问题进行修改或更新时也会更加方便。

泛型可以看作是一辆公交车里面的乘客，在乘客没上车之前没人知道他会是男还是女还是其他小动物，但可以确信的是公交车肯定会有乘客。

#### 为什么使用泛型，使用object不是也可以进行不定类型的处理吗？

`object`在使用时需要进行拆箱装箱，对性能会有损耗，而泛型在直接使用时则不会进行装箱拆箱的操作可以节约系统性能。

#### 泛型的基础使用

泛型使用包括泛型类、泛型接口和泛型方法，他们都可以通过泛型来表示未确定的数据类型，定义泛型需要在类名或接口名或方法名后使用尖括号`<>`，并在其中填入泛型占位符，使用时可以直接使用占位符进行声明泛型变量或处理泛型数据。

例如如下代码中的定义：

```csharp
namespace 泛型Generic
{
    //泛型接口
    public interface IEat<TInstance>
    {
        //使用泛型的方法
        void Eat(TInstance instance);
    }

    //继承了泛型接口的 泛型类
    //继承泛型接口时必须指定泛型对应的类型
    public class Apple<TName, TPrice> : IEat<People>
    {
        //创建泛型变量
        public TName name;
        public TPrice price;
        public Apple(TName name, TPrice price)
        {
            this.name = name;
            this.price = price;
        }

        public void Eat(People instance)
        {
            Console.WriteLine($"{instance.name}正在吃价格为{price}叫做{name}的苹果");
        }
    }
}
```

我们对其进行简单的调用：

```csharp
Apple<string, float> apple = new("水晶红富士", 10.5f);
apple.Eat(new People("泠曦"));
```

结果为：

```C#
泠曦正在吃价格为10.5叫做水晶红富士的苹果
```

而对于上面的吃的函数，也可以不继承接口，使用泛型进行书写：

```csharp
public void Eat<T>(T instance) where T : People
{
    Console.WriteLine($"{instance.name}正在吃价格为{price}叫做{name}的苹果");
}
```

### 9.2 泛型约束

#### 什么是泛型约束？

泛型可以代表任何数据类型，但因为它本身的广泛性，在许多地方不进行类型限制可能会导致严重的程序逻辑错误，就比如吃这个方法，通常而言我们吃的是食物，但如果不进行约束限制，可能调用时传入的是一些不可名状的东西。因此出现了泛型约束，限制可以传入的类型大类，防止出现大的逻辑错误，除此之外，在未进行泛型约束的情况下也无法对泛型变量进行较为精细的操作，例如如下代码：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240925141110466.png" alt="image-20240925141110466" style="zoom:67%;" />

而当我们对它进行约束后，就可以进行比较：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240925141304123.png" alt="image-20240925141304123" style="zoom:67%;" />

#### 如何对泛型进行约束？

对泛型进行约束需要使用`where`关键字，在关键字后写上泛型符号和约束类型，多个约束类型可以用逗号隔开，语法为：

```csharp
where 占位符 : 约束类型
```

例如我们在`Animal`中的`Eat`方法对传入参数进行约束，必须要是`Food`类型或其子类：

```csharp
public class Animal
{
    public void Eat<TFood>(TFood food) where TFood : Food
    {
        food.BeEat();
    }
}
```

在传参时，如果传入的不是限制的类型，编译器将会报错：

![image-20240925134932055](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240925134932055.png)

只有当传入参数符合要求是才可以编译通过。

#### 有哪些类型的泛型约束？

约束的种类有很多，在官方文档中有13个（[类型参数的约束 - C# | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)），常用的有六个，分别为：

+ 值类型约束`where 泛型字母:struct`
+ 引用类型约束`where 泛型字母:class`
+ 存在无参构造函数`where 泛型字母:new()`
+ 某个类本身或其派生类`where 泛型字母:类名`
+ 某个接口`where 泛型字母:接口名`
+ 另一个泛型或其派生类`where 泛型字母:另一个泛型字母`

例如对刚刚的Eat进行约束，必须要是Food并且要有无参构造

![image-20240925135724453](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240925135724453.png)

## 10. 委托Delegate和事件Event

### 10.1 委托

#### 什么是委托？

委托是一种变量类型，如果将函数看作一个行为，委托就是用来存储这些行为的容器，这样讲可能比较抽象，简单举个例子，不同的人有不同的吃饭方法，然后我们有个委托名称叫开饭了，他存储了所有人的吃饭方法，当我们调用这个委托变量时会同时调用所有人的吃饭方法，就像是我们在楼下大喊一声“吃饭啦！”，这时每个人都会对吃饭这个方法进行处理，而不用单独的去叫某某某吃饭了。

#### 为什么需要委托变量？

在书写代码逻辑时，会存反复在在某一阶段或某一步骤批量调用不同类的处理函数，如果分开单独调用不仅占用篇幅，而且也不便于逻辑管理，尤其是在某一些类对象可能会被频繁的销毁和实例化时，使用委托将同意情况下的函数存储起来，合适的时候调用，不合适的时候仅作为变量存在，对象销毁时将该方法从变量中移除，这样将会大大减少工作量。

#### 如何使用委托？

委托类型定义的语法为`访问修饰符（默认为public） delegate 返回值 委托名(参数列表)`，使用时通过委托名声明对应委托变量即可。具体使用会写在后面，这里简单的举一个例子：实现玩家和怪物两个类，游戏开始时调用h开始函数，游戏结束时调用结束函数。

```csharpC#
public static class GameEventHandler
{
    //创建无参无返委托类型
    public delegate void GameEventManager();

    //定义游戏开始委托变量，默认不含有任何函数
    public static GameEventManager? gameStart = null;
    //定义触发，触发委托
    public static void OnGameStart()
    {
        //在非空情况下调用委托
        gameStart?.Invoke();
    }

    //定义游戏结束委托变量
    public static GameEventManager? gameOver = null;
    //定义游戏结束函数触发委托
    public static void OnGameOver()
    {
        //在非空情况下调用委托
        gameOver?.Invoke();
    }
}

public class Player
{
    public string name;
    //在构造函数中对委托进行注册
    public Player(string name)
    {
        this.name = name;
        GameEventHandler.gameStart += GameStart;
        GameEventHandler.gameOver += GameOver;
    }
    //设置移除角色时的方法，清除掉已注册委托
    public void Die()
    {
        GameEventHandler.gameStart -= GameStart;
        GameEventHandler.gameOver += GameOver;
    }
    //具体执行函数
    public void GameStart()
    {
        Console.WriteLine($"玩家{name}触发了游戏开始");
    }
    public void GameOver()
    {
        Console.WriteLine($"玩家{name}触发了游戏结束");
    }
}

public class Enemy
{
    public int id;
    public Enemy(int id)
    {
        this.id = id;
        GameEventHandler.gameStart += GameStart;
        GameEventHandler.gameOver += GameOver;
    }
    public void Die()
    {
        GameEventHandler.gameStart -= GameStart;
        GameEventHandler.gameOver -= GameOver;
    }
    public void GameStart()
    {
        Console.WriteLine($"敌人{id}触发了游戏开始");
    }
    public void GameOver()
    {
        Console.WriteLine($"敌人{id}触发了游戏结束");
    }
}
```

在main函数中进行简单调用：

```csharp
Player p = new("泠曦");
Enemy enemy1 = new(1);
Enemy enemy2 = new(2);

GameEventHandler.OnGameStart();

Console.WriteLine("游戏进行中");

enemy2.Die();
enemy2 = null;

GameEventHandler.OnGameOver();
```

执行结果如下：

```
玩家泠曦触发了游戏开始
敌人1触发了游戏开始
敌人2触发了游戏开始
游戏进行中
玩家泠曦触发了游戏结束
敌人1触发了游戏结束
```

### 10.2 委托的注册与清除

委托单单定义了类型是无法使用的，需要创建对应的变量才能进行操作，而创建变量的方法与正常变量声明的方法相同，所以不再单独写。

#### 委托的注册

委托变量是一个容器，他是用于装载函数，内部没有函数时是无法直接使用的，因此使用前要对委托进行注册。

注册的方式分为两种，一种直接使用对应方法名注册，另一种则是通过实例化委托对象来进行注册，例如上面的代码中注册委托可以有以下两种写法，这两种方法实现的效果相同，实际使用时选择其中一种即可：

```csharp
GameEventHandler.gameStart = new(GameOver);//通过实例化对象来注册
GameEventHandler.gameStart = GameStart;//直接添加对应函数进行注册
```

#### 清除委托

在一些已经用不到或逻辑上已经不存在的对象，我们希望触发委托时不会触发这些对象的方法，所以需要在特定函数中写入清除这些对象方法的代码，清除的时候不可以使用new实例化来清除，因为这代表了两个不同的委托对象，只能使用函数名来进行清除，如同上面代码中的：

```csharp
GameEventHandler.gameStart -= GameStart;
```

除此之外，还可以通过赋值为`null`来直接清空所有函数：

```csharp
GameEventHandler.gameStart = null
```

### 10.3 多播委托

#### 什么是多播委托？

多播委托即指一个委托对象存储了一些列函数，执行的时候相当于在向这些函数的对象进行广播，所以叫做多播委托，就例如最开始定义中讲的那样，在广播中大喊一声”开饭了“，就可以触发所有听见这个广播的对象的开饭函数。

#### 如何实现多播委托？

其实在前面也已经写出来了，多播委托可以通过使用`+`运算来注册，`-`运算来清除，这样实现的委托就是多播委托。

#### 使用多播委托需要注意些什么？

首先就是委托调用时是否包含函数的问题，就如同你在广播中喊一半天”开饭了“，结果没人理你，进楼才发现没人在里面一样，委托为空的时候将无法调用，运行时将会进行报错。

### 10.4 系统自带委托

#### 为什么会有系统自带委托？ 

委托使用时每次都需要先定义类型再声明委托变量并赋值，并且自定义委托有时需要去查找定义位置才能知道他是个委托变量而非一个函数，所以系统写入了两个大类的委托类型，我们可以直接进行使用。

#### 系统自带委托Action

对于无返回值的委托类型，可以直接使用系统自带的`Action`，他可以接受1~16个泛型作为委托传参类型，使用时直接用Action关键字创建委托变量即可，例如前面的`GameEventHandler`中，我们可以直接删去自定义委托类型，使用系统自带`Action`进行声明，它的使用效果与前面的代码相同：

```csharp
public static class GameEventHandler
{
    //定义游戏开始委托变量，默认不含有任何函数
    public static Action? gameStart = null;
    //定义触发，触发委托
    public static void OnGameStart()
    {
        //在非空情况下调用委托
        gameStart?.Invoke();
    }

    //定义游戏结束委托变量
    public static Action? gameOver = null;
    //定义游戏结束函数触发委托
    public static void OnGameOver()
    {
        //在非空情况下调用委托
        gameOver?.Invoke();
    }
}
```

如果需要传入参数，可以在`Action`关键字后添加尖括号注明类型进行使用，涵盖了16个参数类型，通常而言很难超出这个类型数量范围。

![image-20240927173250033](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240927173250033.png)

#### 系统自带含泛型返回值委托Func

`Func`和`Action`一样是系统自带的委托，不同的是`Func`支持一个泛型返回值，使用的时候会将最后一个泛型类型作为返回值类型。

![image-20240927173712159](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240927173712159.png)

例如如下代码，我们书写了两个有返回值的函数并打印他们的返回值，但实际运行的时候可能会发现只打印出了最后一个注册的委托的返回值，通过打断点查看执行会发现只有在执行到最后一个方法时，返回值才被返回到原语句中：

```csharp
internal class Program
{
    static void Main(string[] args)
    {
        Func<string> test = null;
        test += TestFunc1;
        test += TestFunc2;
        Console.WriteLine(test?.Invoke());
    }
    static string TestFunc1()
    {
        Console.WriteLine("in test1");
        return "TestFunc1";
    }
    static string TestFunc2()
    {
        Console.WriteLine("in test2");
        return "TestFunc2";
    }
}
```

输出结果：

```
in test1
in test2
TestFunc2
```

想要获得所有返回值必须要手动去执行每个方法，这时可以使用`GetInvocationList()`来获取委托列表，使用`DynamicInvoke()`来执行单个列表中的委托，例如将上面`Main`函数改为：

```C#
Func<string> test = null;
test += TestFunc1;
test += TestFunc2;
foreach (var fun in test.GetInvocationList())
    Console.WriteLine(fun.DynamicInvoke());
```

他将正确的打印返回值：

```
in test1
TestFunc1
in test2
TestFunc2
```

### 10.5 事件event

#### 什么是事件？

时间相当于一种特殊的委托，但是他无法在写有这个变量的类之外去执行，相当于我是B站UP主，事件变量是我的粉丝列表，你只能关注或取关我（只能添加或减少方法），无法去清空我的粉丝列表（无法直接赋值），也无法决定我如何对待我的粉丝（如何执行事件）。

#### 已经有委托了，为什么还需要事件？

委托相对来讲更加开放包容，但并不安全（因为无法限制他的执行方式以及他存储的方法），而使用事件则更加安全，外部只能存储或取消自己的方法，具体执行等交给我们自己封装，外部只需要调用对应函数，这让代码的安全性得到了保证，减少了程序的耦合，同时在执行出现问题时也能够快速进行定位。

#### 如何使用事件？

使用事件只需要在委托类型前加上`event`关键字即可，语法为`访问修饰符 event 委托类型 事件名`，例如可以把前面`GameEventHandler`代码修改为如下所示，可以发现它的使用与委托基本相同：

```csharp
public static class GameEventHandler
{
    public static event Action? GameStartEvent;
    public static void OnGameStartEvent()
    {
        GameStartEvent?.Invoke();
    }
    public static event Action? GameOverEvent;
    public static void OnGameOverEvent()
    {
        GameOverEvent?.Invoke();
    }
}
```

对于前面的执行语句，这里依然有同样的输出，但这样并不意味着委托和事件是相同的，因为我们并没有写到赋值语句，如果我们在外部对事件进行赋值操作，编译器将会报错，这是因为赋值操作是无法使用的，只有`+=`和`-=`才被允许使用，单独进行拆分为`= ... + ...`后同样不可以使用：

![image-20240929122532158](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240929122532158.png)

![image-20240929123134225](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240929123134225.png)

## 11. 匿名函数和Lambda表达式

### 11.1 匿名函数

#### 什么是匿名函数？

匿名函数顾名思义，是没有名字的函数，那么问题来了，前面不是说函数必须要有函数名吗？没有函数名它是如何定义如何使用的呢？

#### 没有函数名它是如何定义如何使用的呢？

对于匿名函数，它是一种比较特殊的函数，或者说来说是委托，因为它没有名称，所以需要使用一个容器来装载，后续通过这个容器来进行使用，没错，就是委托变量。

匿名函数哦不能够单独使用，一般是伴随着委托进行使用的。

#### 如何定义匿名函数呢？

定义匿名函数的语法如下，它使用委托关键字`delegate`进行声明并书写函数体，如果是无参匿名函数则可以直接省略括号。需要注意==最后必须写上分号`;`==：

```csharp
delegate(参数)
{
    函数体
    return 返回值;
};
```

但是就这样直接书写，编译器将会报错：

![image-20240929172350344](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240929172350344.png)

而我们使用一个委托来接受这个匿名函数，编译器将正常编译，运行时也可以正常执行，例如：

```csharp
Action action = delegate
 {
     Console.WriteLine("匿名函数");
 };
action();
```

他可以去正常执行内部语句：

![image-20240929173153701](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240929173153701.png)

对于有返回值的函数，我们需要使用含返回值的委托类型来接受，例如：

```csharp
Func<int, int, int> action = delegate (int a, int b)
 {
     return a + b;
 };
Console.WriteLine(action(5, 6));
```

他的执行结果为：

![image-20240929173716482](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240929173716482.png)

#### 将匿名函数作为参数传递

在一些情况下，我们使用的函数会需要传入一个特殊处理的方法，而这个方法可能并不会多次使用，只会在这个函数中使用一次，这时可以直接传入匿名函数，减少内存占用并且方便直接在操作位置进行修改，他的语法为在函数传参声明对应类型的委托，在调用时写入匿名函数即可，例如下面声明一个函数需要一个对输入整型进行处理的函数：

```csharp
static void TestFunc1(int a, Action<int> action)
{
    Console.WriteLine("传入参数为" + a);
    action(a);
}
```

在调用时我们希望这个函数会输出a的平方，所以可以像下面这样书写调用，此时将会先输出`传入参数为9`，再输出9的平方`81`：

```csharp
TestFunc1(9, delegate (int a)
{
    Console.WriteLine(a * a);
});
```

#### 将匿名函数作为返回值传递

将函数作为返回值传递可以用于针对不同参数返回不同的方法，调用时只需要通过一个函数来获取对应方法并使用即可，简化实际调用代码，对于返回匿名函数的语法，只需要将返回值修改为对应委托类型并返回一个函数即可，例如我们书写一个方法获取对两个参数进行处理的具体函数，该方法对字符串进行拼接后转换为整型，对整型直接进行相加，最终返回整数：

```csharp
static Func<object, object, int> GetAddTwoNum(Type type)
{
    if (type == typeof(string))
        return delegate (object num1, object num2)
        {
            return int.Parse((string)num1 + (string)num2);
        };
    else
        return delegate (object num1, object num2)
        {
            return (int)num1 + (int)num2;
        };
}
```

再执行该方法时，可以先使用一个变量来存储返回函数，再进行调用，例如：

```csharp
string num1 = "321";
string num2 = "231";
var fun = GetAddTwoNum(num1);
Console.WriteLine(fun(num1, num2));

int num3 = 321;
int num4 = 231;
fun = GetAddTwoNum(num3);
Console.WriteLine(fun(num3, num4));
```

最终结果为：

```
321231
552
```

除此之外，也可以不使用变量存储直接进行调用，它的使用效果与前面的相同：

```csharp
GetAddTwoNum(num1)(num1,num2)
```

### 11.2 Lambda表达式

#### 什么是Lambda表达式？

Lambda表达式其实就是匿名函数的简写，他省去了关键字`delegate`，只需要通过`()=>{};`即可创建一个匿名函数，在使用上它的用法与匿名函数不可以说完全相同，只能说没有任何区别。

#### Lambda表达式使用举例

在前面有一个如下所示的求和的函数：

```csharp
Func<int, int, int> action = delegate (int a, int b)
 {
     return a + b;
 };
```

我们将其简写为如下所示的Lambda表达式（Tips：当前面已经声明参数类型，Lambda表达式中参数列表可以省略类型名，直接书写对应参数名），他的执行结果与前面的函数一致：

```csharp
Func<int, int, int> action = (a, b) =>
{
    return a + b;
};
```

### 11.3 闭包

#### 什么是闭包？

闭包是在使用匿名函数时产生的占用本应该释放的资源延长其原本的生命周期时出现的情况，它可以窃取原本将要被释放掉的内存资源，让这些资源可以再次被使用，但运用不当则会导致大量本应该消亡的内存被错误地保留，造成堆栈内存溢出。

#### 形成闭包的方法/原因是什么？

一般而言，通过使用匿名函数或lambda表达式时可以造成闭包，例如我们写一个函数，该函数使用一个传入参数作为计算基数，在函数内有一个局部变量对基数进行特殊处理，处理完成后返回一个带有局部变量的函数用于后续处理，这时就发生了闭包现象，原来函数中的局部变量被保留了下来：

```csharp
static Func<int, int> SetNum(TestEntity te)
{
    int temp = te.baseNum * te.baseNum;
    return (i) =>
    {
        return i * temp;
    };
}
```

我们调用该函数，传入参数`3`，获取一个计算方法，并用它来计算传入数值为`4`、`5`、`6`的结果：

```csharp
var function = SetNum(new TestEntity() { baseNum = 3 });
Console.WriteLine(function(4));
Console.WriteLine(function(5));
Console.WriteLine(function(6));
```

结果为`36`、`45`、`54`。

这种情况下，`temp`的内存本应该在函数执行完后被释放，但因为有匿名函数使用了该内存，导致其无法正常释放。

#### 闭包是反复使用同一个变量会怎样？

按照我们的思考逻辑，一定会将这个变量所存储的值全部保留下来，但时间并不是，因为闭包时里面存有的数值是直接来自于那块内存，换句话说就是后续那块内存数值改变那么闭包中的数值也会改变，它的值取决于函数的结束态。

例如我们写入一个`for`循环，每次循环时存入对应下标，最后一次性调用存储函数打印存储结果：

```csharp
Action act = null;
for (int i = 0; i < 5; i++)
{
    act += () =>
    {
        Console.WriteLine(i);
    };
}
act.Invoke();
```

运行结果为：

![image-20241009171944488](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241009171944488.png)

而如果我们想要存储不同状态的变量值怎么办呢？答案是新建一个变量并存入对应的变量即可，例如将上面的第4到7行改为下面的代码，打印的结果就会变为`0`、`1`、`2`、`3`、`4`。

```csharp
int temp = i;
act += () =>
{
    Console.WriteLine(temp);
};
```

## 12. 可空类型nullable type

### 什么是可空类型？

在日常使用中，可能会存在我们程序中写了某一个类型的变量，但是实际获取时并没有这个类型的数据，如果强行实用程序进行数据处理会导致程序执行报错，而可空类型就帮我们解决了这个问题，他让我们设置的变量变得可以为空，避免了在获取数据阶段出现问题，那么，代价就是我们在使用时需要先进行判断是否为空才可以进行下一步操作。

### 如何创建可空类型变量？

创建可空类型变量的方式有两种，一种是较为复杂，语法为`Nullable<变量类型> 变量名`，另一种则简单粗暴，直接在变量类型后加上`?`即可，语法为`变量类型? 变量名`。例如下面两行代码，他们的实际结果一致：

```csharp
Nullable<int> n = null;
```

```csharp
int? n = null;
```

### 使用可空类型时需要注意些什么？

可空类型因为它本身可以为空的特性，所以在处理之前需要对其进行非空判定，否则将会导致代码逻辑出现错误，严重时程序会直接崩溃，例如我们有一个可空整型n，未进行判断便将其进行加操作，最后得出的结果为空：

```csharp
int? n = null;
n += 2;
Console.WriteLine("n的值为：" + n);
```

![image-20241011155000398](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241011155000398.png)



## 13. 多线程

#### 什么是进程？

在计算机中进程是

![image-20241028162010173](C:\Users\YimuZ\AppData\Roaming\Typora\typora-user-images\image-20241028162010173.png)

## 12. LINQ语言集查询

### 12.1 LINQ简介

#### 什么是LINQ？

语言集成查询 (LINQ) 是一系列直接将查询功能集成到 C# 语言的技术统称，它类似于数据库中的SQL查询语句，可以帮助我们快速准确的在一大堆数据里面翻出来我们想要的数据。

#### 对LINQ举个栗子？

这里简单的创建一个数据类`Employee`，并且在数据库中建立一张同数据的表用来做对比。

其中数据类的代码如下：

```csharp
public class Employee
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Address { get; set; }
    public Employee(int id, string name, string address)
    {
        Id = id;
        Name = name;
        Address = address;
    }
    public override string ToString()
    {
        return $"id:{Id},name:{Name},address:{Address}";
    }
}
```

数据库中建表SQL语句如下：

```sql
CREATE TABLE EMPLOYEE
(
    id int,
    employeeName varchar(5),
    address varchar(255)
);
```

在他们之中存入了相同的数据：

![image-20241010114617543](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241010114617543.png)

![image-20241010114640421](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241010114640421.png)

这时我们想要查找其中所有员工的名字，使用C#可以像下面这样写：

```csharp
var list =
    from employee in employees
    select employee.Name;
```

而在SQL语句则是这样：

```sql
SELECT employeeName FROM EMPLOYEE;
```

通过这种查询方式，他们获取的结果一致。

![image-20241010115531924](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241010115531924.png)

![image-20241010115548331](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241010115548331.png)

#### 介绍介绍LINQ查询关键字



## 10. 简单数据结构类

### 10.1 动态数组（ArrayList）

#### 什么是动态数组?

动态数组`ArrayList`是命名空间`System.Collections`中的简单数据结构类，就跟名称一样，它可以实现动态管理数组的功能，解决了数组一经创建便无法更改长度和大小的问题，同时，`ArrayList`还支持同时存储不同的类型的数据，进一步拓宽了数组的用途。

#### 为什么使用`ArrayList`？

+ `ArrayList`可以动态分配数组大小，使得对数组元素的增删查改更加方便，不再需要重新构建数组并赋值。
+ 实现了许多更加便利的方法，如直接在某一索引处增改元素、直接通过值来获取索引等。
+ 因为`ArrayList`的存储数据类型为`Object`，所以他能够存入任何类型数据，相比于数组有更强的拓展性。

#### `ArrayList`一定好用吗？

日常使用中==并不建议使用`ArrayList`==，虽然他可以动态扩容并且可以存储任何类型数据，但是它所采用的扩容方式为倍增扩容（在原来基础上增加一倍空间），在进行较大内存数据存储时，他将会产生更多的内存占用，例如我们在它初始内存为100的情况下存储了101个数据，他将扩容为200，造成了近百分之五十的内存浪费。参考[ArrayList 类 (System.Collections) | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/api/system.collections.arraylist?view=net-8.0#remarks)。

#### `ArrayList`的替代方法

对于相同类型的数据，使用`List<T>`进行存储，对于不同类型的数据存储，使用`List<Object>`。

### 10.2 栈Stack

#### 什么是栈？

栈是一种特殊的用于存储数据的数据结构，他的特点为



## 复杂数据结构类