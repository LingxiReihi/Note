# Neo Forge安装及入门

## Neo Forge套件下载及导入

###  初始准备

`NeoForge`需要使用`Java`语言进行开发，所以需要准备好得到对应版本的`Java`开发环境与开发`IDE`。

### 下载`NeoForge`套件

首先要知道两个网站：

[Getting Started with NeoForge | NeoForged docs](https://docs.neoforged.net/docs/gettingstarted/)

[1.21.xNeoForge开发文档中文翻译 - [Neo]NeoForge - MC百科|最大的Minecraft中文MOD百科](https://www.mcmod.cn/post/4403.html)

其中，第一个是官方文档，第二个是在MC百科上发布的中文翻译网站。

而下载`NeoForge`套件则需要到生成模板去下载：[Mod Generator - The NeoForged project](https://neoforged.net/mod-generator/)

![20251227174412662.png (2560×1380)](https://raw.githubusercontent.com/LingxiReihi/PicGo/refs/heads/master/img/20251227174412662.png?token=GHSAT0AAAAAADSJ25GE3KLOTSFCOYTSRNXU2KYZFCA)

在此页面中直接下载后的导入IDE即可。

导入`IDE`后，`IDEA`等编辑器将会自动开始下载，，而其他编辑器需要使用`README`中的指令手动进行下载。

下载完成后，在`Gradle`中找到上方下载箭头，下载我的世界的源代码：

![20251227174444224.png (2560×1440)](https://raw.githubusercontent.com/LingxiReihi/PicGo/refs/heads/master/img/20251227174444224.png?token=GHSAT0AAAAAADSJ25GECOB2U2TVWOWIOZX42KYZKFA)

## 关键字段等

### 主类

主类名为创建时输入的MOD名同名去下划线文件，MOD编译运行时将会从此类访问所有代码及数据。

#### 关键变量

`MODID`：mod的唯一标识，只能包含小写英文字符和数字及`_`和`.`，否则将会在编译阶段报错。

## `gradle.properties`

#### 羊皮纸`parchment`

这是对官方混淆代码反编译后额外的方法及变量映射，用于辅助开发。

`parchment_minecraft_version`：对应的MC版本。

`parchment_mappings_version`：羊皮纸版本，可以通过上方注释中的链接进行页面访问，查看并修改为对应版本。

![20251227183712135.png (1734×139)](https://raw.githubusercontent.com/LingxiReihi/PicGo/refs/heads/master/img/20251227183712135.png?token=GHSAT0AAAAAADSJ25GEORP6UHBQY34GMYYS2KYZKVA)

![20251227183740967.png (2560×1440)](https://raw.githubusercontent.com/LingxiReihi/PicGo/refs/heads/master/img/20251227183740967.png?token=GHSAT0AAAAAADSJ25GFO5MBU4B5FIEVLMSS2KYZKXQ)

### `Environment Properties`环境配置

`minecraft_version`：我的世界版本号。

`minecraft_version_range`：可以支持的我的世界的版本。

`neo_version`：使用的`Neo Forge`版本。

`loader_version_range`：加载器的范围。

### `Mod Properties`模组配置

`mod_id`：模组的`id`，如果在前主类中修改过这里也要对应修改。

`mod_name`：模组的名字。

`mod_license`：许可证。

`mod_version`：模组版本，建议在后面加上对应的游戏版本，避免模组过多版本记混。

`mod_group_id`：与`Maven`相关，可保持原样不管。

`mod_authors`：模组作者，写上自己的名字。

`mod_description`：对模组的描。

更改完成后可以在游戏内看见自己修改后的内容：

![20251227192531182.png (854×523)](https://raw.githubusercontent.com/LingxiReihi/PicGo/refs/heads/master/img/20251227192531182.png?token=GHSAT0AAAAAADSJ25GFTEQRLZK5TYAF4DQO2KYZLKA)

## 创建第一个物品

### 物品延迟注册器

```java
public static final DeferredRegister.Items ITEMS = DeferredRegister.createItems(Mod主类.MOD_ID);
```

### 注册物品

```java
public static final DeferredItem<Item> ICE_ETHER = 
    ITEMS.register("物品id", () -> new Item(new Item.Properties()));
```

### 注册函数

```java
public static void register(IEventBus eventBus) {
    ITEMS.register(eventBus);
}
```

### 物品名称

物品名称存储于`resources/assets/test_mod/lang`文件夹中。

![20251228200441508.png (475×241)](https://raw.githubusercontent.com/LingxiReihi/PicGo/refs/heads/master/img/20251228200441508.png?token=GHSAT0AAAAAADSJ25GFZGUKO2VXJR3JXI3W2KYZLTA)

添加对应`id`（`/`用`.`代替）并写入的对应语言名称即可：

![20251228201452367.png (1180×455)](https://raw.githubusercontent.com/LingxiReihi/PicGo/refs/heads/master/img/20251228201452367.png?token=GHSAT0AAAAAADSJ25GE6AG4PEGCPRABLVFS2KYZL4A)

![20251228201535036.png (1165×460)](https://raw.githubusercontent.com/LingxiReihi/PicGo/refs/heads/master/img/20251228201535036.png?token=GHSAT0AAAAAADSJ25GE4CPHHQKXRW3CFJXO2KYZL7A)

### 物品详情及贴图

物品详情存放于`resources/assets/test_mod/models`中，贴图文件存放于`resources/assets/test_mod/textures`中，没有这两个文件夹需要手动创建。

![20251228201835393.png (489×687)](https://raw.githubusercontent.com/LingxiReihi/PicGo/refs/heads/master/img/20251228201835393.png?token=GHSAT0AAAAAADSJ25GFWCHVPSOCTH5UZO3C2KYZMQA)

#### 物品详情

```json
{
  "parent": "item/generated",//父级
  "textures": {
    "layer0": "test_mod:item/ice_ether" //贴图路径
  }
}
```

