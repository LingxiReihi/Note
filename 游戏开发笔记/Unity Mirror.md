# Unity Mirror

## 什么是Mirror？

Mirror是一个免费开源的Unity高级网络库，提供了一系列方便的组件及模板，大大减轻了开发人员在网络编程上花费的时间，可以很轻松的实现不同设备上的游戏联机功能。

## 相关组件及脚本

### Network Manager网络管理器

#### 什么是网络管理器？

网络管理器是一个封装了各种各样网络相关管理代码的脚本文件，它包括但不限于启动或关闭服务、生成角色、玩家状态身份管理等功能，是一个十分强大的脚本文件。

`Network Manager`是一个单例类型脚本组件，因此在同一个场景中只允许出现一次。

#### 通过Transports进行定制化网络连接管理

`transport`为官方预留出来的自定义网络连接接口组件，他可以设置为任何继承于`Transport`类的类型，以便于我们自己来设置连接方式。

Mirror自带网络连接为基于`UDP`的`KCP`连接，除此之外我们还可以自己通过导入API等方式实现其他链接方式，例如通过`Steam`连接等等。

如果是直接添加`Network Manager`脚本到管理器`Game Object`之上，可以在属性栏中的`Network Info->Transport`进行设置，如果是继承该脚本进行自定义逻辑修改可以直接通过更改`transport`的值进行修改：

![image-20241017173548616](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241017173548616.png)

```csharp
transport = 对应Transport脚本组件;
```

#### 自定义连接地址和端口号

在同样一栏中的`Network Address`中可以设置需要进行连接的服务器IP地址，默认为`localhost`即本机IP，同样也可以在脚本中修改`networkAddress`的值直接进行修改，他在官方脚本中定义如下：

```csharp
/// <summary>向客户端开放的服务器地址。</summary>
[FormerlySerializedAs("m_NetworkAddress")]
[Tooltip("客户端应连接到服务器的网络地址。服务器端不会将其用于任何用途。")]
public string networkAddress = "localhost";
```

#### Game State Management游戏状态管理

该部分被定义在`Network Manager`脚本中，需要手动调用不同的方法来实现不同的启动状态。在脚本中，提供了三个方法表示以客户端启动、以专用服务器启动和同时作为服务器和客户端启动，分别为`StartClient`、`StartServer `、`StartHost`，并且官方在书写这些函数时已经将初始化函数作为一部分写入函数中，直接调用就可以创建对应服务。

例如我们可以通过自定义方法来设置通过传入参数来选择启动方式：

```csharp
public void StartSomething(int state)
{
    if (state == 0)
        StartHost();
    else if (state == 1)
        StartServer();
    else if (state == 2)
        StartClient();
}
```

#### Network Manager HUD

这个组件作为测试中快速通过游戏内UI启动服务器的辅助组件，它的本质也是修改`Network Manager`中的`networkAddress`、调用对应的启动函数来实现，额外增加了绘制UI的代码。

`Network Manager HUD`中用于获取`Network Manager`的部分代码：

![image-20241021112542164](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241021112542164.png)

`Network Manager HUD`中用于设置`networkAddress`的代码片段：

![image-20241021112635476](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241021112635476.png)

`Network Manager HUD`中用于启动服务的代码片段：

![image-20241021112733626](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241021112733626.png)

#### 玩家预制体及其生成控制

因为几乎绝大多数可联机游戏都会有一个可供操作的玩家角色，所以官方直接设置了玩家预制体属性用于生成游戏内玩家对象，并且该预制体不能为空，否则将会发生报错。

![image-20241021120610830](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241021120610830.png)

除了玩家预制体的设置外，还可以对其生成位置、是否自动生成进行设置，在`Inspector`窗口中如下图所示：

![image-20241021114346809](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241021114346809.png)

在源码中则分别对应：

```csharp
/// <summary>在服务器上创建玩家对象时使用的默认预制体。</summary>
// 玩家对象在服务器上的 AddPlayer() 默认处理程序中创建。
// 实现 OnServerAddPlayer 方法可以覆盖此行为。
[Header("Player Object")]
[FormerlySerializedAs("m_PlayerPrefab")]
[Tooltip("玩家对象的预制体。预制体必须包含 Network Identity 组件。可以是一个空的游戏对象或一个完整的角色。")]
public GameObject playerPrefab;

/// <summary>启用后，在连接和场景变化时自动创建玩家对象。</summary>
[FormerlySerializedAs("m_AutoCreatePlayer")]
[Tooltip("场景变化后，Mirror 是否应自动生成玩家？")]
public bool autoCreatePlayer = true;

/// <summary>玩家生成的位置。</summary>
[FormerlySerializedAs("m_PlayerSpawnMethod")]
[Tooltip("按轮询顺序或随机顺序选择起始位置")]
public PlayerSpawnMethod playerSpawnMethod;
```

在代码中也可以对他们进行直接的控制，例如通过修改对应具体值等等。

除了使用默认方式自动进行生成外，我们可以手动去生成对应的预制体，在源码中可以找到客户端连接时生成玩家预制体的代码，代码中直接生成了玩家预制体并设置了基础信息，然后便添加到连接管理中，具体添加逻辑则在分部类`Network Server`之中（其中涉及到的`Network Start Position`将在后面同名组件讲解）。我们可以对其进行更改，如更改为连接不显示玩家或不加载玩家预制体，在其他地方进行加载：

```csharp
/// <summary>当客户端请求添加玩家时在服务器上调用。默认添加 playerPrefab。可以被重写。</summary>
// 该函数的默认实现是从 playerPrefab 创建一个新的玩家对象。
public virtual void OnServerAddPlayer(NetworkConnectionToClient conn)
{
    Transform startPos = GetStartPosition();
    GameObject player = startPos != null
        ? Instantiate(playerPrefab, startPos.position, startPos.rotation)
        : Instantiate(playerPrefab);

    // 实例化一个 "Player" 预制体后，默认名称为 "Player(clone)"
    // => 在名称后面附加连接ID对于调试非常有用！
    player.name = $"{playerPrefab.name} [connId={conn.connectionId}]";
    NetworkServer.AddPlayerForConnection(conn, player);
}
```

而在客户端中，生成玩家预制体总的来讲就是调用`AddPlayer`函数来注册并验证是否注册成功，但是需要进行条件是否合适判定。

```csharp
/// <summary>当客户端连接到服务器时调用。默认情况下，它将客户端设置为就绪状态并添加一个玩家。</summary>
public virtual void OnClientConnect()
{
    // OnClientConnect 默认调用 AddPlayer，但在有在线/离线场景的情况下不应这样做。
    // 因此我们需要 clientLoadedScene 标志来防止这种情况。
    if (!clientLoadedScene)
    {
        // 通常，Ready/AddPlayer 是由场景加载完成触发的。
        // 如果没有加载场景，则在这里调用 Ready/AddPlayer。
        if (!NetworkClient.ready)
            NetworkClient.Ready();

        if (autoCreatePlayer)
            NetworkClient.AddPlayer();
    }
}
```

#### Spawn Prefabs其他预制体注册

在多人游戏中，所有需要在游戏中生成的预制体都需要进行注册，官方的原话为：

If you have one Network Manager that is persisted through scenes via Don't Destroy On Load (DDOL), you need to register all prefabs to it which might be spawned in any scene. If you have a separate Network Manager in each scene, you only need to register the prefabs relevant for that scene.

注册的位置在`Inspector`中最末尾：

![image-20241021141033311](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241021141033311.png)

我们也可以手动对他进行注册会在其他位置进行注册，注册的代码为：

```csharp
 NetworkClient.RegisterPrefab(prefab);
```

#### Scene Management场景管理

在`Inspector`窗口中默认会有两个场景参数，第一个为离线场景，第二个为进入游戏后首次加载的场景（可以理解为联机大厅等），在下面还有一个参数，用于设置离线或短线时延迟显示的时间，在这之中可以进行一些特殊处理。

![image-20241021144527183](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241021144527183.png)

在源码中对应部分如下：

```csharp
/// <summary>在离线时（启动/断开连接/关闭）自动切换到此场景。</summary>
[Header("Scene Management")]
[Scene]
[FormerlySerializedAs("m_OfflineScene")]
[Tooltip("当客户端或服务器停止时，Mirror 将切换到的场景")]
public string offlineScene = "";

/// <summary>在上线时（连接后/启动服务器后）自动切换到此场景。</summary>
[Scene]
[FormerlySerializedAs("m_OnlineScene")]
[Tooltip("当服务器启动时，Mirror 将切换到的场景。客户端在连接时会收到一条场景消息以加载服务器当前的场景。")]
public string onlineScene = "";

[Range(0, 60), Tooltip("断开连接后可选的延迟，用于显示 '连接丢失...' 消息或类似内容，然后再加载离线场景，这在大型项目中可能需要较长时间。")]
public float offlineSceneLoadDelay = 0;
```

在需要进行尝尽切换时，可以通过调用`ServerChangeScene(string newSceneName)`函数来进行切换，它会将`onlineScene`自动更新为切换到的场景，也可以重写函数自定义场景切换。

### Network Start Position游戏开始时玩家生成的位置

这个组件组要负责管理玩家生成的点位信息，在组件内部只有两个生命周期函数，分别调用注册和注销该点位的函数，仅仅起到生成点注册和注销的功能：

![image-20241021135225272](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241021135225272.png)

在世家开发中我们也可以对其进行额外功能的添加，例如在注册注销前添加一些处理逻辑等等。

### Network Animator

## Mirror官方快速入门教程学习及相关字段说明

