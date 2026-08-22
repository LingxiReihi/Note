# Unity脚本

## 什么是Unity脚本文件？

Unity脚本文件即我们所书写的实现各种功能的代码文件，通过将脚本挂载到对应`GameObject`来使用。

## Unity使用什么脚本语言？

C#是Unity使用的脚本语言，它属于高级语言。从开发效率角度来说C#高于C++，但运行效率远不及C++。

除此之外，还可以通过插件或拓展让Unity可以使用Python或Lua进行脚本编写。

==Unity开发时仅仅使用了C#语法==，内部原理和`.Net`运行时完全不同。在脚本开发中，Unity会通过编译器将==C#脚本编译为IL指令==，最终获得的所有IL指令会被编译到`Library/ScriptAssemblies/Assembly-CSharp.dll`文件中，每当代码有修改时，这个文件都会自动重新编译。

## 为什么Unity开发时仅仅使用了C#语法？

==Unity是一个标准的C++游戏引擎==，在运行模式下提供了`UnityEngine.dll`库和`UnityEditor.dll`库，我们编写的C#代码脚本会对这些库中的类和方法进行调用，随后再进一步调用Unity底层的C++核心代码。

但目前Unity官方正在致力于将让Unity成为一个纯正的C#开发引擎，将原本的Mono .NET Runtime迁移至.NET (Core) Runtime，快速的向`.Net`进行迭代，以此来提高用户开发速率和提高产品对硬件设备的利用率（[.NET和Unity的未来 - 技术专栏 - Unity官方开发者社区](https://developer.unity.cn/projects/62bbc040edbc2a7848d45ae8)）。

## Unity如何实现跨平台？

早期Unity在开发和打包运行均采用Mono方案（Mono运行时并非Unity开发的，而是一个开源跨平台的C#运行时解决方案，[Unity 与Mono和.Net的关系](https://www.cnblogs.com/u3ddjw/p/10909975.html)），虽然Mono提供了跨平台解决方案，但许多的平台只提供了C++接口，并没有C#接口，这就导致了Unity没办法更好的与目标平台对接。

后来，Unity开发了==IL2CPP，用于在打包前将IL指令转换为C++代码，并在所有代码都转换成C++后统一打包==，这就为提升性能与多平台移植带来了不少便利。==Unity还接入了贝姆垃圾收集器，让C++也可以进行垃圾收集==（贝姆垃圾收集器是一个非精准、不分代的垃圾收集器 ，内部的大致原理是在监听`new`和`delete`关键字的同时记录引用关系，在收集垃圾的时候进行扫描并卸载无用的垃圾内存[Unity使用的GC方式——贝姆GC（BOEHM GC）](https://blog.csdn.net/zhiai315/article/details/136260511)）。

## 如何在Unity中创建一个脚本文件？

在`Project`窗口中的`Assets`目录下，选择合适的文件夹，右键，选择第一个`Create`，在新出现的一栏中选择`C# Script`，此时文件夹内会出现C#脚本图标，为其进行命名即可（注意：==每个脚本的脚本名必须要和他的类名相同，否则将无法执行==），等待引擎编译完成可以双击打开脚本：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914163429729.png" alt="image-20240914163429729" style="zoom: 50%;" />

![image-20240914163633296](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914163633296.png)

## Unity脚本默认模板中都是些什么东西？

Unity代码脚本默认模板结构如下：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914160003314.png" alt="image-20240914160003314" style="zoom:67%;" />

其中最上方的命名空间`UnityEngine`是对Unity引擎基础代码库的引用；每一个脚本都继承于`MonoBehaviour`；脚本中的`Start`和`Update`则是在游戏运行时执行的代表了游戏物体整个生命周期的函数，其中`Start`函数在游戏运行开始时或游戏对象添加进场景中所有组件加载完成时执行，`Update`则是在`Start`执行后游戏运行中逐帧执行，除了这两个函数外，还有`Awake`、`OnEnable`、`FixedUpdate`、`LateUpdate`、`OnDisable`、`OnDestroy`，他们的运行时段如下图：

![img](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/40a2f5b5f2796110706c52712336aa7f.png)

## 什么是帧？

帧是影像动画中最小元素的单位，在Unity中即为游戏画面最小更新单位，通常来讲的24帧游戏、60帧游戏即每秒更新24次画面和每秒更新60次画面的游戏。

在Unity中每一次画面更新都会调用对应帧的函数来保证游戏运行逻辑的正确性。