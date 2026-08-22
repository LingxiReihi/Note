## 5. 面向对象——封装

### 5.1 面向对象编程

#### 什么是面向对象编程？

面向对象是一种对**现实世界理解和抽象**的编程方法，他把**相关数据和方法当作一个整体来看待**，通过程序来形容对象，从更高的层次来进行程序开发，更加贴近事务的自然运行模式。

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

除运算符外，还可以自定义转换运算：[用户定义的显式和隐式转换运算符 - 提供对不同类型的转换 - C# reference | Microsoft Learn](

## 6. 面向对象——继承

### 6.1 继承概念

#### 什么是继承?

继承是面向对象中三大特征之一，它允许类像父子一样存在继承关系，继承类可以继承被继承类中的所有成员及方法，其中被继承的类称为`父类`、`基类`、`超类`，继承类称为`子类`或`派生类`，在`C#`中只允许单类继承。

#### 继承有什么作用?

如同后代继承现代资产和手艺等，使用继承可以提高代码复用，同时在子类中还可以对父类方法进行进一步的拓展或修改。

#### 继承的基本语法是什么？

`C#`中的继承与`C++`、`Java`不同，它不需要使用任何关键字，只需要使用`:`并在后面写上所继承的父类，形式如下：

```c#
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

```c#
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

```c#
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

```c#
public class Cat : Animal
{
    public Cat(string name) : base(name)
    {
        Console.WriteLine("The Cat`s name is " + name);
    }
}
```

在实例化子类时，他的调用如下：

```c#
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

```C#
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

### 6.4 密封类sealed class

#### 什么是密封类？

密封类即在`class`关键字前加上`sealed`关键字的类，它可以让这个类不能被继承（断子绝孙）。

#### 密封类有什么用处？

密封类可以让底层子类不能被继承，保证代码规范性、结构性和安全性，主要用于复杂程序或程序框架之中。

#### 如何声明密封类？

声明密封类只需要在`class`关键字前加上`sealed`关键字即可，例如下面的代码：

```C#
sealed class Cat : Animal{...}
```

## 7. 面向对象——多态

### 7.1 多态

#### 什么是多态？

多态即“多种状态”，它可以让继承于同一父类的子类在执行相同方法时有不同的行为状态（不同的函数执行方式）。

#### 多态有什么用？

多态可以让继承同一父类的每一个对象调用同一方法时有唯一的方法执行逻辑，实现每一个子类均为独立个体，拥有独立行为（用父类接收的子类对象可以调用自己的函数而非父类中的函数）。

#### 如何使用多态进行代码书写？

首先要记住三个关键字vob(`virtual`、`override`、`base`)，其中`virtual`关键字用于定义父类方法，他将该方法声明为虚方法，子类可以进行重写以实现子类的特殊执行，在子类重写父类虚方法时，需要加上`override`关键字，代表这个方法为重写的父类方法，如果需要调用父类中的代码逻辑，在函数中可以用`base`来进行调用。

例如有父类`GameObject`和子类`Player`、`Enemy`：

```C#
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

```C#
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

简单来讲抽象类是一个不能被实例化的类，只允许被其他类继承，而抽象函数则只能写在抽象类中，他不能有任何实现。

#### 为什么需要抽象类和抽象函数？

抽象类和抽象函数可以用于定义一些比较宽泛的概念如人、水果、动物等，他们不是用来描述单一个体，而是用来描述一系列的对象，不能进行具体实例化的类和函数。使用抽象类和抽象函数可以用于定义这些较为抽象的概念而不必去具体的实现他（例如我们无法直接描述动物是怎么进食的，也无法直接描述水果应该如何食用，但他们确实具备这样的功能或方法），这样可以对一系列类进行方法函数的规范，保证继承后的对象表面特征的一致性，具体实现的多样性。

#### 已经有虚函数为什么还需要抽象函数？

虚函数可以有函数体，可以在函数体中写入一些基础的处理逻辑，但虚函数在被子类继承时，可以不对其进行重写，如果写了一个空虚函数，在未进行重写的情况下运行将会出现错误，对于已经写了预处理逻辑的函数，如果子类改变了部分处理方法，运行时也可能会出现错误，并且因为子类中没有重写该函数而出现难以排查的结果。

抽象函数没有函数体，只需要定义方法名及参数，不关心具体实现，子类必须对其进行重写，避开了前面虚函数的未重写错误或难以排查问题所在的问题（实现函数必定会在子类当中）。

#### 如何书写抽象类和函数？

抽象类和函数都由`abstract`关键字修饰，抽象类在`class`前加上关键字，抽象函数则在返回之前添加，但是需要注意抽象函数不能有具体函数体实现：

```C#
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

```C#
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

```C#
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

接口（interface）是多态的一种体现，他可以看成一种特殊的只包含抽象函数和属性的抽象类，但是与抽象类不同，接口是一种行为方式的集合，代编着一种特殊的行为，例如`飞行 `这个行为，它可以是鸟的行为，也可以是飞机的行为，这是可以将飞行作为接口来定义。

#### 接口有什么用？

接口定义了行为，继承并实现该接口的类相当于具有了这样的行为，通过接口可以对这些行为函数进行规范，同时接口又可以当成他们的基类使用，同一种接口可以接收飞机和鸟这两个除了能飞之外完全不同的类对象，实现了按功能区分不同类。

#### 如何让定义接口/定义接口时需要注意什么？

定义接口关键字为`interface`，默认访问修饰符为`public`并且只能为`public`，接口当中的字段可以为`public`或`protected`，默认为`public`，接口中的函数不能进行定义，只能在实现接口的类中进行定义。

例如书写一个飞行接口：

```C#
public interface IFly
{
    public float Speed { get; set; }
    public void Fly();
}
```

#### 如何实现接口？

实现接口与继承抽象类大致相同，但不同的是需要实现接口内的所有字段，并且只能为`public`，实现的函数可以为虚函数，子类继承是可以再次进行重写。

例如实现上面的接口：

```C#
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

```C#
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

```C#
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

```c#
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