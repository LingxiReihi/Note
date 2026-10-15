Python学习笔记

推荐课程:[2022新版黑马程序员python教程，8天python从入门到精通，学python看这套就够了](https://www.bilibili.com/video/BV1qW4y1a7fU/?share_source=copy_web&vd_source=f9746e047d5d7bc057c05c71dc1d25da)

# 第零章 Python安装和配置

## 0.1 下载和环境配置

### 0.1.1 下载Python

下载地址:https://www.python.org

![下载](https://s2.loli.net/2022/12/18/jJnPkDWIGwpKXFy.png)

### 0.1.2 安装

1.勾选`Add python.exe to PATH`(自动配置环境变量).

2.点击`Customize installation`自定义安装路径.

<img src="https://s2.loli.net/2022/12/18/yWxGRsQFvfbnhO3.png" alt="安装1" style="zoom: 67%;" />

直接点击`Next`.

<img src="https://s2.loli.net/2022/12/18/KjZSiM3o4EWICpe.png" alt="安装2" style="zoom:67%;" />

点击`Browse`选择安装位置,确定后点击`Install`安装.

<img src="https://s2.loli.net/2022/12/18/bJ3FuezhHA4ERrX.png" alt="安装3" style="zoom:67%;" />

点击`Disable path length limit`(取消文件路径长度限制),最后点击`Close`完成安装.

<img src="https://s2.loli.net/2022/12/18/4BK9CgdoGhOkNFX.png" alt="安装4" style="zoom:67%;" />

### 0.1.3 检查安装

键盘点击`Win + R`输入`cmd`打开控制符窗口,输入`py`(老版本输入`python`),可以看见当前版本信息并可以进行简单的代码书写.

![检查安装](https://s2.loli.net/2022/12/18/eZdJrTSRaDjMq2G.png)

## 0.2 Python解释器

### 0.2.1 概述

计算机本身只能识别二进制码如`01010001`,并不能识别代码中的`print`,`if`等等关键字,而程序员却只需要写出这些关键字计算机便能运行,这是因为有`Python解释器`将代码转换为二进制码并提交计算机运行.

安装和配置Python开发环境本质上就是在安装Python解释器.

### 0.2.2 解释器位置

解释器的位置在Python安装文件夹内,(例如我的在`D:\develop\Python3.11.1\python.exe`).

<img src="https://s2.loli.net/2022/12/18/ODjkFoEfMIlva87.png" alt="解释器" style="zoom: 50%;" />

## 0.3 集成开发环境配置

### Visual Studio环境配置

==若中文输出出现乱码,请更改IDE编码格式为`utf-8`.==

1.下载`Visual Studio安装器`

官网:https://visualstudio.microsoft.com/zh-hans/downloads/

2.打开安装器,选择`Visual Studio Community 2022`(免费社区版),选择安装.

3.勾选`Python开发`选项.

![IDE配置1](https://s2.loli.net/2022/12/18/qYVuPSTro4LbRCN.png)

4.选择`安装位置`,为`Visual Studio IDE`和`SDK`选择一个合适的位置(以便于打开和修改).

![IDE配置2](https://s2.loli.net/2022/12/18/c2XLAHiqCdsk8We.png)

5.点击安装

6.创建项目

+ 打开VS,选择`Python 应用程序`,点击`下一步`

  ![创建项目1](https://s2.loli.net/2022/12/18/suUzYdvFQolwg8I.png)

+ 修改`项目名称`为你想要的名称,更改`位置`(建议选择一个独立文件夹进行管理,不建议随手往C盘扔).,点击`创建`即可

  ![创建项目2](https://s2.loli.net/2022/12/18/H2e9GCKbIqw7Njm.png)

+ 创建成功样例

  ![创建项目3](https://s2.loli.net/2022/12/18/3m4cwbrDA56JIZC.png)

### Visual Studio Code环境配置

+ 1.下载安装包

  ![VSCodex1](https://s2.loli.net/2022/12/18/5wnFgeHlmfMZTPY.png)

+ 2.打开并安装

  选择合适的安装位置即可.

+ 3.拓展安装

  (1) 安装汉化包(可选安装)

  在左侧点击`拓展`图标或者键盘点击`Ctrl Shift X`打开拓展安装页面,在搜索栏输出`Chinese`,选择`简体中文`进行安装.(若安装后无任何变化,请参考下方`使用方法`进行操作并重启VSCode)

  ![VSCode2](https://s2.loli.net/2022/12/18/6UI7H1YiQWJr9nz.png)

  

  (2) 安装Python拓展

  相同位置输入`python`,下载安装即可.

  (3) 虚拟环境搭配 (避免项目臃肿),点击键盘`Ctrl Shift ~`打开控制台终端,输入以下内容

  ```
  python -m venv venv
  ```

  回车后,项目文件夹下方出现`venv`虚拟环境文件夹并弹出窗口询问是否应用于整个项目,点击`Yes`即可.

  ![VSCode3](https://s2.loli.net/2022/12/18/sv4BIEXmkcnFRxY.png)

  安装完成后运行文件,可以发现解释器目录发生了改变,从安装的路径改为了虚拟环境路径.

  ![VSCode4](https://s2.loli.net/2022/12/18/IysUfESnivlhZjt.png)

# 第一章  Python基础语法

## 1.1 字面量

### 1.1.1 含义

在代码中,==被写下来==的==固定的值==,称之为字面量.

#### 1.1.2 常见字面量类型

Python中常见的有6种值(数据)的类型

| 类型             | 描述                                                         | 说明                                                         |
| :--------------- | ------------------------------------------------------------ | :----------------------------------------------------------- |
| 数字(Number)     | 支持<br />整数(int)<br />浮点数(float)<br />复数(complex)<br />布尔(bool) | ==整数(int)==,如:10,-10<br />==浮点数(float)=,如:13.14,-13.14=<br />复数(complex),如:4+3j,以j结尾表示复数<br />布尔(bool)表达现实中的逻辑(真或者假),真用True表示,假用False表示,True和False本质上是数字1和0 |
| 字符串(String)   | 描述文本的一种数据类型                                       | ==字符串(string)由任意的字符组成==,如“112233”,”你好”,”abc$#%#@”等等 |
| 列表(List)       | 有序的可变序列                                               | Python中使用最频繁的数据类型,可有序记录一堆数据              |
| 元组(Tuple)      | 有序的不可变序列                                             | 可有序记录一堆不可变的Python数据集合                         |
| 集合(Set)        | 无序不重复集合                                               | 可无序记录一堆不重复的Python数据集合                         |
| 字典(Dictionary) | 无序key-value集合                                            | 可有序记录一堆key-value型的Python数据集合.                   |

### 1.1.3 基于`print语句`的各类字面量输出

源代码:

```python
# 输出整型
print(520)
# 输出浮点型
print(13.14)
# 输出字符串
print("你好")
```

输出:

```python
520
13.14
你好
Press any key to continue . . .
```

## 1.2 变量

### 1.2.1 什么是变量

在==程序运行时==,能==储存计算结果=或能表示值的抽象概念.=<br>简单来说,变量就是在程序运行时记录数据用.</br>

变量的值是可以改变的.

#### 1.2.2 变量定义格式

```python
变量名称 = 变量的值
```

举例:

```python
# 定义一个字符串变量和浮点型变量
food = "苹果"
price = 3.5
```

### 1.2.3 使用举例

```python
# 定义一个字符串变量和整型变量
food = "苹果"
price = 3.5

# print语句输出
print(food, "的价格是:", price)

# 若苹果打8折
price *= 0.8
print(food, "的价格是:", price)
```

输出结果:

```
苹果 的价格是: 3.5
苹果 的价格是: 2.8000000000000003
```

## 1.3 数据类型

参考:[Python六大基本数据类型介绍](http://t.csdn.cn/CK6qx)

| 数据类型      | 描述                                   | 举例                              |
| ------------- | -------------------------------------- | --------------------------------- |
| 整型(int)     | 正负整数,0等等都属于整型               | 1 , -1 , 0b1010(二进制)           |
| 浮点型(float) | 正负小数                               | 3.14 , -3.14 , 3.14e5(科学计数法) |
| 布尔型(bool)  | 逻辑真值(True)和假值(False)            | True , False                      |
| 复数(complex) | 用实数加虚数表示,只要包含虚数,就是复数 | 3-9j , 5+9j                       |
| 字符串(str)   | 用单,双,三引号引起来的内容就是字符串   | ‘1’ , “2” , “”“3”“”               |
| 列表(list)    | 有序储存数据                           | [1, 2.55, “1233”]                 |
| 元组(tuple)   | 有序储存不可变元素                     | (1, 2.55, “1233”)                 |
| 集合(set)     | 无需储存不重复元素                     | {1, 2.55, “1233”}                 |
| 字典(dict)    | 储存一对键值对                         | {“姓名”:”一木折曦” ,”性别”:”男” } |

使用举例

### 1.3.1 整型(int)

```python
# 普通整型
intv = 12
print(intv, type(intv))
intv = -13
print(intv, type(intv))

# 二进制
intv = 0b0110
print(intv, type(intv))
```

输出结果

```
12 <class 'int'>
-13 <class 'int'>
6 <class 'int'>
```

### 1.3.2 浮点型(float)

```python
# 普通浮点型
floatv = 3.14
print(floatv, type(floatv))

# 科学计数法
floatv = 3.14e5
print(floatv, type(floatv))
```

输出结果

```
3.14 <class 'float'>
314000.0 <class 'float'>
```

### 1.3.3 布尔型(bool)

```python
# 布尔变量
boolv = True
print(boolv, type(boolv))
```

输出结果

```
True <class 'bool'>
```

### 1.3.4 复数(complex)

```python
# 复数
complexv = 16-5j
print(complexv, type(complexv))
complexv = complex(2, 5j)
print(complexv, type(complexv))
```

输出结果

```
(16-5j) <class 'complex'>
(-3+0j) <class 'complex'>
```

### 1.3.5 字符串(str)

#### 1.3.5.1 字符串的三种定义方式

```python
# 方法一
变量名 = '内容'
# 方法二
变量名 = "内容"
# 方法三
变量名 = """内容"""
```

举例:

```python
str1 = '123'
str2 = "沐"
str3 = """
这里是\t字符串\n嗯,是字符串
"""
str4 = r"这里\t是无法使用转义字符的字符串" # 元字符串
print(str1, type(str1))
print(str2, type(str2))
print(str3, type(str3))
print(str4, type(str4))
```

输出结果

```
123 <class 'str'>
沐 <class 'str'>

这里是  字符串
嗯,是字符串
 <class 'str'>
这里\t是无法使用转义字符的字符串 <class 'str'>
```

#### 1.3.5.2 字符串的拼接

在编程时,有时会需要将多个字符串拼接成一个字符串使用,这时只需要在中间添加`+`运算符即可.

语法

```python
结果字符串 = 字符串1 + 字符串2
```

示例

```python
strv1 = '520'
strv2 = '1314'
strv3 = strv1 + strv2
print(strv3, type(strv3))
```

输出结果

```
5201314 <class 'str'>
```

字符串也可以与其他类型拼接,但首先需要将其转换为字符串.

举例

```python
strv1 = '520'
strv2 = '1314'
strv3 = strv1 + strv2
intv = 7
print(strv3+str(intv))
```

输出结果

```
52013147
```

#### 1.3.5.4 字符串格式化

##### 格式化方法一

但是实际使用中,可能会觉得每次要将其他的类型变量转换成字符串再拼接显得十分复杂繁琐,这是我们可以用占位符进行格式化,然后拼接.

语法:

```python
目标字符串 = "类容%s内容%i内容%f..." % (占位数据1,占位数据2,占位数据3...(也可以写表达式))
```

举例:

```python
'''
占位符
%s 将后续补入内容转化为str类型拼接
%i(%d) 将后续内容转换为int类型拼接
%f 将后续内容转化为float类型拼接
'''

name = "沐"
age = 19
sex = "男"

msg = "我的名字是%s,年龄%i,性别%s" % (name, age, sex)
print(msg, type(msg))
```

输出结果:

```
我的名字是沐,年龄19,性别男 <class 'str'>
```

##### 字符串格式化-精度控制

在使用字符串时,我们有时会遇到一些特殊需求,如精确到小数点后x位,或者每一个填入内容至少要占用几个空格以保证文本美观.精度控制的占位符非常简单,只需要在`%`和字母之间加上两个数字`m,n`,其中,`m`代表宽度即最小输出宽度,余位用空格补齐,`.n`代表精度.其中,`m`可以省略不写.

使用举例:

```python
name = "沐"
age = 19
sex = "男"

msg = "我的名字是%7s,年龄%8.4f,性别%4s" % (name, age, sex)
print(msg, type(msg))
```

输出结果:

```
我的名字是      沐,年龄 19.0000,性别   男 <class 'str'>
```

明显的看见,沐占用了7格,年龄精确到了小数点后四位且占位8格,男占位4格.

##### 格式化方法二

语法：

```python
字符串变量 = f"部分元素{部分其他元素}"
#中括号内也可以写表达式
```

使用举例：

```python
msg = f"我的名字是{name},年龄{age},性别{sex}"
print(msg, type(msg))
```

输出结果：

```
我的名字是沐,年龄19,性别男 <class 'str'>
```

### 1.3.6 列表(list)

```python
# 列表
listv = [] # 空列表
listv.append(12)
listv.append(11)
print("列表的第0个元素是", listv[0])
print("列表的第一个元素是", listv[1])
print("列表", listv, type(listv))
```

输出结果

```
列表的第0个元素是 12
列表的第一个元素是 11
列表 [12, 11] <class 'list'>
```

### 1.3.7 元组(tuple)

```python
# 元组
tuplev = (18, "520", 13+14j)
print(tuplev[1])
print(tuplev[-1])
print(tuplev, type(tuplev))
"""
元组不支持赋值与修改
"""
```

输出结果

```
520
(13+14j)
(18, '520', (13+14j)) <class 'tuple'>
```

### 1.3.8 集合(set)

```python
# 集合
setv = set()  # 定义空集合
setv.add(123)
setv.add(456)
print(setv, type(setv))
setv.add(123)  # 添加重复元
print(setv, type(setv))
"""
特点:无序,不可修改,自动去重
"""
```

输出结果

```
{456, 123} <class 'set'>
{456, 123} <class 'set'>
```

### 1.3.9 字典(dict)

```python
# 字典
dictv = {}  # 定义空字典
dictv.update({"姓名": "沐"})  # 添加一个键值对
dictv.update({"年龄": "19"})
print(dictv["姓名"])  # 获取key对应的value
print(dictv["年龄"])
print(dictv, type(dictv))
```

输出结果

```
沐
19
{'姓名': '沐', '年龄': '19'} <class 'dict'>
```

## 1.4 类型转换

不同数据类型的变量往往可以相互转换以便于后续关于这些值的一些操作.但不正确的进行转换将会影响到整个程序的运行.

### 1.4.1 转换为整型

常见的数据类型中,`字符串(str)`和`浮点型(float)`可以转换为整型.

并不是所有字符串都可以转换为整型,转换的字符串必须==只含有数字==才可以进行转换.

语法

```python
变量名 = int(需要转换的变量或变量名)
```

示例

```python
strv = "12123"  # 定义字符串
floatv = 13.14  # 定义浮点数
int1 = int(strv)  # 强制转换为整型
print(int1, type(int1))
int2 = int(floatv)
print(int2, type(int2))
```

输出结果

```
12123 <class 'int'>
13 <class 'int'>
```

### 1.4.2 转换为浮点型

`字符串(str)`和`整型(int)`可以转换为浮点型.

语法

```python
变量名 = float(需要转换的变量或变量名)
```

示例

```python
strv = "13.14"
intv = 520
floatv = float(strv)
print(floatv, type(floatv))
floatv = float(intv)
print(floatv, type(floatv))
```

输出结果

```
13.14 <class 'float'>
520.0 <class 'float'>
```

### 1.4.3 转换为字符串

语法

```python
变量名 = str(需要转换的变量或变量名)
```

示例

```python
intv = 520
floatv = 13.14
strv = str(intv)
print(strv, type(strv))
strv = str(floatv)
print(strv, type(strv))
```

输出结果

```
520 <class 'str'>
13.14 <class 'str'>
```

## 1.5 标识符及几种常见命名方法

在代码中,许多变量函数等需要我们给他命名以方便使用,成这个名字为标识符

### 1.5.1 可包含字符

标识符可以包含`数字`,`字母`,`汉字`(一般而言不建议用汉字命名),`下划线(_)`,可以用这些字符进行任意组合,但是==数字不能位于标识符最前面==.

### 1.5.2 命名要求

+ 要求==简单易懂,见文知意==,不建议过分冗杂增大书写难度或过分简约增大阅读难度.
+ ==不能与关键字(如`if`,`print`等)相同==.
+ 区分大小写.

### 1.5.3 下划线命名法

下划线命名法要求所有字母小写,单词与单词之间用`_`隔开.

举例

```python
people_name = "沐"
people_age = 19
```

### 1.5.4 小驼峰命名法

首字母小写,其余单词首字母大写.

举例

```python
peopleName = "沐"
peopleAge = 19
```

### 1.5.5 大驼峰命名法

所有单词首字母均大写.

举例

```python
def SetPeopleName()
```

## 1.6 运算符

### 1.6.1 算术(数学)运算符

| 运算符 | 描述       | 实例                                                         |
| ------ | ---------- | ------------------------------------------------------------ |
| +      | 加         | 两个整型相加`10 + 20`输出结果`30`                            |
| -      | 减         | 两个数相减`10 - 20`输出结果`-10`                             |
| *      | 乘         | 两个数相乘或返回一个重复的字符串`“12” * 3`输出结果`“121212”` |
| /      | 除         | 两个数相除`9 / 2`输出结果`4.5`                               |
| //     | 取整除     | 返回商的整数部分`9.0//2.0`输出结果`4.0`                      |
| %      | 取模(取余) | 求余数`9 % 2`输出结果`1`                                     |
| **     | 指数       | `2**3`输出结果`8`,`3**2`输出结果`9`                          |

### 1.6.2 赋值运算符

| 运算符 | 描述       | 实例                                                         |
| ------ | ---------- | ------------------------------------------------------------ |
| =      | 赋值运算符 | 将`=`右边的值赋给左边,如`num = 1 + 7`,运行完这行代码后,`num`的值为`8` |

### 1.6.3 复合赋值运算符

| 运算符 | 描述             | 实例                        |
| ------ | ---------------- | --------------------------- |
| +=     | 加法赋值运算符   | `a += b`等价于`a = a + b`   |
| -=     | 减法赋值运算符   | `a -= b`等价于`a = a - b`   |
| *=     | 乘法赋值运算符   | `a *= b`等价于`a = a * b`   |
| /=     | 除法赋值运算符   | `a /= b`等价于`a = a / b`   |
| %=     | 取模赋值运算符   | `a %= b`等价于`a = a % b`   |
| **=    | 幂赋值运算符     | `a **= b`等价于`a = a ** b` |
| //=    | 取整除赋值运算符 | `a //= b`等价于`a = a // b` |

## 1.7 键盘数据输入（input）

### input基础使用

语法：

```python
s = input([prompt])	# prompt为输入提示，可选填写
```

注意：input接收到的输入==默认为字符串类型==，需要数字或其它类型需要进行类型转换。

使用举例：

```python
name = input("name: ")
print(f"hello ,{name}")

# 运行结果
# name: 泠曦
# hello ,泠曦
```

### input多参数输入

在需要一次性输入多个参数时，可以直接在`input`语句后添加`split()`对输入的字符串进行拆分，在前面准备对应数量的变量名进行接收，举例：

```python
a, b, c = input("请输入三角形三边的长：").split()
print(f"三角形三边长分别为{int(a)},{int(b)},{int(c)}")

# 运行结果
# 请输入三角形三边的长：3 4 5
# 三角形三边长分别为3,4,5
```

# 第二章 Python判断语句与循环语句

## 2.1  布尔类型与比较运算符

布尔类型底层为一位二进制，其中`0`为假（false），`1`为真（true）；比较运算符则用于对我们需要的条件进行判断，他的返回结果为一个布尔值。

| 运算符 | 描述                                                         | 实例                  |
| :----- | :----------------------------------------------------------- | :-------------------- |
| ==     | 等于 - 比较对象是否相等                                      | (a == b) 返回 False。 |
| !=     | 不等于 - 比较两个对象是否不相等                              | (a != b) 返回 True。  |
| >      | 大于 - 返回x是否大于y                                        | (a > b) 返回 False。  |
| <      | 小于 - 返回x是否小于y。所有比较运算符返回1表示真，返回0表示假。这分别与特殊的变量True和False等价。注意，这些变量名的大写。 | (a < b) 返回 True。   |
| >=     | 大于等于 - 返回x是否大于等于y。                              | (a >= b) 返回 False。 |
| <=     | 小于等于 - 返回x是否小于等于y。                              | (a <= b) 返回 True。  |

使用举例

```python
# 布尔变量与运算符
bool1 = True
bool2 = False
print(f"bool1:{bool1}类型为{type(bool1)},bool2:{bool2}类型为{type(bool2)}")
a = 10
b = 20
print(f"{a}=={b}:{a == b}")
print(f"{a}!={b}:{a != b}")
print(f"{a}>{b}:{a > b}")
print(f"{a}<{b}:{a < b}")
print(f"{a}>={b}:{a >= b}")
print(f"{a}<={b}:{a <= b}")
```

输出结果：

```
bool1:True类型为<class 'bool'>,bool2:False类型为<class 'bool'>
10==20:False
10!=20:True
10>20:False
10<20:True
10>=20:False
10<=20:True
```

## 2.2 if_elif_else

`if_elif_else`为条件判定语句，代码形式一般如下：

```python
if 条件一:
    条件判定成功执行语句1
elif 条件二:
    条件判定成功执行语句2
else:
    条件均不满足则执行语句3
```

在上面的代码中，执行逻辑为：如果满足条件一则执行语句1，满足条件二则执行语句2，均不满足则执行语句3.

具体实例：

```python
num1, num2 = input("Enter two num: ").split()
num1 = int(num1)
num2 = int(num2)
if num1 > num2:
    print(num1, "is greater than", num2)
elif num1 < num2:
    print(num1, "is less than", num2)
else:
    print(num1, "is equal to", num2)
```

运行结果：

```
Enter two num: 10 11
10 is less than 11

Enter two num: 10 10
10 is equal to 10

Enter two num: 11 10
11 is greater than 10
```

## 2.3 match...case

`match...case`类似于其它语言的`switch...case`，`match `后的对象会依次与 `case `后的内容进行匹配，如果匹配成功，则执行匹配到的表达式，否则直接跳过，`_ `可以匹配一切内容。

```python
match subject:
    case <pattern_1>:
        <action_1>
    case <pattern_2>:
        <action_2>
    case <pattern_3>:
        <action_3>
    case _:
        <action_wildcard>
```

使用举例：给用户提示输入三个套餐选择，根据输入匹配套餐

```python
select = int(input("选择一个套餐：1. 套餐A 2.套餐B 3.套餐C\n"))
match select:
    case 1:
        print("套餐A")
    case 2:
        print("套餐B")
    case 3:
        print("套餐C")
    case _:
        print("输入错误")
```

```python
选择一个套餐：1. 套餐A 2.套餐B 3.套餐C
1
套餐A
```

## 2.4 while循环

`while`语句会让程序满足条件的情况下一直执行while内部的代码块，语法大致如下：

```python
while 循环条件:
    满足条件执行的代码块
```

使用举例：循环输出0~5

```python
print("while循环0~5")
num = 0
while num <= 5:
    print(num)
    num += 1
```

输出结果：

```
while循环0~5
0
1
2
3
4
5
```

在循环最后可以加上一个`else`语句，他将会在循环正常结束后执行，例如，在上面代码最后加上

```python
else:
    print("循环结束")
```

输出结果会变为

```
while循环0~5，最后提示循环结束
0
...
5
循环结束
```

## 2.5 for循环

Python for 循环可以遍历任何可迭代对象，如一个列表或者一个字符串。他的基础语法结构如下（else语句可选）：

```python
for <临时变量> in <待处理数据集>:
    <处理语句>
else:
    <处理语句>
```

使用举例：<br>1.输出0~5

```python
for num in range(0, 6):
    print(num)
```

2.依次输出“Hello World”内的字符（输出结果会包含空格）

```python
for w in "Hello World!":
    print(w)
```

## 2.6 range函数

range函数可以让我们获得一个数字序列，它的语法如下：

```python
range(num)					#返回从0开始，num结束（不包括num）的数字序列
range(start, end)			#返回从start开始，end结束（不包括end）的数字序列
range(start, end, step)		#返回从start开始，end结束（不包括end），以step为步长递增的数字序列
```

这里只示例三个参数的使用及结果：

```python
for a in range(0, 10, 3):	#输出0到10，以3为步长增长的数字序列
    print(a)
```

输出结果：

```
0
3
6
9
```

##  2.7 break和continue语句

循环语句中使用break或continue可以对满足某些条件的情况进行跳出循环或跳过后续语句的操作。

### 2.7.1 break

break可以直接使程序跳出当前循环语句，不再进行后续语句的操作，如果循环语句最后包含else，else也不会被执行。

```python
for b in range(0, 10):
    if b == 5: break
    print(b)
else:
    print("循环结束")
```

```
0
1
2
3
4
```

### 2.7.2 continue

continue可以让程序跳过这次循环中后续还没执行的语句，直接进行下一次循环。

```python
# 输出0~10中的奇数
for b in range(0, 10):
    if (b % 2) == 0: continue
    print(b)
else:
    print("循环结束")
```

```
1
3
5
7
9
循环结束
```

# 第三章 列表和元组

## 3.1 序列

Python中内置了多种序列，其中列表和元组是最常用的两种序列。

列表和元组最大的区别在于：==列表元素是可以修改的，而元组元素则不能随意修改==。所以列表适合需要随时向序列中增减元素的场景，元组则适合定义某种基准或其他用处的不可对元素进行修改的场合。

## 3.2 序列操作

对于序列，Python提供了**索引**、**切片**、**相加**、**相乘**和**成员检查资格**的通用操作，同时，也提供了内置函数，用于确定序列长度、找出最大最小值等操作。

### 3.2.1 索引

序列中的元素同其他语言中的数组一样，都有它对应的下标，并且也和其它语言一样（Lua等少数语言除外）下标从0开始。这个代表元素位置的下标即为**索引（indexing）**，可以通过索引来获取或更改特定的元素。

例如，我们可以通过获取一个单词中索引为0的元素来获取他的首字母：

```python
print("Hello"[0])

# 运行结果为打印 H
```

索引除了大于等于0的整数，也可以使用负数，使用负数时将会从序列右侧（尾部）向前查找，如我们想要获得单词索引为-1的元素，它将返回最末的元素，也就是`“o”`：

```python
print("Hello"[-1])

# 运行结果为打印 o
```

### 3.2.2 切片

#### 基础使用

除了使用单个索引获取单个元素外，我们也可以用多个索引来获取某一段区间内的元素，这就是**切片（slicing）**，他的基础使用方法为使用两个索引，中间用冒号隔开，即可获得这第一个索引开始第二个索引结束（不包含第二个索引元素）的一部分。

例如，我们有一个nums序列，我们想要获得它索引为2到8的元素：

```python
nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(nums[2:8])
```

```
[3, 4, 5, 6, 7, 8]
```

切片的索引也可以为负数，例如我们想要获得倒数第三个元素到最后一个元素中的序列：

```python
print(nums[-3:-1])
```

```
[8, 9]
```

但通过负数索引，并不会获得最后一个元素，但如果使用0作为第二个索引，是不是就可以获得包含最后一个元素在内的序列呢？其实并不会：

```python
print(nums[-3:0])
```

```
[]
```

理由其实很简单，再在通过切片获取序列元素时，第一个索引位置如果位于第二个索引位置之后，计算机便不能获取第一个索引往后一直到第二个索引的元素，所以返回一个空序列。

#### 缩写

而对于从头开始或者从末尾结束，Python提供了一种简单的缩写，即：**省略第一个索引表示从序列第一个元素开始截取，省略第二个索引表示一直截取到最末尾一个元素（包含最末尾的元素）**。

例如，我们获取从开始到索引为5的元素与从-3到最末尾的元素：

```python
print(nums[:5])
print(nums[-3:])
```

```
[1, 2, 3, 4, 5]
[8, 9, 10]
```

如果我们将两个索引都省略掉，获得的就是整个序列。

#### 步长

除了可以通过两个索引来获取序列以外，还可以设置第三个参数**步长**，这个数值将告诉程序我们获取元素的间隔，而当我们省略不写的时候，该参数为1，

例如，我们可以通过下面的写法，获得序列中第0，2，4...元素：

```python
print(nums[::2])
```

```
[1, 3, 5, 7, 9]
```

步长可以是除0以外的数（当他为0时无法向前获取元素），当步长为负数时，表示从索引区间反向（从尾部到头部）获取元素。

### 3.2.3 序列相加

不同的序列可以通过`+`运算符进行拼接。

```python
print([1, 2, 3] + [4, 5, 6])
```

```
[1, 2, 3, 4, 5, 6]
```

但一般情况下，不同类型的序列不能进行拼接，如不可以将一个数字列表和字符串进行拼接。

```python
print("Hello" + [4, 5, 6])
```

```
    print("Hello" + [4, 5, 6])
          ~~~~~~~~^~~~~~~~~~~
TypeError: can only concatenate str (not "list") to str
```

### 3.2.4 乘法

序列可以对一个整数做乘法，这会让这一个序列连续重复。

```python
print("Hello" * 3)
```

```
HelloHelloHello
```

使用这种方法可以快速对一些序列进行处理，如快速初始化、快速重置等等。

### 3.2.5 成员资格（成员检测）

我们可以**使用布尔运算符`in`来检测某一元素是否包含在序列当中**，如果包含在序列中，它将返回布尔值True，没有包含在序列中则会返回False。

```python
hanasi = "Hello World!"
if("Hello" in hanasi):
    print('include "Hello"')
else:
    print('not include "Hello"')
```

```
include "Hello"
```

### 3.2.6 获取长度、最小值、最大值

要获取序列的长度、最小值或者最大值，Python内置了len、max、min三个函数：

```python
nums = [100, 200, 333, -5]
print(f"len:{len(nums)}")
print(f"max:{max(nums)}")
print(f"min:{min(nums)}")
```

```
len:4
max:333
min:-5
```

## 3.3 列表

### 3.3.1 list

字符串并不能进行修改，但我们可以将其转化为一个列表，在修改元素后再将它转换回字符串，这样便可以完成对它的修改：

```python
s = "Hello"
print(type(s))
s = list(s)  # 将字符串转换为列表
print(type(s))
s[1] = "a"  # 修改列表中的元素
s = "".join(s)  # 将列表转换为字符串
print(s)
print(type(s))
```

```
<class 'str'>
<class 'list'>
Hallo
<class 'str'>
```

### 3.3.2 列表的基本操作

#### 修改列表（给元素赋值）

需要修改某一个元素的值或给某一个元素赋值，只需要使用`=`即可，这里不再进行举例，但需要注意的是，赋值对象不可以是超出范围的对象，

#### 删除元素

如果需要删除列表中的元素，我们可以使用`del`语句，删除后对应元素将永久消失，列表的长度也会重新进行更新。

```python
nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(f"nums[0]: {nums[0]},len(nums):{len(nums)}")
del nums[0]
print(f"nums[0]: {nums[0]},len(nums):{len(nums)}")
```

```
nums[0]: 1,len(nums):10
nums[0]: 2,len(nums):9
```

#### 切片赋值

前面介绍过通过切片的方式获取某一段序列的值，除了获取某一段的值，我们还可以对某一段元素直接进行替换。

```python
nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(f"nums:{nums},len(nums): {len(nums)}")
nums[1:5] = [11, 33, 22]
print(f"nums:{nums},len(nums): {len(nums)}")
```

```
nums:[1, 2, 3, 4, 5, 6, 7, 8, 9, 10],len(nums): 10
nums:[1, 11, 33, 22, 6, 7, 8, 9, 10],len(nums): 9
```

我们也可以在不改变原有元素的同时，对列表进行插入操作

```python
nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(f"nums:{nums},len(nums): {len(nums)}")
nums[2:2] = [520, 1314]
print(f"nums:{nums},len(nums): {len(nums)}")
```

```
nums:[1, 2, 3, 4, 5, 6, 7, 8, 9, 10],len(nums): 10
nums:[1, 2, 520, 1314, 3, 4, 5, 6, 7, 8, 9, 10],len(nums): 12
```

### 3.3.3 列表相关的方法（函数）

| 方法名   | 含义                           | 方法名    | 含义                                   |
| -------- | ------------------------------ | --------- | -------------------------------------- |
| `append` | 添加元素到末尾                 | `insert`  | 插入元素                               |
| `clear`  | 清空列表内容                   | `pop`     | 从列表中删除一个元素，默认为最末尾元素 |
| `copy`   | 复制列表                       | `remove`  | 删除第一个为指定值的元素               |
| `count`  | 元素出现的数量                 | `reverse` | 反转列表                               |
| `extend` | 将多个值附加到列表末尾         | `sort`    | 对列表进行排序，默认为从小到大         |
| `index`  | 查找指定值第一次出现的索引位置 |           |                                        |

#### `append`

`append`方法会就地修改列表，在列表末尾添加元素，所以它并不会返回任何值，只会返回`None`。

```python
nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(f"nums[-1]:{nums[-1]},len(nums): {len(nums)}")
nums.append(15)
print(f"nums[-1]:{nums[-1]},len(nums): {len(nums)}")
```

```
nums[-1]:10,len(nums): 10
nums[-1]:15,len(nums): 11
```

#### `clear`

`clear`会就地清空列表的所有内容

```python
nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(f"nums:{nums},len(nums): {len(nums)}")
nums.clear()
print(f"nums:{nums},len(nums): {len(nums)}")
```

```
nums:[1, 2, 3, 4, 5, 6, 7, 8, 9, 10],len(nums): 10
nums:[],len(nums): 0
```

#### `copy`

常规的赋值操作只是名称关联的行为，两个变量名指向的内容为同一个列表，`copy`则会构建一个列表的副本，让被赋值的变量名指向的列表变为经过copy产生的副本，这样便可以对他们分别进行操作（类比于`C/C++`的浅拷贝和深拷贝）。

使用常规赋值：

```python
a = [1, 2, 3, 4]
b = a
print(f"a:{a},b:{b}")
b.append(5)
print(f"a:{a},b:{b}")
```

```
a:[1, 2, 3, 4],b:[1, 2, 3, 4]
a:[1, 2, 3, 4, 5],b:[1, 2, 3, 4, 5]
```

copy：

```python
a = [1, 2, 3, 4]
b = a.copy()
print(f"a:{a},b:{b}")
b.append(5)
print(f"a:{a},b:{b}")
```

```
a:[1, 2, 3, 4],b:[1, 2, 3, 4]
a:[1, 2, 3, 4],b:[1, 2, 3, 4, 5]
```

#### `count`

`count`可以用于计算特定元素出现的次数：

```python
a = [1, 2, 2, 3, 4]
print(f"1出现的次数:{a.count(1)}，2出现的次数:{a.count(2)}")
```

```
1出现的次数:1，2出现的次数:2
```

#### `extend`

`extend`可以就地同时将多个元素添加到列表末尾，他与列表拼接、切片末尾插入列表效果相同，不过拼接效率相对较低，因为他无法就地修改列表，需要重新赋值。

```python
a = [1, 2, 2, 3, 4]
b = [[100, 20], 15, 32]
a.extend(b)
print(a)
```

```
[1, 2, 2, 3, 4, [100, 20], 15, 32]
```

#### `index`

`index`可以用于寻找指定元素第一次出现的位置索引，但是当指定的值并不包含在列表中时，程序将会报错

```python
c = ["hello", "python", "hello", "world"]
print(f'index of "hello": {c.index("hello")}')
```

```
index of "hello": 0
```

```python
print(f'index of "hell": {c.index("hell")}')	# 查找不包含在内的元素时，程序报错无法运行
```

```
    print(f'index of "hell": {c.index("hell")}')
                              ^^^^^^^^^^^^^^^
ValueError: 'hell' is not in list
```

#### `insert`

`insert`函数也是对列表进行就地插入，它包含两个参数，第一个参数为插入元素的位置，第二个参数为插入元素的值。

```python
c = ["hello", "python", "hello", "world"]
c.insert(4, "halo")
print(c)
```

```
['hello', 'python', 'hello', 'world', 'halo']
```

#### `pop`

`pop`会从列表中删除一个指定位置的元素（没有指定则默认最末尾的元素），然后返回被删除的值。

```python
c = ["hello", "python", "hello", "world"]
pop_1 = c.pop()
pop_2 = c.pop(0)
print(f"c: {c}, pop_1: {pop_1}, pop_2: {pop_2}")
```

```
c: ['python', 'hello'], pop_1: world, pop_2: hello
```

#### `remove`

`remove`可以就地删除第一个出现的指定值，但如果列表中不包含这个值，程序将会报错。

```python
c = ["hello", "python", "hello", "world"]
c.remove("hello")
print(f"c: {c}")
```

```
c: ['python', 'hello', 'world']
```

#### `reverse`

`reverse`可以将列表进行逆转，但不会返回任何值。

```python
c = ["hello", "python", "hello", "world"]
c.reverse()
print(f"c: {c}")
```

```
c: ['world', 'hello', 'python', 'hello']
```

#### `sort`与`sorted`

`sort`会就地对列表进行排序，而`sorted`则更像是先将序列复制转化为列表，再对其进行排序。

sort排序示例：

```python
a = [12, 56, 55, 96, 32, 565, 6]
a.sort()
print(a)
```

```
[6, 12, 32, 55, 56, 96, 565]
```

sorted排序示例：

```python
a = [12, 56, 55, 96, 32, 565, 6]
b = sorted(a)
print(a)
print(b)
```

```
[12, 56, 55, 96, 32, 565, 6]
[6, 12, 32, 55, 56, 96, 565]
```

#### 高级`sort`排序方法

`sort`还可以接受两个可选参数：`key`和`reverse`，其中key指定排序时比较的值，reverse则是反向排序（从大到小）。

```python
w = ["banana", "apple", "orange", "pear", "grape"]
w.sort(key=len)  # 按照单词长度排序
print(w)
w.sort(key=len, reverse=True) # 按照单词长度排序，降序
print(w)
```

```
['pear', 'apple', 'grape', 'banana', 'orange']
['banana', 'orange', 'apple', 'grape', 'pear']
```

### 3.3.4 元组（不可修改）

元组定义非常简单，只需要用逗号隔开即可，也可以用圆括号包裹起来。

```python
t = 1, 2, 3
print(t)
```

```
(1, 2, 3)
```

而如果要定义只有一个元素的元组，需要在这个元素后面打上逗号，只用圆括号包裹起来并不能将其定义为元组。

```python
print(type((1,)))
print(type((1)))
```

```
<class 'tuple'>
<class 'int'>
```

使用`tuple`关键字可以将列表转化为元组。

```python
a = [1, 2, 3]
print(type(a))
a = tuple(a)
print(type(a))
```

```
<class 'list'>
<class 'tuple'>
```

元组除没有增、删、改、排序操作外，其他操作方式与列表相同。

# 第四章 字符串

## 4.1 设置字符串格式

设置字符串格式的方法有很多，这里主要介绍通过调用`format`并传入需要设置的值来设置格式的信息，其中需要被替换的值用花括号包裹起来，如果需要在字符串中显示花括号，需要使用两个相同的花括号。

下面内容主要以`format()`为主，但我们也可以在字符串时前使用`f`标识符，效果一致如下的两个语句效果是一样的

```python
name = "泠曦"
age = "18"
print(f"name:{name:^10},age:{age:^10}")
```

```python
name = "泠曦"
age = "18"
print("name:{name:^10},age:{age:^10}".format(name=name, age=age))
```

输出都是

```
name:    泠曦    ,age:    18  
```

### 4.1.1 替换字段名

第一种方法则为在花括号内指明参数名称，在`format`中给对应参数赋值：

```python
print("{name},{age}".format(name="泠曦", age=18))
```

```
泠曦,18
```

第二种为不设置参数名，只在后面写上参数值，将会按照顺序填充：

```python
print("{},{}".format("你好", "World"))
```

```
你好,World
```

第三种为设置索引，将会在后面括号中按照索引顺序获得对应值：

```python
print("{1},{0}".format("字符串", "格式设置"))
```

```
格式设置,字符串
```

但是需要注意，手动设置索引和不设置索引自动引入不可以同时使用，否则将会出现错误：

```python
print("{1},{}".format("字符串", "格式设置"))
```

```
    print("{1},{}".format("字符串", "格式设置"))
          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
ValueError: cannot switch from manual field specification to automatic field numbering
```

我们还可以使用`.`来访问导入模块的函数、属性、变量：

```python
import math

s = "从{mod.__name__}中获取圆周率：{mod.pi}"
print(s.format(mod=math))
```

```
从math中获取圆周率：3.141592653589793
```

### 4.1.2 基本转换

在指定字段中包含的值后，我们可以在后面添加如何设置其格式的指令：

```python
print("{emoji!s}{emoji!r}{emoji!a}".format(emoji="😀"))
```

```
😀'😀''\U0001f600
```

上面分别将`😀`指定为`str(s)`、`repr(r)`、`ascii(a)`格式进行转换。

除此之外，我们还可以指定将值转换为哪种类型，如小数、二进制码等等。只需要将`!`改为`:`，然后写上对应的类型说明符即可。

如我们将63用十进制、二进制、八进制、十六进制展示出来：

```python
print("十进制:{num:d}\t二进制:{num:b}\t八进制:{num:o}\t十六进制:{num:x}".format(num=63))
```

```
十进制:63	二进制:111111	八进制:77	十六进制:3f
```

字符串设置中的类型说明符见下表

| 类型 | 含义                                                         |
| ---- | ------------------------------------------------------------ |
| `b`  | 将整数表示为二进制数                                         |
| `c`  | 将整数解读为Unicode码点                                      |
| `d`  | 将整数视为十进制数处理，整数默认会使用的说明符               |
| `e`  | 使用科学表示法来表示小数（用e表示指数）                      |
| `E`  | 与`e`相同，但是使用E表示指数                                 |
| `f`  | 将小数表示为定点数                                           |
| `F`  | 与f相同，但对于特殊值（nan和inf），使用大写表示              |
| `g`  | 自动在定点表示法和科学表示法之间做出选择。这是默认用于小数的说明符，但默认情况下至少有一位小数 |
| `G`  | 与`g`相同，但是使用大写来表示指数和特殊值                    |
| `n`  | 与`g`相同，但插入随区域而异的数字分隔符                      |
| `o`  | 将整数表示为八进制数                                         |
| `s`  | 保持字符串的格式不变，这是默认用于字符串的说明符             |
| `x`  | 将整数表示为十六进制并使用小写字母                           |
| `X`  | 与`x`相同，但表示为大写字母                                  |
| `%`  | 将数表示为百分比值（乘以100，按说明符`f`设置格式，最后加上%） |

### 4.1.3 宽度、精度和千位分隔符

#### 宽度

需要设置宽度时，我们可以直接在`:`后加上我们需要的宽度即可：

```python
print("{num:8}".format(num=63))
print("{num:8f}".format(num=63))
```

```
      63
63.000000
```

#### 精度

设置精度时，需要先写上小数点，然后在后面写上需要设置的精度：

```python
print("{num:.2f}".format(num=63))
```

```
63.00
```

#### 千位分隔符

需要使用千位分隔符要使用`,`：

```python
print("{num:,}".format(num=10**10))
```

```
10,000,000,000
```

### 4.1.4 符号、对齐和填充

有些时候我们需要指定输出数据位置对齐，这里有三个符号可以表示对齐方式：`<`左对齐，`>`右对齐，`^`中对其，它的具体实现效果如下：

```python
print("{0:<10.2f}\n{0:^10.2f}\n{0:>10.2f}".format(pi))
```

```
3.14      
   3.14   
      3.14
```

而如果需要设置填充，我们可以在设置宽度和精度的数前面，添加`0`、`+`、`-`或空格，其中`0`表示使用数字0填充，`-`为默认填充方式，`+`会在正数前加上正号：

```python
print("{:010.2f}".format(pi))
print("{: 10.2f}{: 10.2f}".format(pi, -pi))
print("{:+10.2f}{:+10.2f}".format(pi, -pi))
print("{:-10.2f}{:-10.2f}".format(pi, -pi))
```

```
0000003.14
      3.14     -3.14
     +3.14     -3.14
      3.14     -3.14
```

我们还可以使用`=`，它会将填充放置于符号和数字之间：

```python
print("{:=+010.2f}\n{:=+010.2f}".format(pi, -pi))
```

```
+000003.14
-000003.14
```

最后还有一种标识符`#`，将它放在符号说明符和宽度之间，他会触发另一种转换方式，转换细节随类型而异：

```python
print("{:b}".format(63))
print("{:#b}".format(63))
print("{:g}".format(63))
print("{:#g}".format(63))
```

```
111111
0b111111
63
63.0000
```

## 4.2 字符串方法

关于字符串的方法有很多，这里只介绍比较常用的方法（其中方括号中的内容为可选内容）：

| 方法                               | 用处                                                         |
| ---------------------------------- | ------------------------------------------------------------ |
| `center(宽度[,填充])`              | 将字符串居中，并将其左右填充指定字符（类似方法还有`ljust`、`rjust`） |
| `find(需要查找的内容[,起点,终点])` | 在字符串中从起点到终点查找对应内容，找到则返回第一次出现的索引，否则返回`-1` |
| `join(序列)`                       | 与`split`相反，将序列合并为一个字符串（序列中的元素必须是字符串） |
| `lower()`                          | 将字符串中所有字符转换为小写并返回                           |
| `replace(指定子串,字符串)`         | 将指定子串替换为字符串                                       |
| `split([分隔符,分割次数])`         | 将字符串根据分隔符位置分割为一个字符串列表（未指定分隔符则匹配空白字符） |
| `strip([指定字符])`                | 删除字符串开头和结尾的指定字符（默认删除空格）               |
| `translate(转换表)`                | 可以对字符串进行单字匹配替换，并删除指定的字符，但是使用前需要创建转换表，使用`str.maketrans(目标字符,替换字符[,删除字符])`创建 |

以下为各种方法的使用示例：

### 4.2.1 `center(宽度[,填充])`

```python
s = "hello"
print(s.center(30))  # 使用空格填充居中
print(s.center(30, "*"))  # 使用*填充
```

```
            hello             
************hello*************
```

### 4.2.2 `find(需要查找的内容[,起点,终点])`  

```python
s = "hello world"
print(s.find("l"))  # 查找字符串中第一个匹配的位置
print(s.find("l", 3))  # 从第三个字符开始查找字符串中第一个匹配的位置
print(s.find("l", 4, 9))  # 从第三个字符开始，到第五个字符结束，查找字符串中第一个匹配的位置
```

```
2
3
-1
```

### 4.2.3 `join(序列)`  

```python
print("".join(["a", "b", "c"]))
```

```
abc
```

### 4.2.4 `lower()`  

```python
print("ABcdFgHiJk".lower())
```

```
abcdfghijk
```

### 4.2.5 `replace(指定子串,字符串)`  

```python
print("Hello World!".replace("l", "e"))
```

```
Heeeo Wored!
```

### 4.2.6 `split([分隔符,分割次数])`

```python
s = "Hello python, hello world!"
print(s.split())  # 默认以空格为分隔符
print(s.split(","))  # 以逗号为分隔符
print(s.split(" ", 1))  # 以空格为分隔符，只分割一次
```

```
['Hello', 'python,', 'hello', 'world!']
['Hello python', ' hello world!']
['Hello', 'python, hello world!']
```

### 4.2.7 `strip([指定字符])` 

```python
s = "   ***  Hello World   ***   "
print(s.strip())  # 删除字符串头尾的空格
print(s.strip(" *"))  # 删除字符串头尾指定的空格和*
```

```
***  Hello World   ***
Hello World
```

### 4.2.8 `translate(转换表)`

```python
s = "This is translate's test"
table = str.maketrans("is", "**")  # 创建字符映射的转换表，配合translate方法使用
print(s.translate(table))  # 将字符串中的i,s替换为*,*
```

```
Th** ** tran*late'* te*t
```

### 4.2.9 判断字符串是否满足某些特定条件

| 方法          | 解释                                                         |
| ------------- | ------------------------------------------------------------ |
| `isalnum()`   | 检查字符串是否由字母和数字组成，即字符串中的所有字符都是字母或数字。如果字符串至少有一个字符，并且所有字符都是字母或数字，则返回 `True`；否则返回 `False`。 |
| `isalpha()`   | 如果字符串至少有一个字符并且所有字符都是字母或中文字则返回 `True`, 否则返回 `False` |
| `isdigit()`   | 如果字符串只包含数字则返回 `True `否则返回 `False`           |
| `islower()`   | 如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是小写，则返回 `True`，否则返回 `False` |
| `isnumeric()` | 如果字符串中只包含数字字符，则返回 `True`，否则返回 `False`  |
| `isspace()`   | 如果字符串中只包含空白，则返回 `True`，否则返回 `False`.     |
| `istitle()`   | 如果字符串是标题化的(见 title())则返回 True，否则返回 False  |
| `isupper()`   | 如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是大写，则返回 `True`，否则返回 `False` |

# 第五章 集合`set`

## 5.1 集合`set`简介

集合`set`是一种==无序的、不可重复的、可修改==的数据容器。由于集合是无序的，所以不支持索引访问。

```python
s1 = {'A', 'B', 'C'} # 含有三个元素的集合
s2 = set() # 空集合，不能用{}表示，因为{}表示空字典
```

## 5.2 集合常用方法

| 操作             | 含义                                                         | 样例                  |
| ---------------- | ------------------------------------------------------------ | --------------------- |
| `add(...)`       | 添加元素到集合中                                             | `s1.dd('t')`          |
| `remove(...)`    | 移除集合中指定元素（指定元素不存在将报错）                   | `s1.remove('t')`      |
| `pop()`          | 随即删除集合中的元素并返回                                   | `e = s1.pop()`        |
| `clear()`        | 清空集合                                                     | `s1.clear()`          |
| `difference()`   | 求取两个集合的差集（包含在第一个集合中，但不在第二个集合中） | `s1.diffrence(s2)`    |
| `union()`        | 求取两个集合的并集                                           | `s1.union(s2)`        |
| `intersection()` | 求取两个集合的交集                                           | `s1.intersection(s2)` |

### `add()`

```python
s = {12, 200, 33, 21, 4, 64, 8, 466, 6, 6, 6, 458}
s.add(65)
```

```
原：{64, 33, 4, 6, 200, 8, 458, 12, 466, 21}
现：{64, 33, 65, 4, 6, 200, 8, 458, 12, 466, 21}
```

### `remove()`

```python
s.remove(200)
```

```
原：{64, 33, 65, 4, 6, 200, 8, 458, 12, 466, 21}
现：{64, 33, 65, 4, 6, 8, 458, 12, 466, 21}
```

### `pop()`

```python
print(s.pop())
print(s)
```

```
原：{64, 33, 65, 4, 6, 8, 458, 12, 466, 21}

64
{33, 65, 4, 6, 8, 458, 12, 466, 21}
```

### `clear()`

```python
s.clear()
print(s)
```

```
原：{33, 65, 4, 6, 8, 458, 12, 466, 21}

set()
```

### `difference()`

```python
s1 = {11, 12, 13, 14}
s2 = {11, 12, 15, 16}

print(s1.difference(s2)) # 差集也可以使用-，例如：s1 - s2

s3 = {item for item in s1 if item not in s2} # 另一种计算方式
print(s3)
```

```
{13, 14}
{13, 14}
```

### `union()`

```python
s1 = {11, 12, 13, 14}
s2 = {11, 12, 15, 16}

print(s1.union(s2)) # 交集也可以使用|，例如：s1 | s2
```

```
{11, 12, 13, 14, 15, 16}
```

### `intersection()`

```python
s1 = {11, 12, 13, 14}
s2 = {11, 12, 15, 16}

print(s1.intersection(s2)) # 交集也可以使用&，例如：s1 & s2
```

```
{11, 12}
```

# 第六章 字典

## 6.1 字典简介

字典是一种可变容器，它不同于列表，不是通过下表进行访问，而是使用对应的键值（`key`）进行值（`value`）的访问。

字典的结构大致如下，其中，`key`和`value`可以被替换为其他任何值，但是需要注意的是==`key`的值是唯一不可重复的==：

```python
dic = {"key1":"value1", "key2":"value2",..., "key":"value"}
```

在需要访问他的数据时，只需要通过`dic.key即可获得它的值。

## 6.2 创建字典

