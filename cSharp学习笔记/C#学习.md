# C#学习

## 基础代码

```c#
using System;

namespace cSharp1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

### 基础代码分析

```c#
using System;//引入System命名空间
//运行程序时需要引入相应的命名空间才可以运行
namespace name//定义一个名字为name的命名空间
{
    class Program//定义一个叫做Program的类
    {
        static void Main(string[]args)//main方法
        {
            Console.WriteLine("abcd");//输出“abcd”并换行（不换行删除Line即可）
        }
    }
}
```

Console是System空间里面的一个类，Write是其中的一个方法。