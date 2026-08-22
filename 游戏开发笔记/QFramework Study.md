# QFramework

## 简介

------

`QFramework `是一套渐进式、快速开发框架，适用于任何类型的游戏及应用项目。包含一套开发架构和大量的工具集。

使用基础的 `QFramework `只需要导入一个不到cs文件即可，而官方还提供了许多可供下载或自定义的工具集，前往官方网站[QFramework.cn](https://QFramework.cn)可以下载文件或完整工具集

`QFramework`具有简单、易上手、强大的特点，采用MVC架构模式，提供IOC（Inversion Of Control控制反转）、分层支持、CQRS支持，符合SOLID原则，可以使用DDD的方式设计项目，整个框架源代码不到1000行。

### `QFramework`官方提供的工具集（`QFramework.Toolkits`）

------

1. `UIKit `界面 & View快速开发 & 管理解决方案

- `UI`、`GameObject`的代码生成 & 自动赋值
- 界面管理
- 层级管理
- 界面堆栈
- 默认使用`ResKit`方式管理界面资源
- 可自定义界面的加载、卸载方式
- `Manager Of Manager`架构集成（不推荐使用）

2. `ResKit`资源快速开发&管理解决方案

- `AssetBundle`提供模拟模式，开发阶段无需打包即可加载资源
- 资源名称代码生成支持
- 同一个 API 可加载`AssetBundle`、`Resources`、网络和自定义来源的资源
- 提供一套引用计数的资源管理模型

3. `AudioKit`音频管理解决方案

- 提供背景音乐、人声、音效 三种音频播放 API
- 音量控制
- 默认使用`ResKit`方式管理音频资源
- 可自定义音频的加载、卸载方式

4. `CoreKit`提供大量的代码工具

- `ActionKit`：动作序列执行系统
- `CodeGenKit`：代码生成 & 自动序列化赋值工具
- `EventKit`：提供基于类、字符串、枚举以及信号类型的事件工具集
- `FluentAPI`：对大量的 Unity 和 C# 常用的 API 提供了静态扩展的封装（链式 API）
- `IOCKit`：提供依赖注入容器
- `LocaleKit`：本地化&多语言工具集
- `LogKit`：日志工具集
- `PackageKit`：包管理工具，由此可更新框架和对应的插件模块。
- `PoolKit`：对象池工具集，提供对象池的基础上，也提供`ListPool`和`Dictionary Pool`等工具。
- `SingletonKit`：单例工具集
- `TableKit`：提供表格类数据结构的工具集

## `QFramework`架构

------

### `QFramework`中的MVC

------

`QFramework`是基于MVC架构的，即 Model + View + Controller，其中`Model`即数据模型层，负责管理数据，`View`即表现层，用于展示数据修改的结果，`Controller`即控制层，用于控制数据交互及调用View层进行数据展示更新。

在`QFramework`中，`View`指的是游戏物体上挂载的组件，`Controller`指的是挂载在物体上的脚本，`Model`则指的是物体上的对外公开可供外部读或写的数据，而为了方便管理这些不同的模块，引入了`Architecture`，提供一整套架构的解决方案，而模块管理和提供 MVC 只是其功能的一小部分。

例如我们有一个计数器的代码如下：

```csharp
using UnityEngine;
using UnityEngine.UI;

// Controller
public class CounterAppController : MonoBehaviour
{
    // View
    private Button mBtnAdd;
    private Button mBtnSub;
    private Text mCountText;

    // Model
    private int mCount = 0;

    void Start()
    {
        // View 组件获取
        mBtnAdd = transform.Find("BtnAdd").GetComponent<Button>();
        mBtnSub = transform.Find("BtnSub").GetComponent<Button>();
        mCountText = transform.Find("CountText").GetComponent<Text>();


        // 监听输入
        mBtnAdd.onClick.AddListener(() =>
                                    {
                                        // 交互逻辑
                                        mCount++;
                                        // 表现逻辑
                                        UpdateView();        
                                    });

        mBtnSub.onClick.AddListener(() =>
                                    {
                                        // 交互逻辑
                                        mCount--;
                                        // 表现逻辑
                                        UpdateView();
                                    });

        UpdateView();
    }

    void UpdateView()
    {
        mCountText.text = mCount.ToString();
    }
}
```

在上述代码中，下面的部分跟可以看作`Model`，他负责存储更新的数据：

```csharp
// Model
private int mCount = 0;
```

`View`则为场景中的组件：

```csharp
// View
private Button mBtnAdd;
private Button mBtnSub;
private Text mCountText;
```

其余部分则是属于`Controller`部分。

而对于上面的计数器中的数据`mCount`，后续极有可能会将其向其他脚本公开，每次获取都需要单独找到这个脚本再获取数据，如果这个脚本挂载的物体被销毁或出现其他的情况导致无法正常找到时，将会无法访问到这个数据，所以可以将它单独封装为一个`Model`类，`QFramework`提供了抽象类`AbstractModel`用来定义`Model`类，使用时继承该类即可。如下：

```csharp
public class CounterAppModel : AbstractModel
{
    public int Count;

    protected override void OnInit()
    {
        Count = 0;
    }
}
```

`Model`的引入是用来解决数据共享的问题，并不是只要是数据都要放在这里面，对于只在内部使用的变量，依然建议只在内部声明和使用。

接下来我们需要将他在`Architecture`中进行注册：

```csharp
public class CounterApp : Architecture<CounterApp>
{
    protected override void Init()
    {
        // 注册 Model
        this.RegisterModel(new CounterAppModel());
    }
}
```

而移除后的`CounterAppController`则需要继承` IController`以使用组件的功能：

```csharp
public class CounterAppController : MonoBehaviour , IController /* 实现 IController 接口 */
{
    // View
    ...

    // 4. Model
    private CounterAppModel mModel;

    void Start()
    {
        // 5. 获取模型
        mModel = this.GetModel<CounterAppModel>();

        // View 组件获取
        ...


        // 监听输入
        mBtnAdd.onClick.AddListener(() =>
                                    {
                                        // 6. 交互逻辑
                                        mModel.Count++;
                                        // 表现逻辑
                                        UpdateView();        
                                    });

        mBtnSub.onClick.AddListener(() =>
                                    {
                                        // 7. 交互逻辑
                                        mModel.Count--;
                                        // 表现逻辑
                                        UpdateView();
                                    });

        UpdateView();
    }

    void UpdateView()
    {
        mCountText.text = mModel.Count.ToString();
    }

    // 指定架构
    public IArchitecture GetArchitecture()
    {
        return CounterApp.Interface;
    }
}
```

### 引入Command

------

对于上面的`Controller`代码，随着开发的深入，代码肯定会越来越臃肿，一个脚本的代码量也会大大增加，所以可以引入`Command`，用来处理`Controller`中的交互逻辑，想要实现这个功能需要继承`AbstractCommand`，并重写`OnExecute`函数，在内部实现交互逻辑，而对于参数传递需求，需要在内部定义属性并且通过构造函数传递：

```csharp
public class IncreaseCountCommand : AbstractCommand
{
    protected override void OnExecute()
    {
        this.GetModel<CounterAppModel>().Count++;
    }
}
```

```csharp
public class DecreaseCountCommand : AbstractCommand
{
    protected override void OnExecute()
    {
        this.GetModel<CounterAppModel>().Count--;
    }
}
```

此时只需要调用这个命令即可：

```csharp
...
mBtnAdd.onClick.AddListener(() =>
                            {
                                // 交互逻辑
                                this.SendCommand<IncreaseCountCommand>();
                                // 表现逻辑
                                ...   
                            });
...
```

在这里将交互单独写成一个命令可能显得非常麻烦夸张，但当需要进行大量处理时，将交互封装成命令可以大量简化`Controller`内的代码，还可以很方便地对这些函数进行管理。

### 引入事件（Event）

------

在引入了`Command`之后可以简化部分交互逻辑，而在此基础上，我们会发现屏幕UI更新会发生在每一次数值更改后，那么我们可以将其视为一个更新显示的事件，在`QFramework`中一个事件声明只需要定义一个结构体即可，并且该结构体可以不书写变量等内容。如果需要传参可以在内部写上公有变量并且通过构造函数进行赋值即可。

这里的声明其实是声明了一个结构体事件名，实际调用时会根据这个结构体类型去调用对应的事件。

例如声明一个数字发生变化的结构体，代码如下：

```csharp
public struct CountChangeEvent {}
```

之后在相应位置进行注册：

```csharp
this.RegisterEvent<CountChangeEvent>(e =>
{
    UpdateView();
}).UnRegisterWhenGameObjectDestroyed(gameObject);
```

在调用的时候通过`SendEvent`即可：

```csharp
SendEvent<CountChangeEvent>();
```

### 引入Utility层解决更多问题

------

此时，我们可能会需要一个数据存储的功能，例如我们要将它存储到Unity自带的`PlayerPrefs`中，最简单的方法即将它书写到`Model`中，例如下面这样就可以实现数据的读取操作：

```csharp
public class CounterAppModel : AbstractModel
{
    private int mCount;

    public int Count
    {
        get => mCount;
        set
        {
            if (mCount != value)// 当数值与本身数值不等的时候才进行更新，避免频繁无用存储
            {
                mCount = value;
                PlayerPrefs.SetInt(nameof(Count),mCount);
            }
        }
    }

    protected override void OnInit()
    {
        Count = PlayerPrefs.GetInt(nameof(Count), mCount);
    }
}
```

但是如果后面需要大量存储，这个脚本的代码量将大幅度上升，如果后续不使用`PlayerPrefs`而是用其他的，更改起来也会更加复杂，所以`QFramework`提供了`Utility`层来用于这些工具类的脚本定义，例如可以将上面的存储代码转移到一个`Utility`类中：

```csharp
public class Storage : IUtility
{
    public void SaveInt(string key, int value)
    {
        PlayerPrefs.SetInt(key,value);
    }

    public int LoadInt(string key, int defaultValue = 0)
    {
        return PlayerPrefs.GetInt(key, defaultValue);
    }
}
```

在`Architecture`中去注册后，就可以在这个模块中去进行使用：

```csharp
RegisterUtility(new Storage());// 注册
```

```csharp
GetUtility<Storage>().SaveInt(nameof(Count), Count);// 使用
```

### 引入系统（System）

------

#### 目前代码

在开始前先看一下目前已有的代码：

```csharp
using UnityEngine;

public class CounterAppModel : AbstractModel
{
    private int mCount;

    public int Count
    {
        get => mCount;
        set
        {
            if (mCount != value)
            {
                mCount = value;
                PlayerPrefs.SetInt(nameof(Count),mCount);
            }
        }
    }
    protected override void OnInit()
    {
        var storage = this.GetUtility<Storage>();

        Count = storage.LoadInt(nameof(Count));

        // 可以通过 CounterApp.Interface 监听数据变更事件
        CounterApp.Interface.RegisterEvent<CountChangeEvent>(e =>
        {
        	this.GetUtility<Storage>().SaveInt(nameof(Count), Count);
        });
    }
}
```

```csharp
using UnityEngine;

public class Storage : IUtility
{
    public void SaveInt(string key, int value)
    {
        PlayerPrefs.SetInt(key,value);
    }

    public int LoadInt(string key, int defaultValue = 0)
    {
        return PlayerPrefs.GetInt(key, defaultValue);
    }
}
```

```csharp
public class CounterApp : Architecture<CounterApp>
{
    protected override void Init()
    {
        // 注册 Model
        this.RegisterModel(new CounterAppModel());

        // 注册存储工具的对象
        this.RegisterUtility(new Storage());
    }
}
```

```csharp
public struct CountChangeEvent { }
```

```csharp
public class IncreaseCountCommand : AbstractCommand 
{
    protected override void OnExecute()
    {
        this.GetModel<CounterAppModel>().Count++;
        this.SendEvent<CountChangeEvent>();
    }
}
```

```csharp
public class DecreaseCountCommand : AbstractCommand
{
    protected override void OnExecute()
    {
        this.GetModel<CounterAppModel>().Count--;
        this.SendEvent<CountChangeEvent>(); // ++
    }
}
```

```csharp
using UnityEngine;
using UnityEngine.UI;

public class CounterAppController : MonoBehaviour , IController
{
    // View
    private Button mBtnAdd;
    private Button mBtnSub;
    private Text mCountText;

    private CounterAppModel mModel;

    void Start()
    {
        mModel = this.GetModel<CounterAppModel>();

        mBtnAdd = transform.Find("BtnAdd").GetComponent<Button>();
        mBtnSub = transform.Find("BtnSub").GetComponent<Button>();
        mCountText = transform.Find("CountText").GetComponent<Text>();

        // 监听输入
        mBtnAdd.onClick.AddListener(this.SendCommand<IncreaseCountCommand>;

        mBtnSub.onClick.AddListener(this.SendCommand(new DecreaseCountCommand()));

        UpdateView();

        // 表现逻辑
        this.RegisterEvent<CountChangeEvent>(e => 
        { 
        	UpdateView(); 
        }).UnRegisterWhenGameObjectDestroyed(gameObject);
    }

    private void UpdateView() => _countText.text = _counterModel.Count.ToString();

    public IArchitecture GetArchitecture() => CounterApp.Interface;
}
```

#### 引入成就系统

------

这里使用一个成就系统来举例在`QFramework`中如何书写一个系统。

我们假设一个功能，即策划提出了一个成就达成的功能，即 Count 到 10 的时候，触发一个点击达人成就，点击二十次 则触发一个 点击专家成就。逻辑听起来很简单，我们直接在`IncreaseCountCommand`里编写即可：

```csharp
public class IncreaseCountCommand : AbstractCommand 
{
    protected override void OnExecute()
    {
        ...
        if (model.Count == 10)
        {
            //TODO:成就处理逻辑
        }
        else if (model.Count == 20)
        {
            //TODO
        }
    }
}
```

但如果接下来策划又想增加到 -10 的时候的成就，虽然我们还是可以在这里直接添加，但是如果成就越来越多且相关功能越来越复杂，那么每一次更改需求都要先找到对应位置再进行更改，这样明显非常麻烦，所以这里可以引入成就系统来专门对游戏内的成就进行管理。

在QFramework中有着系统的设计，在需要一个系统的时候，只需要继承`AbstractSystem`并在`Architecture`中进行注册：

```csharp
public class AchievementSystem : AbstractSystem, IAchievementSystem
{
    protected override void OnInit()
    {
        this.RegisterEvent<CountChangedEvent>(e =>
        {
            var model = this.GetModel<CounterModel>();
            if (model.Count == 10)
            {
                Debug.Log("Achievement: 10");
            }
            else if (model.Count == 20)
            {
                Debug.Log("Achievement: 20");
            }
            else if (model.Count == -10)
            {
                Debug.Log("Achievement: -10");
            }
        });
    }
}
```

### 数据+数据变更对象`BindableProperty`

`BindableProperty`是一个数据和数据变更事件结合的对象，





# 附录

## IOC（Inversion of Control，控制反转）

------

IOC（Inversion of Control，控制反转）是一种设计思想，目的是将对象的创建和依赖关系管理从类内部转移到外部容器，从而降低类与类之间的耦合度，提高系统的灵活性和可维护性。软甲架构中的IOC通常用于解决类之间的依赖关系问题，使得应用程序能够更容易地进行扩展、测试和维护。

在软甲架构（Layered Architecture）中，IOC的主要作用是让各个层（如表示层、业务逻辑层、数据访问层等）之间的依赖关系不再直接由层内的代码来创建，而是通过外部容器来注入依赖，从而实现“控制反转”。

### IOC的基本思想

------

1. **依赖注入（DI）**：通过外部容器注入依赖对象，而不是让类自己去创建依赖。这些依赖通常是接口或抽象类，外部容器负责提供具体的实现。
2. **反转控制**：IOC将对象的创建和控制权交给外部容器，避免了类之间直接的依赖和创建。这样，一个类不再负责自己的依赖对象的管理和创建，依赖关系变得更加灵活。
3. **松耦合**：IOC使得各个模块或层之间的耦合度大大降低。组件之间通过接口进行交互，具体实现由外部容器注入。这种松耦合的设计使得系统更加模块化，易于维护和扩展。

### IOC在软甲架构中的应用

------

1. **表示层**（UI层）：可以通过IOC容器注入服务或业务逻辑层的依赖，避免在UI层中直接创建业务逻辑层对象。
2. **业务逻辑层**：业务逻辑层可能依赖于数据访问层，IOC容器可以负责将数据访问层的实现注入到业务逻辑层中，而无需业务层自己去创建数据访问层对象。
3. **数据访问层**：在数据访问层中，可能需要连接到数据库或其他外部资源，IOC容器可以注入相应的数据库连接或数据源，而不用手动创建和管理。

### 常见的IOC容器

------

1. `Spring Framework`：Spring是Java领域中广泛使用的IOC框架，它提供了强大的依赖注入机制。Spring通过XML、注解等方式配置依赖，并通过反射机制将依赖注入到目标对象中。
2. `Unity`（非Unity3D）：Unity是一个轻量级的IOC容器，在.NET环境中使用广泛。它提供了类似Spring的依赖注入功能。
3. `Autofac`：Autofac是一个.NET平台上的IOC容器，提供了丰富的配置和扩展功能，支持构造函数注入、属性注入等多种注入方式。

### 依赖注入的常见方式

------

1. **构造函数注入**：通过构造函数注入依赖对象，最为常见，也是最推荐的方式。它可以保证对象在创建时就能完成依赖的注入。
2. **属性注入**：通过属性来注入依赖对象。该方式在某些情况下比较灵活，但可能导致类的状态不一致，较少使用。
3. **方法注入**：通过方法参数注入依赖对象。这种方式用于需要对依赖进行临时配置的场景。

### 优点

------

- **降低耦合**：通过IOC容器进行管理，减少了对象之间的紧密耦合，使得代码更容易进行扩展和替换。
- **提高可测试性**：由于依赖通过注入的方式提供，便于进行单元测试。可以轻松替换依赖，模拟测试场景。
- **增强可维护性**：通过统一的IOC容器管理依赖，整个系统的依赖关系更清晰，维护起来更加方便。

### 缺点

------

- **学习曲线**：IOC容器的使用和配置可能会增加一定的学习曲线，尤其对于不熟悉依赖注入模式的开发者。
- **性能开销**：IOC容器需要通过反射等技术来注入依赖，这可能会带来一定的性能开销，尤其在需要频繁创建对象时。

### 代码示例

------

#### 1. 定义接口和实现

```csharp
// 定义服务接口
public interface IMessageService
{
    void SendMessage(string message);
}

// 实现服务接口
public class EmailMessageService : IMessageService
{
    public void SendMessage(string message)
    {
        Console.WriteLine($"Sending Email: {message}");
    }
}
```

#### 2. 定义一个依赖于`IMessageService`的业务逻辑类

```csharp
// 定义业务逻辑类，依赖于 IMessageService
public class NotificationService
{
    private readonly IMessageService _messageService;

    // 通过构造函数注入 IMessageService 依赖
    public NotificationService(IMessageService messageService)
    {
        _messageService = messageService;
    }

    // 使用 IMessageService 发送通知
    public void Notify(string message)
    {
        _messageService.SendMessage(message);
    }
}
```

#### 3. 配置IOC容器并进行依赖注入

```csharp
using Microsoft.Extensions.DependencyInjection;

class Program
{
    static void Main(string[] args)
    {
        // 设置一个简单的IOC容器
        var serviceProvider = new ServiceCollection()
            .AddSingleton<IMessageService, EmailMessageService>() // 注册 IMessageService 和 EmailMessageService
            .AddTransient<NotificationService>() // 注册 NotificationService
            .BuildServiceProvider();

        // 从容器中获取 NotificationService 实例
        var notificationService = serviceProvider.GetRequiredService<NotificationService>();

        // 使用 NotificationService
        notificationService.Notify("Hello, IOC with Dependency Injection!");
    }
}
```

## **CQRS**（Command Query Responsibility Segregation，命令查询职责分离）

------

**CQRS**（Command Query Responsibility Segregation，命令查询职责分离）是一种软件架构模式，旨在将系统中的“读取操作”和“写入操作”分开，分别使用不同的模型来处理。它的核心思想是**分离负责更新数据的命令部分（Command）和负责读取数据的查询部分（Query）**，以提高系统的可扩展性、性能和可维护性。

### CQRS的核心概念

------

1. **Command（命令）**
   - 表示对系统状态的更改（写操作）。
   - 一个命令负责执行某种操作，例如创建、更新或删除某个实体。
   - 通常由写模型（Write Model）来处理，写模型可能涉及复杂的业务逻辑验证。
2. **Query（查询）**
   - 表示对系统状态的读取（读操作）。
   - 查询是幂等的（不会改变系统状态），例如获取数据列表或详情。
   - 通常由读模型（Read Model）来处理，读模型可能被优化为仅供查询使用。
3. **职责分离**
   - 命令和查询使用不同的数据模型，甚至可以使用不同的数据存储方式。例如，写模型可能使用关系型数据库，而读模型可能使用文档数据库或内存缓存。

### CQRS的典型架构

------

在CQRS架构中，系统可以被分为以下几个部分：

1. **写模型**

- 专注于处理命令（Command）。
- 包含完整的业务逻辑，例如验证、规则检查和授权等。
- 通常将数据存储到规范化的数据库中，以支持复杂的事务操作。

2. **读模型**

- 专注于优化查询操作。
- 不需要复杂的业务逻辑，只负责高效地返回查询结果。
- 数据可能是去规范化的（Denormalized），甚至存储在缓存中，以便加快查询速度。

3. **数据同步**

- 当写模型更新数据时，通过事件（Event）通知读模型同步更新。
- 这种事件驱动机制可以通过消息队列或事件总线实现，确保读模型与写模型的数据一致性。

### CQRS的主要优势

------

1. **性能优化**：读和写分开，可以为每种操作优化底层存储和查询逻辑。例如，读操作可以使用去规范化数据以提高查询性能。
2. **扩展性**：写模型和读模型可以独立扩展。例如，针对高查询量的场景，可以单独扩展读模型。
3. **清晰的职责划分**：命令和查询的分离使代码更易读、易维护，减少模块之间的耦合。
4. **更好的用户体验**：读模型可以提供快速响应，而写操作可以异步处理并最终一致性。
5. **支持复杂业务逻辑**：写模型可以完全聚焦于处理业务规则，而读模型可以专注于满足前端的展示需求。

### CQRS的挑战

------

1. **复杂性增加**：实现读写分离和事件驱动的一致性机制，需要额外的开发和运维成本。
2. **数据一致性问题**：在读写分离的架构中，可能会出现短暂的最终一致性问题，例如用户刚更新数据后，查询时未反映最新数据。
3. **事件溯源的引入**：如果结合事件溯源（Event Sourcing）使用，系统复杂性会进一步增加，需要设计事件存储和回溯机制。

### CQRS的典型使用场景

------

1. **复杂业务逻辑的系统**：系统中有大量写操作涉及复杂的业务规则，而查询操作的要求则侧重于性能和灵活性。
2. **高并发系统**：读操作远多于写操作的场景，例如电商网站、内容管理系统。
3. **需要水平扩展的系统**：读和写的负载可以分开扩展，针对不同的性能瓶颈进行优化。
4. **需要审计和追踪的系统**：结合事件溯源（Event Sourcing），可以完整记录所有写操作的历史，便于审计和回溯。

### 代码示例

------

#### 1. 数据模型（读数据）

```csharp
// Model模型层(数据层)
// 用于处理数据，提供公有数据交互的接口，解决数据共享问题
public interface ICountModel : IModel
{
    public int Count { get; set; }
}
public class CounterModel : AbstractModel, ICountModel
{
    // 设置提供的数据及对应属性
    private int _count = 0;
    public int Count
    {
        get => _count;
        set
        {
            if (_count != value)
            {
                _count = value;
                _storage.SaveInt(nameof(_count), _count);
            }
        }
    }
    
    // 数据操作工具
    private IStorage _storage;

    protected override void OnInit()
    {
        // 数据初始化
        _storage = this.GetUtility<IStorage>();
        _count = _storage.GetInt(nameof(_count), 0);
    }
}
```

#### 2. 命令处理器（写操作）

```csharp
public class IncreaseCountCommand : AbstractCommand
{
    protected override void OnExecute()
    {
        // 对数据进行操作并触发相应事件
        this.GetModel<CounterModel>().Count++;
        this.SendEvent<CountChangedEvent>();
    }
}
```

#### 3. 事件

```csharp
public struct CountChangedEvent
{
    // 可以添加附带数据条目，通过构造函数进行初始化
}
```

#### 4. 控制器

```csharp
// Controller 控制器
public class CounterController : MonoBehaviour, IController
{
    // View 视图层
    private Button _addButton;
    private Button _subButton;
    private Text _countText;

    // Model 模型层(数据层)
    private CounterModel _counterModel;

    private void Start()
    {
        // 获取模型层变量
        _counterModel = this.GetModel<CounterModel>();

        // View 组件获取
        _addButton = transform.Find("AddButton").GetComponent<Button>();
        _subButton = transform.Find("SubButton").GetComponent<Button>();
        _countText = transform.Find("CountText").GetComponent<Text>();


        // 监听输入
        _addButton.onClick.AddListener(() =>
                                       {
                                           // 交互逻辑
                                           this.SendCommand<IncreaseCountCommand>();
                                       });

        _subButton.onClick.AddListener(() =>
                                       {
                                           // 交互逻辑
                                           this.SendCommand<DecreaseCountCommand>();
                                       });

        this.RegisterEvent<CountChangedEvent>(e => { UpdateView(); })
            .UnRegisterWhenGameObjectDestroyed(this.gameObject);
        // 表现逻辑
        UpdateView();
    }

    private void UpdateView()
    {
        _countText.text = _counterModel.Count.ToString();
    }

    public IArchitecture GetArchitecture()
    {
        return CounterApp.Interface;
    }
}
```

#### 5. 存储工具（数据存储）

```csharp
// 用接口设计模块 方便拓展和管理
public interface IStorage : IUtility
{
    /// <summary> 存储整型数据 </summary>
    void SaveInt(string key, int value);

    /// <summary> 获取对应名称整型数据 </summary>
    int GetInt(string key, int defaultValue = 0);
}

public class PlayerPrefsStorage : IStorage
{
    /// <summary>
    /// 保存整型数据
    /// </summary>
    /// <param name="key">key</param>
    /// <param name="value">value</param>
    public void SaveInt(string key, int value)
    {
        PlayerPrefs.SetInt(key, value);
    }

    /// <summary>
    /// 获取对应整型数据
    /// </summary>
    /// <param name="key">key</param>
    /// <param name="defaultValue">默认值，默认为 0 </param>
    /// <returns></returns>
    public int GetInt(string key, int defaultValue = 0)
    {
        return PlayerPrefs.GetInt(key, defaultValue);
    }
}
```

## SOLID原则

------

**SOLID** 是一组设计原则，旨在帮助开发者编写更易于理解、扩展和维护的面向对象代码。SOLID 是五个基本设计原则的首字母缩写，它们分别是：

1. **S** - **Single Responsibility Principle**（单一职责原则）
2. **O** - **Open/Closed Principle**（开放/封闭原则）
3. **L** - **Liskov Substitution Principle**（里氏替换原则）
4. **I** - **Interface Segregation Principle**（接口隔离原则）
5. **D** - **Dependency Inversion Principle**（依赖倒转原则）

### 1. Single Responsibility Principle（单一职责原则，SRP）

------

**定义**：一个类应该只有一个引起它变化的原因，也就是说，类应该只有一个职责（责任）。

- 每个类应该负责做一件事，且这一件事应该完全清晰并且独立。
- 如果一个类有多个职责，修改其中一个职责可能会影响到类的其他职责，增加了系统的复杂性和维护难度。
- 例如，假设有一个`User`类，同时负责用户的业务逻辑处理和日志记录。这里的`User`类就违反了单一职责原则，因为它承担了两个职责：管理用户和记录日志。

**遵循原则的好处**：

- 提高代码的可读性和可维护性。
- 避免类和模块的耦合度过高，减少变动带来的风险。

### 2. Open/Closed Principle（开放/封闭原则，OCP）

------

**定义**：软件实体（类、模块、函数等）应该对扩展开放，对修改封闭。

- 这意味着一个类应当允许在不修改现有代码的情况下进行扩展。换句话说，你应该能够添加新功能，但不应该修改现有代码。
- 通常通过使用继承或接口来扩展现有类的功能，而不直接修改类本身。

**遵循原则的好处**：

- 减少了对现有代码的修改，降低了引入新错误的风险。
- 可以在不影响现有功能的情况下进行功能扩展，提高系统的灵活性和可维护性。

### 3. Liskov Substitution Principle（里氏替换原则，LSP）

------

**定义**：子类对象应该能够替换父类对象，并且程序的行为不应该发生变化。

- 如果一个类是父类，那么它的子类应该能够在不改变原有行为的情况下，替代父类对象并参与工作。
- 换句话说，子类必须能够完全继承父类的行为，不应破坏父类的逻辑和契约。

**遵循原则的好处**：

- 允许使用多态来替代父类对象，确保子类能够以与父类相同的方式参与到系统中。

### 4. Interface Segregation Principle（接口隔离原则，ISP）

------

**定义**：不应强迫客户端依赖它们不需要的接口。

- 这一原则主张接口应该尽可能的小而精，不要包含过多的方法。一个接口不应包含客户端不需要的功能。
- 如果一个类实现了一个庞大的接口，但只用了其中一小部分功能，那么这个类就违反了接口隔离原则。

**遵循原则的好处**：

- 可以避免不必要的依赖，减少类和接口之间的耦合，使系统更加灵活。
- 提高了代码的可维护性和可扩展性。

### 5. Dependency Inversion Principle（依赖倒转原则，DIP）

------

**定义**：高层模块不应依赖低层模块，二者应依赖抽象；抽象不应依赖细节，细节应依赖抽象。

- 高层模块（如业务逻辑）应当依赖于抽象（接口或抽象类），而不是具体的低层模块（如数据库、网络通信等）。
- 低层模块应该实现抽象接口，而不是直接依赖于高层模块的实现。
- 依赖倒转原则的关键在于将依赖关系抽象化，使得高层模块和低层模块的依赖不再直接耦合。

**遵循原则的好处**：

- 使系统更易于扩展和修改。
- 提高了代码的可测试性，因为依赖关系通过接口注入，可以轻松替换不同的实现。

## DDD（Domain-Driven Design，领域驱动设计）

------

**DDD**（Domain-Driven Design，领域驱动设计）是一种软件开发方法论，旨在通过紧密结合业务领域来设计和构建复杂的软件系统。DDD强调以业务为核心，利用领域知识和领域模型来指导系统设计，从而帮助开发团队理解和解决业务问题。

### DDD的核心理念

------

1. **领域（Domain）**：在DDD中，"领域"指的是系统所要解决的问题的业务范围。领域可以是金融、电子商务、医疗健康等任何行业或业务。
2. **领域模型（Domain Model）**：领域模型是对业务领域的抽象，通常以对象、实体、聚合、值对象等形式表示。它表达了业务领域中的核心概念、规则和行为。
3. **领域专家（Domain Expert）**：业务领域的专家，在DDD中，开发团队需要与领域专家紧密合作，理解业务需求，以便构建符合业务需求的系统。

### DDD的关键设计原则

------

1. **统一语言（Ubiquitous Language）**
   - 统一语言是指开发团队和领域专家之间共享的、基于领域模型的语言。这种语言贯穿项目的所有部分（代码、文档、讨论等），确保大家对业务有相同的理解。
   - 例如，在电商系统中，`Order`、`Item`、`Payment`、`Customer`等概念都是统一语言的一部分。
2. **限界上下文（Bounded Context）**
   - 限界上下文是指在一定的上下文或范围内，领域模型的定义是统一的。不同的团队或系统可以在不同的上下文中使用不同的模型和语言，而这些上下文之间的交互是通过明确的接口进行的。
   - 例如，一个订单管理系统和库存管理系统可能有不同的模型和规则，但它们可以通过`Order`或`Stock`等共享接口进行交互。
3. **上下文映射（Context Mapping）**
   - 上下文映射是指明确不同限界上下文之间的关系，帮助团队理解各个上下文如何交互，避免模型的重复和冲突。
   - 上下文映射包括以下几种关系：
     - **共享内核**（Shared Kernel）：两个上下文共享相同的模型。
     - **客户-供应商**（Customer-Supplier）：一个上下文是另一个上下文的客户，客户期望从供应商那里获得某些功能。
     - **防腐层**（Anti-Corruption Layer）：防止外部系统的模型污染当前系统的模型。
4. **领域事件（Domain Events）**
   - 领域事件是描述业务领域中发生的事情，通常表示某个状态变化。它们有助于系统间解耦和异步通信。
   - 例如，`OrderPlaced`、`PaymentReceived`等都是领域事件。

### DDD的实施步骤

------

1. **理解业务领域**：与领域专家紧密合作，深入了解业务需求、规则和流程。这是DDD的基础，正确理解业务是成功实施DDD的关键。
2. **建模**：构建领域模型，将业务概念抽象成实体、值对象、聚合等。
3. **划分限界上下文**：根据业务的不同子域或团队职责，划分系统的上下文范围，定义清晰的接口和边界。
4. **统一语言的使用**：确保开发团队和领域专家使用统一的业务语言，以避免沟通和理解上的差异。
5. **应用领域驱动设计**：通过领域服务、仓储、工厂等模式，将业务逻辑与持久化、界面等外部代码解耦。

### DDD的核心概念

------

#### 1. **实体（Entity）**

- 实体是有唯一标识的对象，可以在系统中持续存在。实体的生命周期和业务规则通常较为复杂，它们的身份（ID）是关键。
- 例如，在一个订单管理系统中，`Order` 可以是一个实体，每个订单都有一个唯一的ID。

```csharp
public class Order
{
    public Guid Id { get; private set; }
    public DateTime CreatedAt { get; private set; }
    public List<OrderItem> Items { get; private set; }

    public Order(Guid id)
    {
        Id = id;
        CreatedAt = DateTime.Now;
        Items = new List<OrderItem>();
    }

    public void AddItem(OrderItem item)
    {
        Items.Add(item);
    }
}
```

#### 2. **值对象（Value Object）**

- 值对象是没有唯一标识的对象，通常用于描述事物的属性或特征。它们是不可变的（immutable），一旦创建，其状态无法更改。
- 例如，`Money`、`Address`等通常是值对象，它们只通过属性来定义其值。

```csharp
public class Money
{
    public decimal Amount { get; private set; }
    public string Currency { get; private set; }

    public Money(decimal amount, string currency)
    {
        Amount = amount;
        Currency = currency;
    }

    public Money Add(Money other)
    {
        if (this.Currency != other.Currency)
        {
            throw new InvalidOperationException("Cannot add different currencies.");
        }
        return new Money(this.Amount + other.Amount, this.Currency);
    }
}
```

#### 3. **聚合（Aggregate）**

- 聚合是由多个实体和值对象组成的一个集合，这些实体和值对象共同协作完成某个功能。聚合的根实体被称为**聚合根**（Aggregate Root），它是聚合内外部交互的唯一入口。
- 聚合的核心目的是确保在一个业务事务内，数据的一致性和完整性。

```csharp
public class OrderAggregate
{
    public Order Order { get; private set; }
    public Money TotalAmount { get; private set; }

    public OrderAggregate(Order order)
    {
        Order = order;
        TotalAmount = new Money(0, "USD");
    }

    public void CalculateTotalAmount()
    {
        TotalAmount = Order.Items.Sum(item => item.TotalPrice);
    }
}
```

#### 4. **领域服务（Domain Service）**

- 领域服务是解决某些复杂业务逻辑的服务，通常涉及到多个实体或值对象。它通常不属于任何单一实体，而是与业务逻辑紧密相关的功能。
- 例如，在一个电商系统中，`PaymentService` 可以是一个领域服务，它涉及订单和支付之间的协作。

```csharp
public class PaymentService
{
    private readonly OrderRepository _orderRepository;
    private readonly PaymentGateway _paymentGateway;

    public PaymentService(OrderRepository orderRepository, PaymentGateway paymentGateway)
    {
        _orderRepository = orderRepository;
        _paymentGateway = paymentGateway;
    }

    public void ProcessPayment(Guid orderId, Money amount)
    {
        var order = _orderRepository.GetOrder(orderId);
        if (order == null)
        {
            throw new InvalidOperationException("Order not found.");
        }

        var paymentSuccessful = _paymentGateway.MakePayment(amount);
        if (paymentSuccessful)
        {
            order.MarkAsPaid();
        }
    }
}
```

#### 5. **仓储（Repository）**

- 仓储模式用于抽象数据存储，提供对聚合根的持久化操作。仓储允许通过聚合根来访问和操作数据，而不暴露底层的数据存储机制。
- 例如，`OrderRepository` 提供对 `Order` 聚合的增删查改（CRUD）操作。

```csharp
public interface IOrderRepository
{
    Order GetById(Guid orderId);
    void Save(Order order);
}
```

#### 6. **工厂（Factory）**

- 工厂模式用于创建复杂的对象，特别是在对象的构建过程较为复杂时。工厂可以帮助你封装对象的创建逻辑，确保聚合和实体的一致性。
- 例如，`OrderFactory` 可以用于创建一个新的 `Order` 实体及其相关的业务逻辑。

```csharp
public class OrderFactory
{
    public Order CreateOrder()
    {
        return new Order(Guid.NewGuid());
    }
}
```