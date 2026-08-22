# DOTS

## 1.DOTS简介

### 什么是DOTS？

**DOTS**全称为**D**ata-**O**riented **T**echnology **S**tack（面向数据技术栈），是Unity通过多个核心包来定义的一种全新的Unity编写模型，并且在核心包之外包含一系列的游戏功能拓展包及工具包，是unity下面向数据设计与编程的一整套解决方案。

DOTS在Unity中包含三大部分：Entity Component System(ECS)、Job System、Burst Compiler.其中国，Entity只是一个身份标签(identifier)，Component则持有相关的数据（例如速度、生命值等等），System则负责运行相关逻辑。

在运行时，System会分别访问不同的Entity，获取他们之中的Component数据，再通过提供的数据和逻辑对他们进行更新。

![image-20250113171233745](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250113171233745.png)

他的相关包为：

- com.unity.entities（实体组件包）
- com.unity.entities.graphics（实体组件渲染包）
- com.unity.physics（物理）
- com.unity.burst（Burst编译）
- com.unity.collections（HPC#容器，包含Unity常见数据类型）
- com.unity.mathematics（游戏中常用的数学库）

### 谁需要关注DOTS？

- 技术负责人
- 处理游戏逻辑部分的工程师
- 处理网络通信部分的工程师
- 处理动画部分的工程师
- 处理物理模拟部分的工程师
- 开发工具与工作流相关内容的工程师
- 技术美术
- AssetStore中DOTS相关工具与插件的开发人员

### DOTS可以应用到哪些地方？

- 具有大世界流式加载的游戏
- 具有复杂的大规模模拟的游戏
- 具有多种网络类型的多人连线游戏
- 具有需要客户端模拟预测的网络游戏，如射击游戏

### 为什么需要DOTS？

随着硬件设备的不断能发展，游戏中最耗费资源的不再是渲染，而是CPU资源，在CPU多核化后，如何合理的调配资源提高运行效率成为非常重要的一步。DOTS则是面向缓存友好型技术，用DOTS编写的程序可以充分利用现代CPU多核并行的设计，可以极大的提高CPU利用率，在处理大型游戏逻辑上相比于传统方法能够提高将近2000倍运行效率。

### 如何学习DOTS？

- 看：视频、官方文档、官方论坛DOTS区，官方Github中例子的代码
- 查：专业术语、相关概念、拓展材料
- 学：核心包、游戏拓展包、三方拓展与工具
- 改：官方Github中的例子、Unity Assets Store中的例子
- 调：官方Github例子，自己的Demo
- 写：Demo、小工程、DOTS游戏
- 交流：官方论坛，，社交媒体群

## 2.什么是面向数据设计（DOD）

### 面向数据设计是什么？

面向数据的编程是一种编程范式，它将数据作为程序设计的核心，强调以数据为中心进行程序设计和开发。在面向数据的编程中，数据被视为程序的主要组成部分，程序的逻辑和操作都围绕数据展开。

面向数据的编程具有以下特点：

1. 数据驱动：面向数据的编程强调程序的逻辑和操作是基于数据的需求和变化而变化的。程序的设计和实现都是为了处理和操作数据。
2. 数据抽象：面向数据的编程通过定义数据结构和数据类型来抽象和封装数据，使得程序可以更加灵活地操作和处理数据。
3. 数据流动：面向数据的编程强调数据在程序中的流动和传递。程序通过对数据的操作和转换来实现功能。
4. 数据一致性：面向数据的编程注重数据的一致性和完整性。程序设计和实现需要保证数据的正确性和可靠性。

### 面向数据与面向对象的区别？

面向对象程序(Object-oriented Programming,OOP)是便于我们程序书写人员书写的一种编程方式，但他其实并不便于计算机的理解，而面向数据设计则是计算机内存/缓存友好型程序设计方式。

在面向对象编程中，数据往往跟随着每一个对象，这就导致当需要访问大量数据时会出现大量的地址跳转，影响系统访问速率，而面向数据编程将数据与运行逻辑分开，访问时不需要大量的随机跳转，只需要访问连续的内存空间，这会大大的节省CPU访址时间，提高运行效率。

![image-20250109203258744](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250109203258744.png)

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250113174154964.png" alt="image-20250113174154964" style="zoom:50%;" />

## 3.DOTS安装与配置

### (1)相关官方包安装

Check the overview of the available [DOTS packages](https://unity.com/dots/packages).

You should add the following recommended set of core packages to your project:

- [com.unity.entities](https://docs.unity3d.com/Packages/com.unity.entities@latest)
- [com.unity.entities.graphics](https://docs.unity3d.com/Packages/com.unity.entities.graphics@latest)

首先安装DOTS的核心包 `Enntities` ，他几乎包含了 **DOTS** 所需的所有相关核心包（如 `Burst` 、 `Mathematics` 等等）。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250114162955987.png" alt="image-20250114162955987" style="zoom:67%;" />

为了让我们烘培的物体能够在场景中正常显示，我们还需要一个图形渲染包 `Entities Graphics`.

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250114170222992.png" alt="image-20250114170222992" style="zoom: 67%;" />

除此之外，为了让 **DOTS** 支持物理效果，我们还需要一个支持包 `Unity Physics`。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250114170505893.png" alt="image-20250114170505893" style="zoom:67%;" />

### (2)DOTS支持的IDE及推荐的Editor设置

The Entities package uses [Roslyn Source Generators](https://docs.microsoft.com/en-us/dotnet/csharp/roslyn-sdk/source-generators-overview). Because of this, you should use an IDE that's compatible with source generators. Previous IDE versions might experience slow-downs or mark valid code as errors. 

(Entities 包使用 [Roslyn 源生成器](https://docs.microsoft.com/en-us/dotnet/csharp/roslyn-sdk/source-generators-overview)。因此，您应该使用与源生成器兼容的 IDE。以前的 IDE 版本可能会遇到速度变慢或将有效代码标记为错误的情况。)

The following IDEs are compatible with source generators:

- Visual Studio 2022+
- Rider 2021.3.3+

To get the best performance in your Entities project, you should disable Unity's [Domain Reload](https://docs.unity3d.com/Manual/ConfigurableEnterPlayMode.html) setting. To do this, go to **Edit > Project Settings > Editor** menu, and enable the **Enter Play Mode Options** setting, but leave the **Reload Domain** and **Reload Scene** boxes disabled.

(要在 Entities 项目中获得最佳性能，应禁用 Unity 的 [Domain Reload](https://docs.unity3d.com/Manual/ConfigurableEnterPlayMode.html) 设置。为此，请转到 **Edit > Project Settings > Editor** 菜单，并启用 **Enter Play Mode Options** 设置，但禁用 **Reload Domain** 和 **Reload Scene**。)

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250114172817521.png" alt="image-20250114172817521" style="zoom: 67%;" />

## 4.开始使用DOTS

### (1)创建`Sub Scene`

在 **DOTS** 中，需要通过创建一个`Sub Scene`子场景来对实体进行烘培，在子场景以外的物体将会按照原本的方式进行烘培渲染，处于子场景中的物体则会在运行时被转化为**DOTS**实体。

子场景的创建只需要在`Scene窗口`右键，选择`New Sub Scene -> Empty Scene...`即可创建，新建的`Sub Scene`会默认放置于该场景所处文件夹中的同名文件夹中：

![image-20250114233719690](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250114233719690.png)

![image-20250114234240839](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250114234240839.png)

### (2)查看Sub Scene中实体的组件信息

当在`Sub Scene`中创建实体后，`Inspector`窗口中看见的信息和正常创建的物体相同，但是在下方多出了`Enntity Baking Preview`窗口，我们可以在上面看见所有运行时会被烘焙在实体中的 **DOTS** 组件（如果无法查看请先点击一次运行），单击名称还可以看见对应的属性值。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250114234912986.png" alt="image-20250114234912986" style="zoom:80%;" />

也可以通过改变`Inspector`窗口的显示模式来查看实体组件，需要点击右上角圆圈，修改为`Runtime`模式，即可在下面看见所有他将被烘培的DOTS组件。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250114235347565.png" alt="image-20250114235347565" style="zoom: 67%;" />

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250114235547189.png" alt="image-20250114235547189" style="zoom:50%;" />

实体所包含的组件不会与游戏物体的组件一一对应，通常他只会预先烘培实际需要的组件。

### (3)`Sub Scene`的本质

通过点击创建好的`Sub Scene`，可以在`Inspector`窗口中看见，这个子场景实际上是一个特殊的`GameObject`，而DOTS组件的烘培也是将原本的组件中的数据转换为DOTS二进制数据。

![image-20250115000816428](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250115000816428.png)

在子场景右侧有一个复选框，勾选后我们可以对子场景中的实体进行编辑，取消勾选后则无法进行任何操作。

在一个场景中可以包含多个`Sub Scene`，这也就意味着我们可以将地图划分为多个区域，在游戏运行时对不同的区域进行动态加载或卸载，进一步节省系统资源。

而对于一个空物体，DOTS将不会对他进行烘培，因为这没有任何意义，所以如果子场景中有一个空的游戏对象，那么在游戏运行烘培后将无法找到任何他相关的数据，当一个场景中这样的物体太多时，这样做会节省出来大量的时间和效率。

### (4)DOTS对基础组件的支持

在 **DOTS** 中，对于一些 Unity 自带的基础组件，已经实现了很好的适配，他可以在不需要我们进行任何操作的情况下将其转化为 DOTS 二进制数据，并且会与 DOTS 中对应的系统实现完美适配，我们只需要像使用原本 Unity 中的组件一样进行操作即可。

### (5)设置运行时可以在`Scene`窗口看见实时烘培的数据

在默认情况下，我们无法在`Scene`窗口看见游戏运行时的烘培结果，在很多情况下这并不利于我们进行开发测试，为了可以看见实际运行效果，可以在`Editor -> Preferences -> Entities -> Scene View Mode`中将其更改为`Runtime Data`即可。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250115003746692.png" alt="image-20250115003746692" style="zoom:67%;" />

## 5.自定义DOTS组件

### (1)创建组件脚本

在需要创建组建的位置右键，选择`Create->Entities->IComponentData Script`即可创建一个数据组件脚本，也可以通过直接创建普通脚本手动继承对应接口。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250115142342465.png" alt="image-20250115142342465" style="zoom:67%;" />

```csharp
using Unity.Entities;

public struct MoveSpeed : IComponentData
{
    
}
```

==在**DOTS**中组件内任然可以书写函数，但是并不建议书写任何函数在其中，因为这对于 DOTS 和 ECS 是无意义的。==

### (2)烘培自定义组件到实体

在创建好自定义组件后，我们会发现无法直接将该组件添加到实体上，这是因为==DOTS组件必须要通过代码进行烘培==。

#### 创建`MonoBehaviour`脚本

因为 Unity 中只有继承 MonoBehaviour 的脚本才能挂在到 GameObject 上，所以我们需要借助一个继承于 Mono 的脚本来帮助我们进行操作和烘培，这里的脚本需要包含所有自定义 DOTS 组件的变量，命名方式建议为`自定义组件名 + Authoring`。

```csharp
using UnityEngine;

public class MoveSpeedAuthoring : MonoBehaviour
{
    public float value;
}
```

#### 创建烘培类`Baker`

接下来需要创建一个会在烘培过程中被调用的烘培类，它可以是一个内部类，也可以写在该脚本外部，需要实现`Bake`函数。

```csharp
	/// <summary>
    /// 烘培类，将自定义 DOTS 组件烘培到实体上
    /// </summary>
    public class Baker:Baker<MoveSpeedAuthoring>
    {
        public override void Bake(MoveSpeedAuthoring authoring)
        {
            var entity = GetEntity(TransformUsageFlags.Dynamic);
            AddComponent(entity,new MoveSpeed
            {
                value = authoring.value,
            });
        }
    }
```

其中通过`GetEntity`函数获取到实体，传入参数`TransformUsageFlags`为该实体是否需要`transform`组件，总共包含的类型如下：

- `None`: 没有特定的`transform`组件需求。但是其他的[烘培器](https://docs.unity3d.com/Packages/com.unity.entities@1.3/manual/baking-baker-overview.html)可以添加`TransformUsageFlags`值到该实体。
- `Renderable`: 该实体需要`transform`进行渲染，但是不需要在场景中进行任何移动，他将只会在渲染阶段使用`transform`。
- `Dynamic`: 该实体需要`transform`组件实现运行时移动。
- `WorldSpace`: 无论父实体的属性如何，他只能处于世界坐标系中进行变换。
- `NonUniformScale`: 表明实体需要被非均匀缩放。
- `ManualOverride`: 忽略同意游戏对象上的所有`TransformUsageFlags` 值。并且不允许任何烘培器向其添加对应属性。

紧接着需要使用`AddComponent`方法向其添加我们自定义的组件，等待编译完成后我们可以看见实体已经包含了自定义组件，并且它的值与对应的 Mono 脚本值一致。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20250115160112024.png" alt="image-20250115160112024" style="zoom:67%;" />

## 6.DOTS系统

### (1)什么是DOTS中的系统

在关于 DOTS 的简介中就提到，他将实体作为唯一标识，组件用来存放数据，系统用来书写逻辑，也就是说，DOTS 中的系统是用来实现游戏中各种各样的逻辑的，用一种不太恰当的说法，DOTS 中的系统就相当于原本 MonoBehaviour 中的逻辑部分。

### (2)创建System模板

系统模板建立十分简单，直接在需要创建组建的位置右键，选择`Create->Entities->ISystem Script`即可创建，创建完成的模板如下，它包含那三个默认函数，表示游戏运行的不同阶段：

```csharp
using Unity.Burst;
using Unity.Entities;

namespace System
{
    public partial struct UnitMoveSystem : ISystem
    {
        [BurstCompile]
        public void OnCreate(ref SystemState state)
        {
            
        }

        [BurstCompile]
        public void OnUpdate(ref SystemState state)
        {
            
        }

        [BurstCompile]
        public void OnDestroy(ref SystemState state)
        {

        }
    }
}
```

### (3)不同的系统类型

DOTS 官方总共提供了4种系统类型：

- [`SystemBase`](https://docs.unity3d.com/Packages/com.unity.entities@1.3/manual/systems-systembase.html): 提供一个基类用于管理托管类型（引用类型）。
- [`ISystem`](https://docs.unity3d.com/Packages/com.unity.entities@1.3/manual/systems-isystem.html): 提供一个接口用于管理非托管类型（值类型）。
- [`EntityCommandBufferSystem`](https://docs.unity3d.com/Packages/com.unity.entities@1.3/manual/systems-entity-command-buffers.html): 为其他系统提供实体命令缓冲区实例。这允许您将[结构更改(structural changes)](https://docs.unity3d.com/Packages/com.unity.entities@1.3/manual/concepts-structural-changes.html)分组在一起，以提高应用程序的性能。
- [`ComponentSystemGroup`](https://docs.unity3d.com/Packages/com.unity.entities@1.3/api/Unity.Entities.ComponentSystemGroup.html): 为系统提供嵌套组织和更新顺序。

### (4)简单的移动代码

```csharp
foreach (
    var (localTransform, moveSpeed)
    in SystemAPI.Query<RefRW<LocalTransform>, RefRO<MoveSpeed>>())
{
    localTransform.ValueRW.Position =
        localTransform.ValueRO.Position +
        new float3(1, 0, 0) * moveSpeed.ValueRO.value * SystemAPI.Time.DeltaTime;
}
```

通过一个简单的`foreach`对所有实体的`LocalTransform`和`MoveSpeed`进行遍历，因为他们都是结构体类型，所以需要先转化为引用类型。使用`RefRW`转化为可读写引用，`RefRO`为只可读引用，将速度与时间进行操作，最后与 DOTS 中的时间修正相乘让实体能够正常进行移动。

## 7.在MonoBehaviour中访问并操作DOTS实体

```csharp
// 移动对象（DOTS实体）与 MonoBehaviour 的交互
var entityManager = World.DefaultGameObjectInjectionWorld.EntityManager;
var entityQuery = new EntityQueryBuilder(Allocator.Temp).WithAll<UnitMover>().Build(entityManager);

var unitMoverArray = entityQuery.ToComponentDataArray<UnitMover>(Allocator.Temp);
// var entityArray = entityQuery.ToEntityArray(Allocator.Temp);
for (var i = 0; i < unitMoverArray.Length; i++)
{
    var unitMover = unitMoverArray[i];
    unitMover.targetPosition = mouseWorldPosition;
    unitMoverArray[i] = unitMover;
    // entityManager.SetComponentData(entityArray[i], unitMover); // 将数据保存到对应实体
}

entityQuery.CopyFromComponentDataArray(unitMoverArray); // 一次性批量保存数据，减少函数调用，提高性能
```

要从MonoBehaviour中访问DOTS实体，需要使用到[EntityManager](##EntityManager(实体管理器))，每一个[世界（world）](##World(世界))都会有一个**EntityManager**，他提供了用于创建、更新、读取、销毁实体的API。

接下来需要使用[实体查询器(EntityQuery)](##EntityQuery(实体查询器))来对我们需要进行操作的实体进行相关查询，便于后续操作，

# DOTS相关API

## World(世界)

### 概述

在**DOTS**中，World是实体的集合，实体的ID只有在自己所处的World才是唯一的。

一个世界有一个[EntityManager](##EtityManager)结构，用于创建、读取、修改和删除实体。一个世界中包含一组系统，这些系统通常只访问同一世界实体。

## EntityManager(实体管理器)

### 概述

`EntityManager`是一个提供了对实体的创建、读取、修改和删除的一系列方法的API。每一个[世界](##World(世界))中都会有一个`EntityManager`，用于管理该世界的所有实体。

## EntityQuery(实体查询器)

### 概述

实体[管理器(EntityQuery)](##EntityManager(实体管理器))可以对实体管理器中的所有实体进行查询，找到包含有被查询的组件的实体，并根据调用函数的不同返回不同的数据(NativeArray类型)。

### ToComponentDataArray\<T>(AllocatorHandle)

创建一个 NativeArray，其中包含所选实体的 T 类型的组件。

#### 声明

```csharp
public NativeArray<T> ToComponentDataArray<T>(AllocatorManager.AllocatorHandle allocator) where T : unmanaged, IComponentData
```

#### 参数

| 类型                                                         | 名字        | 描述               |
| :----------------------------------------------------------- | :---------- | :----------------- |
| [AllocatorManager](https://docs.unity3d.com/Packages/com.unity.collections@2.5/api/Unity.Collections.AllocatorManager.html).AllocatorHandle | *allocator* | 要分配的内存类型。 |

#### 返回值

| 类型                                                         | 描述                                                      |
| :----------------------------------------------------------- | :-------------------------------------------------------- |
| [NativeArray](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Unity.Collections.NativeArray_1.html)\<T> | 一个数组，其中包含 EntityQuery 选择的所有实体的指定组件。 |

## Allocator

