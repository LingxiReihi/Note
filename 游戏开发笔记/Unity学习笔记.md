

# Unity编辑器界面

## Unity基础界面

### 编辑器默认界面布局

打开Unity编辑器，初次启动后看见的界面如下图所示：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240925145638800.png" alt="image-20240912174541569" />

将会发现整个屏幕被分为了不同的标签页（Tabs）进行显示，这里也可以称为视图（View）、窗口（Window）、编辑器（Editor）。

### 打开和关闭编辑界面

对于一些Unity引擎中并没有直接打开的界面，我们可以手动进行打开，例如打开`Animation`窗口，可以通过`最上方菜单栏->Window->Animation->Animation`进行打开，或者可以使用对应的快捷键如该窗口快捷键为`Ctrl 6`：

<video muted>
<source src="https://gitee.com/yimuzhexi/pico-go/raw/master/video/%E6%89%93%E5%BC%80%E6%96%B0%E7%BC%96%E8%BE%91%E7%95%8C%E9%9D%A2.mp4" typr="vedio/mp4">
</video>

关闭窗口的方法也有两种，第一种为右键窗口名，选择`Close Tab`进行关闭，另一种则是直接点击窗口右上角的关闭按钮，对于部分没有关闭按钮的窗口，可以通过点击右上角省略号打开菜单选择`Close Tab`：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240925153304957.png" alt="image-20240925153304957" style="zoom:50%;" />

<video muted>
    <source src = "https://gitee.com/yimuzhexi/pico-go/raw/master/video/关闭界面.mp4">
</video>

### 自定义界面布局

默认的编辑器布局已经将常用的窗口放置在了界面中，但是实际使用中我们可能任然需要一些新的界面和合适的布局，引擎为我们提供了自定义布局并保存布局的功能。

在编辑器窗口中，我们可以通过鼠标左键标签名来对窗口进行拖动，在靠近边缘时窗口还会自动吸附：

<video muted>
    <source src = "https://gitee.com/yimuzhexi/pico-go/raw/master/video/自定义布局-移动标签.mp4 ">
</video>

在已经调整好的布局中，我们可以点击右上角或上方菜单栏中方Window，然后点击`Layouts->Save Layout`，为该布局起一个名称即可将布局保存下来，后续可以通过选择对应布局一键恢复：

<video muted>
    <source src="https://gitee.com/yimuzhexi/pico-go/raw/master/video/%E4%BF%9D%E5%AD%98%E5%B8%83%E5%B1%80.mp4">
</video>

### Unity资源商店Unity Assets Store

在新版本中，资源商店将不再包含在Unity引擎当中，需要通过浏览器打开资源商店购买界面并购买素材，商店的地址为[Unity Asset Store](https://assetstore.unity.com/)。

#### 什么是资源商店？

资源商店是Unity官方提供的游戏素材资源交易平台，我们可以在商店中购买所需要的素材或拓展来帮助我们进行开发，也可以在商店上传资源以获取利润。

#### 资源商店中包含哪些东西？

资源商店中包含有3D模型、纹理、图片音频、引擎拓展插件等等，在这里甚至可以找到已经完成的完整游戏源码，可以在源码基础上进行修改。

资源商店的主界面如下所示：

![image-20240925171831541](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240925171831541.png)

我们可以在上方搜索框搜索我们需要的资源或直接在下方选择资源种类进行筛选，例如我需要3D素材，则点击下面的`3D`，页面将会导向3D素材售卖页面：

![image-20240925172301425](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240925172301425.png)

接下来继续搜素3D素材中的道具，点击`PROPS`即可进入道具页面：

![image-20240925172551056](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240925172551056.png)

在右侧也可以对我们所需要的素材进行详细筛选，例如我需要工业类的素材，在右侧选择工业，将会显示符合需求的所有素材的列表：

![image-20240925172734245](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240925172734245.png)

在下方还可以对素材的价格进行筛选，甚至官方还为我们提供了免费资源的选项，我哭死：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240925173037647.png" alt="image-20240925173037647" style="zoom:50%;" />

#### 如何进行素材导入？

##### Unity官网购买素材或插件导入方法

点击编辑器上方`Window`窗口，点击`Package Manager`打开包管理界面：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240912174541569.png" alt="image-20240912174541569" style="zoom:50%;" />

在Package Manager中点击`Packages`选择`My Assets`，进入个人已购买素材库：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240912175058545.png" alt="image-20240912175058545" style="zoom:50%;" />

在左侧列表选中需要的素材或插件，点击右上角`Download`进行下载：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240912175409980.png" alt="image-20240912175409980" style="zoom:50%;" />

下载完成后，点击`Import`进行素材导入：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240912175509305.png" alt="image-20240912175509305" style="zoom:50%;" />

##### 非官网素材导入

直接将文件拖入编辑器内`Assets`文件夹或其他新建的文件夹即可。

##### 非官网插件导入

打开`Package Manager`界面后，点击左上角`+`，选择对应导入方式即可：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240912175755871.png" alt="image-20240912175755871" style="zoom:50%;" />

## Scene窗口和Hierarchy窗口

`Scene`窗口和`Hierarchy`窗口息息相关，在`Scene`窗口中看见的对象就是在`Hierarchy`窗口中显示的东西。

### `Hierarchy`窗口操作

`Hierarchy`窗口主要负责创建、选择、操作场景中的物体。

#### 鼠标右键操作

鼠标右键点击窗口，可以实现新建模型、对象等功能：

![image-20241024140902297](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024140902297.png)

鼠标右键已有对象，可以进行复制粘贴删除重命名等操作，也可以实现在该对象层级内创建一个新的低一级对象：

![image-20241024141058920](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024141058920.png)

#### 快捷键操作

`F2`：快速重命名。

`Ctrl + C`：复制。

`Ctrl + V`：粘贴。

`Ctrl + D`：克隆一个新对象（直接粘贴+复制）。

`Delete`：删除。

### `Scene`窗口操作

在Scene窗口顶上的工具栏如下图所示：

![image-20241024142553307](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024142553307.png)

#### 渲染模式设置

点开渲染模式设置界面可以看见如下菜单栏：

![image-20241024142943230](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024142943230.png)

其中设置渲染模式的选项为`Shading Mode`，有三个选项`Shaded`（着色器渲染）、`Wireframe`（网格渲染）及`Shaded Wireframe`，他们的效果如下：

（着色器渲染）

![image-20241024143225443](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024143225443.png)

（网格渲染）

![image-20241024143247221](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024143247221.png)

（着色器和网格共同渲染）

![image-20241024143301381](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024143301381.png)

#### 是否启用灯光渲染

在场景中存在灯光，可以通过点击小灯泡选择启用或关闭场景中的灯光显示，图标为蓝色为启用灯光，灰色则为关闭。

（启用灯光）

![image-20241024143637126](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024143637126.png)

（关闭灯光）

![image-20241024143658662](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024143658662.png)

#### 场景辅助线切换

点击图标会出现如下图所示的界面，其中`Grid Plane`为切换辅助线方向，默认为以Y轴为垂线；`Opacity`为设置辅助线透明度。

![image-20241024144049185](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024144049185.png)

（以X轴为垂线的辅助线）

![image-20241024144244160](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024144244160.png)

（以Z轴为垂线的辅助线）

![image-20241024144328242](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024144328242.png)

#### 切换2D视角

在进行2D游戏开发时会使用的视角，场景将会锁定Z轴正方向朝内X轴正方向朝右显示并将辅助线设置为以Z轴为垂线。

（启用了2D视角的效果）

![image-20241024144019616](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024144019616.png)

#### 辅助图标设置

直接点击图标可以启用或禁用场景中的辅助图标。

点击右侧箭头后出现以下窗口，其中`3D Icons`可以设置是否启用3D图标，这种图标可以实现场景放大缩小时图标同步放大缩小，右侧可以设置图标大小；`Selection Outline`用于控制是否显示选中物体轮廓图；`Selection Wire`设置是否显示选中物体的网格；

![image-20241024145522215](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024145522215.png)

#### 坐标系

在Unity中采用左手坐标系，即屏幕正对为z正方向，右侧为x正方向，向上为y正方向，对应图标分别为蓝色、红色、绿色。

![image-20241024150459005](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024150459005.png)

通过点击坐标系对应坐标轴可以快速切换视角。

其中，点击坐标系正中心的正方体，可以切换显示为正交显示（左图），通过点击坐标系下方`Persp`（正交模式为`Iso`）也可以切换。

![image-20241024150654860](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024150654860.png)

点击X、Y、Z可以切换视角正对着的方向为对应负方向。

![image-20241024151058498](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024151058498.png)

#### 相对坐标系

点击可以进行全局坐标系`Global`和局部坐标系`Local`的切换，具体表现为当物体角度进行改变后，移动坐标时所选的参考坐标系。

![image-20241024154352661](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024154352661.png)

### Scene中的`Tool Bar`快捷工具栏

快捷工具栏图标及快捷键如下所示：

![image-20241024151418424](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024151418424.png)

#### 平移`Q`

使用快捷键`W`或选中对应图标，鼠标指针将会变为一个手掌，左键场景并拖动可以让视角中的场景进行平移（但不会更改对应物体的坐标）。

#### 移动`W`

选中图标或使用快捷键`W`，此时再选中某一个物体或左键框选一系列物体，可以对这些物体进行移动（会改变坐标），其中包含三个坐标轴方向移动和三个平面移动，移动式按住`Left Ctrl`可以实现以某一单位长度进行移动：

+ 红色坐标轴：沿X轴移动。
+ 蓝色坐标轴：沿Z轴移动。
+ 绿色坐标轴：沿Y轴移动。
+ 红色平面：可以沿Z轴和Y轴形成的平面移动。
+ 蓝色平面：可以沿X轴和Y轴形成的平面移动。
+ 绿色平面：可以沿Z轴和X轴形成的平面移动。

![image-20241024152040348](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024152040348.png)

#### 旋转`E`

选择第三个图标或按快捷键`E`，可以对选中的一个或多个物体进行旋转，将改变物体的`Rotation`属性，其中可以沿三个方向旋转，分别为X轴（红色）、Y轴（蓝色）、Z轴（绿色）。

![image-20241024152638384](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024152638384.png)

#### 缩放`R`

点击第四个图标或使用快捷键`R`，可以对选中物体进行缩放操作，可以沿着坐标轴缩放和全方向等比例缩放，按住`Left Ctrl`键可以以某一比例进行缩放。

![img](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/36b85da159bd37c8c2fdc2ea660da90b.png)

#### 2D图片或UI缩放及移动`T`

这个功能通常用于2D游戏开发中，通过点击第五个图标或快捷键`T`使用，图片将会显示顶点及锚点位置，可以拖动边界改变它的大小或直接移动位置。

![image-20241024153707842](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024153707842.png)

#### 综合操作`Y`

集所有功能为一身，尽享方便（虽然从来没用过这个功能）。

![image-20241024153931571](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024153931571.png)

### 其他常用快捷键

![image-20241024154825099](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024154825099.png)

## Game窗口

`Game`窗口展示场景中的主摄像机拍摄到的游戏对象，也就是玩家游玩时实际看见的游戏画面。

#### 游戏运行控制

在编辑器最上方有三个图标，他们分别实现了在编辑器中运行游戏、暂停游戏、逐帧运行游戏的功能。

![image-20241024160057075](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024160057075.png)

在`Game`窗口最上方，有以下这些设置选项：

![img](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/eaa4d5195210606df5566f45182aab61.png)

#### 切换运行设备

点击最左侧`Game`可以切换运行设备（例如切换为手机画面）。

![image-20241024160923998](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024160923998.png)

#### 切换相机

点击`Display`旁边的箭头可以切换相机，通过设置相机的`Target Display`来设置对应相机。

![image-20241024161143576](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024161143576.png)

#### 修改画面比例及分辨率

画面比例默认为`Free Aspect`，即自由视角，他的大小将会是窗口的大小，可以自行更改到其他固定大小窗口便于观察游戏场景和UI。

![image-20241024162252014](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241024162252014.png)

## Project窗口

`Project`窗口为工程窗口，显示项目中所有的工程文件，代码、素材、音频等等都在这个窗口中。

![](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028104900792.png)

### 窗口布局设置

点击`Project`窗口右上角三个点，可以打开设置菜单栏，从上往下可以设置为单列显示、双列显示。

![image-20241028105358539](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028105358539.png)

单列显示效果图（左）和双列显示效果图（右），其中双列显示还可以通过右下角来调整显示的图标大小。

![image-20241028110100996](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028110100996.png)

### 创建和打开资源文件

在窗口左上角点击`+`可以在当前选中文件夹中创建资源文件或文件夹，同时，通过`右键文件夹->Create`也可以进行创建。

快速双击资源文件，如果电脑中包含可以处理这种类型文件的应用则会直接打开对应应用，可以快速对资源文件进行处理。

右键文件，选择`Show in Explore`可以在资源管理器中显示文件或文件夹。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028110812692.png" alt="image-20241028110812692" style="zoom:50%;" />

### 资源文件检索

#### 按照文件名搜索

直接在搜索框中输入对应文件名称即可，窗口中将会显示所搜索的文件。

#### 按照文件类型进行检索

通过点击下图所示位置，可以打开类型选择界面，选中对应类型后，`Project`窗口中将会只显示该类型资源文件。此时在旁边搜索框输入名称，可以实现精准搜索。

直接通过在搜索栏中输入`文件名 t:类型`也可以实现对某一类型文件的搜索。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028111542202.png" alt="image-20241028111542202" style="zoom:67%;" />

#### 按照文件标签搜索

点击类型搜索旁边的按钮可以打开标签搜索菜单栏，可以通过自己输入标签或直接选中的方式进行搜索。

也可以在搜索框中输入`文件名 I:标签名`进行搜索。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028112216667.png" alt="image-20241028112216667" style="zoom:50%;" />

### Unity支持的部分文件类型

+ 图片格式:`jpg`、`png`、`tga`

+ 模型格式:`fbx`、`max`、`maya`

+ 音效:`wav`、`mp3`、`0gg`

+ 文本:`txt`、`json`、`bytes`

+ 视频:`mp4`

## `Inspector`窗口

`Inspector`窗口显示所选资源的详细信息，例如代码文件中的代码、图片文件的详细设置信息、游戏物体上的脚本及其设置等等。

![image-20241028115039980](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028115039980.png)

### 窗口锁定

通常情况下，我们选中不同文件时`Inspector`窗口将会更新为选中文件的的信息，而有些时候并不会希望窗口更改（例如对一些参数或属性进行设置的时候），这是可以通过点击右上角锁定图标进行窗口锁定，锁定后的窗口将不会随着我们选择的目标的改变而改变（左侧为锁定后选中Cube，右侧为未锁定选中Cube）。

![image-20241028121307688](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028121307688.png)

### 游戏对象的基础设置

#### 对象图标设置

在编辑场景时，有些时候可能需要快速定位到某些对象在场景中的位置，可以通过设置一个图标来对他进行显示，点击这个按钮会出现详细设置的选项，最上方椭圆形选中后会在场景中显示对象名称并以该种颜色椭圆作为底色，第二栏的小点则是直接在场景中显示出对应颜色的点图标，`Other...`选项则允许我们选择自定义图标。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028122025071.png" alt="image-20241028122025071" style="zoom:50%;" /><img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028122205838.png" alt="image-20241028122205838" style="zoom:67%;" />

不同图标在场景中的样式

![image-20241028122756977](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028122756977.png)

#### 设置是否启用对象

通过勾选这个位置的选择框可以设置对象的启用与禁用，禁用的对象将不会再场景中进行显示，也不会继续的更新对象的状态，但任然可以被代码找到和操作。

（上图：已禁用该对象，但坐标等基础属性任然可以被操作；下图：正常启用对象。）

![image-20241028123854049](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028123854049.png)

#### 对象名设置

在上方文本框中可以修改对象名称，修改后`Hierarchy`窗口中的名称会同步更改，效果等同于直接在`Hierarchy`窗口中修改名称。

#### 静态游戏物体

在窗口右上角可以设置该对象是否为静态对象，通常而言会将一些游戏运行中不会发生过多改变（如坐标变化等）的物体设置为静态物体，它是一种以内存换取时间的行为[静态游戏对象 - Unity 手册](https://docs.unity.cn/cn/2018.4/Manual/StaticObjects.html#:~:text=有关 静态 （即非移动）对象的信息通常可在 Editor 中预先计算，因为此类对象不会因对象位置的变化而无效。 例如，可以通过将多个静态对象组合成称为_批次_的单个大对象来优化渲染。 游戏对象的,Inspector 在右上角有一个 Static 复选框和菜单，用于向 Unity 中的各种不同系统告知该对象不会移动。 对于每个系统，可以单独将对象标记为静态，因此可以选择在不能带来优势的情况下不计算对象的静态优化。)，如果设置为静态的物体任然在不断变化，则不会对性能产生任何优化。

如果通过代码控制需要在物体实例化之前进行设置，否则将不会有任何效果。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028141339499.png" alt="image-20241028141339499" style="zoom:50%;" />

在旁边下拉菜单中还可以设置他的具体静态类型。

#### 设置标签Tag

在下方可以为对象设置一个标签，相当于对物体进行一个分类，可以方便后续查找物体对象和一些物理、射线等等类型的检测。

在下拉菜单中还可以选择`Add Tags...`来手动添加标签，添加完成后再进行设置。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028142208351.png" alt="image-20241028142208351" style="zoom:67%;" />

#### 设置层级Layers

在标签旁边可以设置物体所处层级，层级可以影响到相机的渲染、物理检测等等，在`Project Settings`中的`Physics`可以对不同层级的碰撞关系进行详细的设置。

![image-20241028142321292](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028142321292.png)

### 游戏对象的脚本

#### 查看脚本

选中对象后，在下方可以看见类似于如下图的内容，其中粗体代表脚本名（例如`Transform`、`Plane`等），点开可以看见里面有许多设置参数，这些事脚本中的公有成员变量及序列化后的变量。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028144328668.png" alt="image-20241028144328668" style="zoom:50%;" />

#### 添加和删除脚本

点击最下方的`Add Component`可以打开选择界面，找到或直接输入对应脚本名可以将添加到对应对象上。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028144920954.png" alt="image-20241028144920954" style="zoom:50%;" />

点击需要删除的脚本右上角三个点，可以选中`Remove Component`对其进行删除（`Transform`脚本为每个对象最基本的脚本，无法进行删除），也可以选择`Reset`来重置脚本的所有属性。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028144634107.png" alt="image-20241028144634107" style="zoom:50%;" />

#### 更改脚本排序

除了`Transform`脚本之外，每个脚本都可以通过长按标题并拖动的方式来进行脚本的排序（会出现蓝色宽横线来提示新的位置），也可以通过右上角三个点选择`Move Down`或`Move Up`来更改排序，Unity中获取对象脚本时使用的顺序即为排序顺序。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028145225435.png" alt="image-20241028145225435" style="zoom:50%;" />

#### 启用或禁用脚本

可以通过点击脚本名前方的方框来启用或禁用脚本，被禁用的脚本将不会运行。

#### 打开调试模式

点击`Inspector`窗口右上角的三个点，选中`Debug`即可将`Inspector`窗口设置为调试模式视图。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028145507506.png" alt="image-20241028145507506" style="zoom:50%;" />

调试模式下脚本将会显示所有公有和私有属性（左侧为正常模式，右侧为调试模式），但是私有属性并不能被更改。

![image-20241028145722607](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028145722607.png)

## `Console`控制台窗口

控制台窗口用于显示开发时出现的编译、调试等信息、警告、错误等，在开发过程中是一个十分重要的窗口。

<img src="https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241028152020959.png" alt="image-20241028152020959" style="zoom:67%;" />

在这个窗口中，从左往右分别用于：

+ ①清除所有显示内容；
+ ②下拉选择是否启用在运行时、构建时、编译时清除；
+ ③设置是否折叠相同信息；
+ ④设置是否在发生错误时暂停游戏；
+ ⑤搜索具体信息；
+ ⑥是否显示普通信息（`Debug.Log`）；
+ ⑦是否显示警告信息（`Debug.LogWarning`）；
+ ⑧是否显示报错（`Debug.LogError`）。

# Unity工作原理

## Unity的反射机制及游戏场景

### 场景中的对象的本质是什么？

首先在场景当中，无论是图片、模型还是音效等等，都是基于`GameObject`类对象存在的，而`GameObject`类则是Unity引擎提供给我们的所有对象的基本类型。

将游戏视作一出戏剧，`GameObject`相当于一个没有任何剧本的演员，其他的各种各样的组件则相当于是可执行的各种各样的工作或表演。

### `Transform`是什么？

在舞台上，无论演员是干什么的，她首先都会有一个明确所在的位置，而`Transform`就是来提供这一信息的组件，她告诉了不同的游戏物体应该在什么地方，面朝角度及具体缩放信息。

### 游戏物体如何获取到不同的组件/场景中物体如何进行反射？

在C#中，可以通过反射机制，通过类名获取到这个类的公有属性等信息，同时可以根据获取到的信息新建一个同类型对象并进行操作。

在Unity中，组件添加实质上是首先获取到组件名，再通过组件名去获取到他的公有属性并新建对象，设置对应属性值的时候也是通过反射机制更改对应对象的属性。

### Unity场景文件

Unity场景文件本质是一个记录场景中各种对象信息的文本文件，可以在文件中找到场景中所有的对象及关联的脚本信息，本质上并没有存储类对象等，这也说明Unity加载场景时确实是经过反射来获取到各种类型的具体的信息。

例如在场景中包含一个脚本的物体Cube，在场景文件中可以找到它的名称、所在层级等等信息，顺着往下可以看见他的脚本信息，可以看见只记录了一系列公有属性的值、脚本的基础性息（如名字、ID），只在加载场景时才会通过反射机制来实例化这些信息：

![image-20241119105932634](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241119105932634.png)

![image-20241119110218145](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241119110218145.png)

### 游戏场景的本质

游戏场景的本质就是一个后缀为`.unity`的配置文件，只存储对象相关的公有信息，在运行时才会通过Unity自身的反射机制来进行各个对象的实例化及赋值。

## 预制体Prefab

### 什么是预制体？

预制体是Unity提供的一种可以将游戏对象及其信息进行批量存储及使用的解决方案，它相当于培养了一个有了十分丰富的表演经验的演员，你可以在任何地方去让他进行相同的表演。

### 预制体的本质？

预制体是一个`.prefab`的配置文件，他与场景文件结构几乎相同。

### 如何创建预制体？

创建预制体的方法十分简单，只需要将场景中需要保存的对象长按拖到`Assets`文件夹下方任何位置（一般会专门设置`Prefabs`文件夹进行存储）即可创建并保存对应预制体。

### 如何对预制体进行更改？

如果需要在预制体上添加新的对象，可以直接在场景中进行添加（例如添加一个空物体到Cube），此时他的图标会显示一个与其他预制体中物体不同的图标，表明这是一个新增的物体：

![image-20241119113023278](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241119113023278.png)

此时如果要将他同步到原来的预制体上，可以直接将其拖动到原复制体文件夹，这样可以直接进行覆盖，也可以通过旁边`Inspector`窗口，点击上方`Prefab`一栏的`Overrides->Apply All`进行保存。

![image-20241119113308674](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241119113308674.png)

预制体内的物体删除同理即可。

除开在场景中修改外，通过双击预制体问价打开预制体进行修改，他的修改将会同步到所有应用到的位置。

### 如何取消预制体的打包？

选中场景中的预制体，`右键->Prefab->Unpack`即可取消打包。

### 如何删除预制体？

找到预制体文件直接删除即可，删除后场景中如果有相关联的对象将会红名显示，可以直接取消打包。

## Unity资源包导入与导出

### 什么是资源包？

资源包是一个以`.unitypackge`为后缀名的文件，它包含了一些设置好的Unity脚本、预制件等等，可以快速将这些内容进行批量的打包保存与转移。

### 如何导出资源包？

右键Project窗口，点击`Export Package`可以打开导出界面，在界面中可以选中需要导出的资源文件，点击`Export...`选择对应位置并命名即可导出资源：

![image-20241119115937569](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241119115937569.png)

![image-20241119120117513](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241119120117513.png)

### 如何导入资源包？

导入资源包的方法有两种，第一种是直接将资源包拖入窗口进行导入，第二种则是通过右键选择导入资源包进行导入。

# Unity脚本基础

## 脚本编辑器设置

依次点击上方菜单栏`Edit->Preferences->External Tools->External Script Editor`选择对应脚本编辑器。

![image-20241119121211064](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241119121211064.png)

## 脚本基础规则

### 如何在Unity中创建一个脚本文件？

在`Project`窗口中的`Assets`目录下，选择合适的文件夹，右键，选择第一个`Create`，在新出现的一栏中选择`C# Script`，此时文件夹内会出现C#脚本图标，为其进行命名即可（注意：==每个脚本的脚本名必须要和他的类名相同==），等待引擎编译完成可以双击打开脚本：

![image-20240914163429729](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914163429729.png)

![image-20240914163633296](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914163633296.png)

### 脚本创建规则

1. 尽可能不在脚本编辑器中创建脚本，如果创建需要返回引擎界面一次让Unity引擎将脚本进行编译后方可正常修改脚本内容，否则可能会引起大量警告、报错等。
2. 脚本文件可以放在`Assets`文件夹下任何位置，但建议存放于同一文件夹（如`Scripts`）。
3. 脚本的类名和脚本名必须一致，修改类名或脚本名必须要手动修改另一个（因为Unity基于反射获取脚本信息，脚本文件名与类名不同将无法正确获取到对应类）。
4. 建议不使用中文命名（会降低脚本文件美观性与可读性、不同编码计算机打开可能会出现乱码、在部分情况下中文命名会导致出现文件读取等方面的错误）。
5. 无特殊需求的情况下，不需要单独设置命名空间。
6. 创建的脚本会默认继承于`MonoBehavior`，有需要可以手动删除继承（没有继承该基类将无法挂载到场景对象上）。

### `MonoBehavior`基类是什么？

[重要的类 - MonoBehaviour Unity3D官方文档](https://docs.unity.cn/cn/2021.1/Manual/class-MonoBehaviour.html)

[MonoBehaviour - Unity文档](https://docs.unity3d.org.cn/6000.0/Documentation/ScriptReference/MonoBehaviour.html)

`MonoBehavior`是官方提供的一个脚本框架，提供了游戏运行时的各种事件等，每一个新建的脚本都会显式继承该类型，并且只有继承了该类型的脚本才可以附加到游戏对象中。

![image-20241119123956980](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241119123956980.png)

继承了`MonoBehavior`的类将不能通过`new`关键字进行实例化，只能通过挂载到游戏对象来获取到对应的类对象（因此脚本中的构造函数将不会有任何意义）。

继承已经继承了`MonoBehavior`的类时，同样也可以直接挂载到场景当中。

同一个脚本可以多次挂载，如果需要只能单次挂载的功能，需要在类定义前添加`DisallowMultipleComponent`属性。

![image-20241119134805296](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241119134805296.png)

### 不继承`MonoBehavior`脚本使用方法

不继承`MonoBehavior`的脚本无法挂载到场景中，但是他可以按照正常的类进行使用，通常会将数据类、工具单例类等等设置为不继承。

### 自定义脚本的执行顺序

我们可以通过点击脚本文件后在`Inspector`中点击`Execution Order...`打开自定义脚本运行设置面板：

![image-20241119144548270](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241119144548270.png)

也可以直接在`Edit->Project Settings->Script Execution Order`中进行设置，其中`Default Time`是所有未自定义顺序的脚本执行的时间。

![image-20241119145040405](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241119145040405.png)

### 脚本默认模板

在Unity中新建的脚本都会有一个如下的默认脚本结构，他的默认模板存储于`Editor\Data\Resources\ScriptTemplates`中，如果有需要可以按照需求进行更改。

![image-20240914160003314](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914160003314.png)

## 生命周期函数

### 什么是帧？

游戏运行时实际上就是一个死循环，从进入游戏到结束游戏都在不停地刷新游戏画面，而游戏中每一次画面刷新即为一帧。

fps（Frames Per Second）即为每秒钟帧数。通常所说的60帧、30帧即每秒刷新60次（约为16.66ms刷新一次）和每秒刷新30次（约为33.33ms刷新一次），人眼一般觉得画面不卡顿的刷新率即为每秒24帧。

一般游戏卡顿即为电脑CPU处理能力差或一帧内执行的逻辑太多导致无法正常处理完成所有逻辑运算。

### 脚本的生命周期函数

- Q：什么是生命周期函数？
  A：Unity中每个继承`MonoBehavior`的脚本在游戏的整个逻辑循环中，都会被Unity以反射的形式在不同游戏时期调用不同的生命周期函数（如果有），这些函数可以帮我们确定下来什么时候什么代码会被执行，帮助我们正确的书写脚本。
  生命周期函数一般设置为`private`或`protected`，因为这些函数通常由Unity进行调用，而不是手动在其他脚本中调用。
- Q：生命周期函数支持继承吗？
  A：生命周期函数支持继承和多态。

常见的生命周期函数如下图，其中所直接提到的“对象”为脚本本身的类对象，并非`GameObject`对象。

![img](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/40a2f5b5f2796110706c52712336aa7f.png)

### 设置`FixedUpdate`更新频率

`FixedUpdate`通常用于物理更新，他并不是在每一个游戏帧进行更新，而是会在固定的时间更新，可以通过`Edit->Project Settings->Time->Fixed Timestep`更改他的更新间隔。

![image-20241119161810657](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241119161810657.png)

## `Inspector`可编辑的脚本变量

### 默认会显示的变量

在Unity中，为了方便我们进行一些属性的设置及调试，我们所写的公有基础数据类型会显示在`Inspector`之中，我们可以对他进行设置来更改它的取值。

![image-20241120111949199](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120111949199.png)

### 显示私有变量

在有些情况下，设计代码的时候会设计一些私有变量，但是有希望这些变量可以在`Inspector`窗口被显示或可编辑，便于后续的调试，但Unity默认不显示私有变量，我们需要手动进行设置让他显示出来。

在Unity编辑器中，显示私有变量的方法有两种，一种是打开`Inspector`窗口的`Debug`视图，私有变量将会呈灰色显示，并且无法更改它的值：

![image-20241120112344850](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120112344850.png)

另一种方式则是添加`SerializeField`特性，它可以让私有变量在`Inspector`中直接可见并可以编辑：

![image-20241120112537887](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120112537887.png)

### 显示自定义数据类型

在Unity中，自定义的类、结构体的变量无论是公有还是私有，都是不会被显示出来的，要想被显示出来需要使用特性`System.Serializable`，它会将这个类视为数据类进行处理：

![image-20241120121945226](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120121945226.png)

### 隐藏公有变量

在实际开发中，可能在一些参数上我们已经测试出来了合适的数值，并且不希望后续有人对他进行修改，而且因为代码互相的关联性无法直接设置成私有变量，这是就只能将他在`Inspector`窗口中隐藏起来。

需要隐藏一个变量时，与显示私有变量同理，只需要添加特性`HideInInspector`即可：

![image-20241120114127621](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120114127621.png)

### 限制可以输入的取值范围

在一些时候我们可能编码时会对一些变量进行特殊的处理，这是会要求填写数值时只能限制在某一范围内，而单纯的口头或书面限制可能并不会让人遵守，这时候就需要~~物理~~代码层面限制。

在Unity中同样提供了一个特性来限制可输入范围`[Range(最小值, 最大值)]`，添加了此特性的变量显示时会在输入框前添加一个滑动条，可以滑动进行设置，同时输入的任何一个大于或小于边界值的值都会被强制改为边界值，保证取值在需要的范围内：

![image-20241120115024109](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120115024109.png)

### 其他特性

- **在`Inspector`窗口中显示加粗的标题对内容进行分割**
  如果我们一个脚本中设置的变量非常多的情况下，我们可能会需要有一个标题性质的文本对他进行分割或分类，这时可以杀死用Unity提供的`Header`特性，它可以在窗口中增加一行加粗文本，可以通过文本的位置来判断：
  ![image-20241120115759270](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120115759270.png)

- **在不同变量显示时进行换行**
  为了保持界面美观及与前面的变量进行区分，我们可以通过让变量进行换行显示，只需要用到`Space`特性即可：
  ![image-20241120120054067](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120120054067.png)

- **添加提示语**
  因为在`Inspector`中没办法显示出来变量具体的类型，变量过多时我们可能也对某一些变量的作用会产生混淆，此时使用`Tooltip`来进行标记说明是一个很好的解决方案，他将会让我们将鼠标放在变量名上时显示对应变量的Tooltip：
  ![image-20241120120459491](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120120459491.png)

- **设置多行显示**
  对于一些字符串，可能会存储分行的多行信息，原本的显示框只能显示一行文本，使用`Multiline(行数)`可以实现多行显示，默认会以3行进行显示，但是需要注意的是设置多行显示并不会让文本进行自动换行显示：
  ![image-20241120124045164](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120124045164.png)

- **设置多行显示并且自动换行**
  对于一些特殊的数据，我们在编辑时就会添加换行，或者对于一些数据读取时，我们希望它自动换行来提高可读性，这是可以用到`Area(最小显示行数, 最大显示行数)`这个特性，他会将长文本自动换行，超过最大显示行数会在文本框右侧显示滑动条便于快速找到所需内容：
  ![image-20241120140238917](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120140238917.png)

- **为属性添加方法**

  对于部分属性，我们提供了一个初始值，并且允许进行修改其他值，如果最终其他值不合适，我们想要将初始值添加回来，这是可以给这个属性添加`ContextMenuItem("名称", "方法名")`的特性，它会使我们右键该属性的时候出现额外的我们设定的选项，但是要注意的是，这里提供的方法只能是无参无返的函数，是否为公有函数并没有任何影响：
  ![image-20241120141136536](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120141136536.png)

- **为函数添加特性使其可以在`Inspector`窗口中运行**
  对于某些情况，我们可能需要一些函数在游戏运行前对一些数值进行检测或去重置一些属性值，这是可以给这个函数或方法加上`ContextMenu("显示的方法名")`，此时可以在对应组件右侧三点打开菜单栏，在最下方看见我们添加的显示的方法名，可以通过点击这个按钮来调用方法（重置参数值的方法Unity也提供了函数`Reset`，可以直接重写该函数实现）：
  ![image-20241120142411824](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120142411824.png)

- **多个特性叠加使用**
  在上面提到的特性基本上都能进行叠加使用，例如可以在限制范围时添加提示语等等，只需要将不同的特性用逗号隔开即可。

## `MonoBehavior`提供的基础方法及属性

### 获取当前组件依附游戏对象

因为继承了`MonoBehavior`后的组件需要挂载到游戏对象上才可以运行，所以在开发中不可避免地会经常需要获取到某一脚本所挂载的对象，此时可以通过`gameObject`来进行访问，例如可以直接使用通过其获取挂载的对象的名称：

```csharp
Debug.Log(this.gameObject.name);
```

![image-20241120161011412](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120161011412.png)

### 获取挂载对象的位置相关信息

可以通过`transform`来进行访问对应的`Transform`组件，以此来获取相关信息，例如在控制台中打印当前对象的坐标：

```csharp
Debug.Log(this.transform.position);
```

![image-20241120161303870](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241120161303870.png)

### 获取并设置脚本的激活状态

当需要控制某一脚本是否运行时，可以通过`enabled`来获取当前激活状态或设置脚本的激活状态，设置激活和取消激活会促发相对应的生命周期函数。

### 获取所挂载的组件脚本

当涉及到多脚本交互的时候，需要获取到自身或其他对象身上所挂载的脚本，此时提供了三种获取的方法，分别为通过名称获取、通过类型获取和通过泛型获取，前两个返回的是基类`Component`，需要进行类型转换才可以使用。

当没有该脚本时，将会返回`Null`。

```csharp
test = this.GetComponent("Test") as Test;
test = this.GetComponent(typeof(Test)) as Test;
test = this.GetComponent<Test>();
```

### 获取所挂载的某一类型的所有组件

通过获取单个组件加上复数形式可以获取到所有同类型的组件（无法通过名称获取），常用的有以下两种方式：

```csharp
Test[] tests = this.GetComponents<Test>();
List<Test> testList = new(tests);
this.GetComponents<Test>(testList);
```

### 获取子物体上的组件（同时会查找自身对应组件）

通过下面的两个函数可以获取到子对象上的组件，同时也会获取到自身对应的组件，括号内为可选参数，默认为`false`即不会获取失活对象的组件：

```csharp
GetComponentInChildren<组件名>(bool);
GetComponentsInChildren<组件名>(bool);
```

### 获取父物体上的组件（同时会查找自己）

```csharp
this.GetComponentInParent<组件名>(bool);
this.GetComponentInParents<组件名>(bool);
```

### 尝试获取组件

有些时候并不确定是否含有某一个组件时，可以使用下面的方法获取，它会返回一个bool值来表示是否含有该脚本，参数列表中返回获取到的脚本：

```csharp
bool isHaveComponent = this.TryGetComponent<Test>(out Test test);
```

# Unity基础组件及API

## 最小单位`GameObject`

### `GameObject`的成员变量

#### 名字`name`

每一个游戏对象都会有他的名称，可以通过`Gameobject.name`来进行获取或修改：

```csharp
string name = this.gameObject.name;	// 获取当前对象名称
this.gameObject.name = "12131";		// 设置当前对象名称为 12131
```

#### 自身激活状态`activeSelf`

通过`activeSelf`可以获取到自身的激活状态，但他只是可读不可改的属性：

```csharp
bool isActive = this.gameObject.activeSelf;
```

#### 是否为静态对象`isStatic`

通过该属性可以获取到对象是否为静态对象（静态对象即为游戏中不会发生移动的对象，设置为静态对象可以降低游戏运行时的算力消耗[静态游戏对象 - Unity官方手册](https://docs.unity3d.com/cn/2021.3/Manual/StaticObjects.html#:~:text=%E5%A6%82%E6%9E%9C%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1%E5%9C%A8%E8%BF%90%E8%A1%8C%E6%97%B6%E6%9C%AA%E7%A7%BB%E5%8A%A8%EF%BC%8C%E5%88%99%E8%A2%AB%E7%A7%B0%E4%B8%BA%20%E9%9D%99%E6%80%81%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1%E3%80%82%20%E5%A6%82%E6%9E%9C%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1%E5%9C%A8%E8%BF%90%E8%A1%8C%E6%97%B6%E7%A7%BB%E5%8A%A8%EF%BC%8C%E5%88%99%E8%A2%AB%E7%A7%B0%E4%B8%BA%20%E5%8A%A8%E6%80%81%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1%E3%80%82%20Unity%20%E4%B8%AD%E7%9A%84%E8%AE%B8%E5%A4%9A%E7%B3%BB%E7%BB%9F%E9%83%BD%E5%8F%AF%E4%BB%A5%E5%9C%A8,Editor%20%E4%B8%AD%E9%A2%84%E8%AE%A1%E7%AE%97%E6%9C%89%E5%85%B3%E9%9D%99%E6%80%81%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1%E7%9A%84%E4%BF%A1%E6%81%AF%E3%80%82%20%E7%94%B1%E4%BA%8E%E9%9D%99%E6%80%81%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1%E4%B8%8D%E4%BC%9A%E7%A7%BB%E5%8A%A8%EF%BC%8C%E5%9B%A0%E6%AD%A4%E8%BF%99%E4%BA%9B%E8%AE%A1%E7%AE%97%E7%9A%84%E7%BB%93%E6%9E%9C%E5%9C%A8%E8%BF%90%E8%A1%8C%E6%97%B6%E4%BB%8D%E7%84%B6%E6%9C%89%E6%95%88%E3%80%82%20%E8%BF%99%E6%84%8F%E5%91%B3%E7%9D%80%20Unity%20%E5%8F%AF%E4%BB%A5%E8%8A%82%E7%9C%81%E8%BF%90%E8%A1%8C%E6%97%B6%E8%AE%A1%E7%AE%97%E6%88%90%E6%9C%AC%EF%BC%8C%E5%B9%B6%E5%8F%AF%E8%83%BD%E6%8F%90%E9%AB%98%E6%80%A7%E8%83%BD%E3%80%82)），同时也可以对其进行设置（需要在对象实例化前进行设置，否则运行时将不会有明显的效果）：

```csharp
bool isStatic = this.gameObject.isStatic;	// 获取是否为静态对象
this.gameObject.isStatic = true;			// 设置为静态对象
```

#### 对象所在层级`layer`

游戏中分为不同的层级，不同层级之间可以单独设置物理碰撞等的效果（2D游戏中尤为常用），可以通过`layer`获取或设置对象当前层级（返回值为代表层级的整型数字）：

```csharp
int layer = this.gameObject.layer;	// 获取当前层级
```

#### 对象的标签`tag`

游戏当中会出现对一些列对象的处理，此时想要分辨出不同对象的类型可以使用标签`tag`，可以通过`GameObject`来获取或设置相对应的标签：

```csharp
string tag = this.gameObject.tag;
```

### `GameObject`的静态方法

#### 创建Unity自带模型`CreatePrimitive`

可以直接通过自带方法在场景中直接创建一个自带模型，如果不进行任何配置模型将会出现在坐标(0, 0, 0)。该方法会返回一个`GameObject`类型变量，可以通过该变量对新建立模型进行设置。

方法接收一个参数及模型类型，Unity提供了`Sphere`,`Capsule`, `Cylinder`,`Cube`,`Plane`,`Quad`共六种基础模型。

```csharp
GameObject newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
```

#### 通过名字寻找物体`GameObject.Find`

无法找到失活对象。一般不建议直接通过名称寻找对象，因为这种方法会对场景中所有的对象进行遍历，效率低下。

```csharp
GameObject obj = GameObject.Find("GameObject Name");
```

#### 通过标签寻找对象

通过标签寻找单个对象有两个方法，两者效果相同，都会获取到该类型标签的一个对象：

```csharp
GameObject obj = GameObject.FindWithTag("GameObject Tag");
GameObject obj = GameObject.FindGameObjectWithTag("GameObject Tag");
```

如果有多个对象存在，需要使用`FindGameObjectsWithTag`来进行查找，它将返回所有符合条件的对象：

```csharp
GameObject[] objs = GameObject.FindGameObjectsWithTag("GameObject tag");
```

#### 通过对象上挂载的脚本获取对象

这里获取的对象会默认返回`Object`类，但是该类型是Unity引擎提供并非C#提供的类型，并且该方法不仅会遍历游戏对象，还会遍历对象上挂载的脚本，效率十分低下。

```csharp
Test t = GameObject.FindObjectOfType(typeof(Test)) as Test;
Test t = GameObject.FindObjectOfType<Test>();
```

#### 创建（克隆）游戏物体`Instantiate`

`Instantiate`可以创建游戏场景中已有物体或是预制体，并且他有相当多的重载函数可以对新创建的预制体进行设置：

```csharp
GameObject obj = GameObject.Instantiate(被克隆的物体);
```

#### 移除对象或脚本`Destory`

通过`Destory`可以对对象或脚本进行移除，并且可以设置移除延时，但是他不会在执行到的时候直接移除对象，而是会在下一帧的时候进行移除：

```csharp
GameObject.Destroy(this.gameObject);	// 移除依附的对象
GameObject.Destroy(this);				// 移除该脚本
```

除此之外，还有一种马上移除的方法，但是除非十分需要这种执行，否则不建议使用：

```csharp
GameObject.DestroyImmediate(this);
```

#### 加载场景不删除

```csharp
GameObject.DontDestroyOnLoad(this.gameObject);
```

### `GameObject`成员方法

#### 生成空对象`new`

生成空对象可以直接通过`new`一个`GameObject`来实现，同时可以传递参数为其命名或添加其他组件（组件数目不定，可以随意添加），同时可以直接用新创建的对象来进行操作：

```csharp
GameObject obj1 = new GameObject();
GameObject obj2 = new GameObject("有名字的对象");
GameObject obj3 = new GameObject("有名字有组件的对象", typeof(BoxCollider), typeof(AudioClip));
```

![image-20241121144218460](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241121144218460.png)

#### 动态添加脚本在对象上`AddComponent<type>()`

通过该代码可以为对象添加脚本，并且可以通过返回值得到脚本的信息：

```csharp
BoxCollider collider = this.gameObject.AddComponent<BoxCollider>();
```

#### 比较对象的标签`CompareTag("tag")`

该方法与直接获取标签属性进行比较效果相同，符合返回`true`，否则返回`false`：

```csharp
this.gameObject.CompareTag("tag")
```

#### 设置对象激活与失活`SetActive`

`this.gameObject.SetActive(false);`设置激活状态为失活，同理传入`true`可以设置为激活。

#### 发送消息执行方法`SendMessage`

调用该方法会去查询对象所有脚本中的函数进行匹配，找到传入的名称的函数（例如下方会找到`Func`），无论该函数是否为私有，都会去执行，但是该方法效率较低，建议直接获取对应脚本执行方法：

```csharp
gameObject.SendMessage("Func"[, 参数]);
```

#### 广播让自己和子对象执行方法`BroadcastMessage`

```csharp
gameObject.BroadcastMessage("方法名"[, 参数]);
```

#### 让自己和父对象执行方法`SendMessageUpwards`

```csharp
gameObject.SendMessageUpwards("方法名"[, 参数]);
```

## 时间相关的类Time

### 什么是Time？

`Time`是Unity提供的用于处理位移、计时等等的类，可以通过他计算游戏内一些操作所消耗的时间、设置游戏内整体计算速度（时间流速）等。

### 时间缩放比例`timeScale`

时间缩放比例可以说是设定时间流速比率的属性，当设置为0时时间将停止流动，设置为1则正常流动，2则2倍速流动，默认为1。

通过`Time.timeScale`来获取当前时间比例或对其进行设置。

### 帧间隔时间

帧间隔时间就是最近的一帧用了多长的时间，他的单位为秒。帧间隔时间有两种，一种是受时间比例影响的时间，一种不受时间比例影响。

#### 受到时间缩放比例影响的帧间隔时间`deltaTime`

该时间会受到缩放比例影响，当比例较大时取值会较大，否则相反，通常用于处理物理位移等等的效果，当时间比例为0时，涉及到的效果将不会执行。

#### 不受到时间缩放比例影响的帧间隔时间`unscaledDeltaTime`

该时间不会受到缩放比例影响，只与计算机运行速率相关，通常如果需要一些无视游戏暂停等等规则的移动需要使用该间隔时间。

### 从游戏开始到现在的时间

该时间主要用于计时，一般常用于单机类游戏用来计算运行时长。

#### 受缩放比例影响的时间`time`

#### 不受缩放比例影响的时间`unscaledTime`

### 物理帧时间（FixedUpdate）执行间隔

该时间一般用于处理物理效果，并且时间间隔可以在引擎中进行设置（`Edit->Project Settings -> Time -> Fixed Timestep`），默认为0.02：

![image-20241121172455239](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241121172455239.png)

#### 受时间间隔影响的物理帧`fixedDeltaTime`

#### 不受时间间隔影响的物理帧`fixedUnscaledDeltaTime`

### 游戏运行到现在的总帧数`frameCount`

用于获取从游戏开始运行到现在的已渲染画面帧数（次数）。

## Transform

### 相对于世界坐标系中的坐标`transform.position`

通过这个属性获取到的是物体在世界坐标系中的位置，与本身在`Inspector`窗口中的`position`的数值无关，只与相对于世界坐标系原点的位置有关。

### 相对于父物体的局部坐标`transform.localPosition`

该属性获取的是局部坐标，只与物体相对于父物体的位置有关，与世界坐标系无关（没有父物体则直接等于世界坐标系中的位置），具体值与`Inspector`中的`position`数值相同。

### 改变当前坐标

无论是世界坐标还是局部坐标都可以进行改变，但是无法单独改变某一个坐标值，只能整体改变：

```csharp
this.gameObject.transform.position = new Vector3(0, 0, 0);	// 修改世界坐标为（0，0，0）
```

### 获取当前对象的朝向

可以通过与Vector3获取各方向向量相同的方法来获取对象的朝向，将返回一个单位向量来表示目前面向的方向，例如获取一个物体面朝的方向可以使用`transform.forward`来获取。

### 设置位移

位移计算公式：位移 = 时间 \* 速度 \* 方向

#### 手动进行位移

手动进行移动的方式即为直接更改目前坐标到需要的位置，并且每帧进行刷新，例如每帧让物体向前移动一个单位长度：

```csharp
private void Update()
{
    this.transform.position += Time.deltaTime * 1.0f * this.transform.forward;
}
```

![QQ20241122-123257 00_00_00-00_00_30](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/QQ20241122-123257%2000_00_00-00_00_30.gif)

#### 使用`transform`提供的方法`Translate`移动

`Translate`方法使用语法为`transform.Translate(位移距离 [, 相对坐标系])`，这里的相对坐标系可以不填（默认为自身坐标系），也可以填写`Space`枚举类型来指定世界坐标，也可以直接填入一个`transform`来指定其相同的坐标系。例如，在下面指定另一个物体的坐标系进行移动：

```csharp
public Transform relativeTo;
private void Update()
{
    this.transform.Translate(Time.deltaTime * 1 * Vector3.forward, relativeTo);
}
```

![QQ20241122-172241 00_00_00-00_00_30](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/QQ20241122-172241%2000_00_00-00_00_30.gif)

### 角度与旋转



## Vector3

### 什么是Vector3？

Vector3是Unity提供的用来表示三维坐标或向量的结构体，它内部封装了点和向量的基础算法，如加减乘除点乘等。与之相对应的，对于2D游戏，Unity也提供了Vector2来进行二位坐标向量等的表示。

### 创建Vector3变量

Vector3提供了三种初始化方法，即无参初始化、两个参数初始化和三个参数初始化，其中无参创建后可以使用对应的`x、y、z`初始化，若不进行初始化则默认全为0：

```csharp
Vector3 v = new Vector3();
v.x = 1;
v.y = 2;
v.z = 3;
```

第二种为有参初始化，可以传入全部三个参数进行创建，例如下面的代码块等同于上面的代码块：

```csharp
Vector3 v = new Vector3(1, 2, 3);
```

第三种为传入x、y两个数值，会默认将z设置为0：

```csharp
Vector3 v = new Vector3(1, 2);
```

### Vector3基本运算（+、-、\*、/）

Vector3提供了向量计算的基本方法，可以实现两个向量的加减乘除以及向量与数字的乘除法。

### Vector3提供的基础向量

|       向量        |                描述                 |
| :---------------: | :---------------------------------: |
|  `Vector3.zero`   | 每一个位置均取值为0，即（0，0，0）  |
|   `Vector3.one`   | 每一个位置均取值为1，即（1，1，1）  |
| `Vector3.forward` | Unity中坐标系正前方，即（0，0，1）  |
|  `Vector3.back`   | Unity中坐标系正后方，即（0，0，-1） |
|  `Vector3.left`   | Unity中坐标系正左方，即（-1，0，0） |
|  `Vector3.right`  | Unity中坐标系正右方，即（1，0，0）  |
|   `Vector3.up`    | Unity中坐标系正上方，即（0，1，0）  |
|  `Vector3.down`   | Unity中坐标系正下方，即（0，-1，0） |

### 计算两点之间的距离

Vector3提供了一个静态函数用于获取两点的距离，语法为`Vector3.Distance(pos1, pos2)`:

```csharp
Vector3.Distance(new Vector3(1, 1, 1), new Vector3(0, 0, 0))	//1.732051
```



## 2D图片素材处理

### 为什么需要对图片素材进行修改？

一般而言绘制图片的画师制作图片素材时会按照一般通用的格式去对图片进行设置，例如图片的大小、分割并不一定符合我们的实际需求，所以需要手动过去对图片进行针对性设置。

### 如何对图片进行针对性处理？

使用Unity自带的`Texture Import Settings`可以方便快捷的对图片进行分割、压缩质量等的设置。

### 如何对图片进行设置？

在素材导入后，需要对其进行针对性处理，点击需要处理的2D图片，在`Inspector`中可以看见如下图的内容：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913142336689.png" alt="image-20240913142336689" style="zoom:50%;" />

#### 面板条目介绍

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913142715855.png" alt="image-20240913142715855" style="zoom: 67%;" />

**Texture Type**：设置该图片的类型或用途，选项不同下方其他设置项也会不同。

#### 快速批量设置图片/保存设置预设（Preset）

##### 为什么要保存预设？

图片素材一般不会只有一张，在面对大量素材时，一张一张的去进行设置将会极其耗费时间，虽然可以通过多选图片进行批量设置，但是这样设置后设置天幕并不会被保存，后续有其他图片导入时，仍然需要手动去进行设置。

保存设置的预设不仅可以快速批量进行图片设置，还可以方便后续其他资源导入时对其进行设置。

##### 如何保存并使用预设？

通过保存设置方案，可以快速对同类型图片素材进行设置，步骤如下：

+ 点击右上角配置图标：<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913143823945.png" alt="image-20240913143823945" style="zoom:50%;" />将会打开预设窗口。

+ 如果已有预设，可以直接在窗口内选择对应预设，若没有预设，需要点击下方`Create new Preset...`保存当前预设

  <img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913143908000.png" alt="image-20240913143908000" style="zoom:50%;" />

+ 选择对应文件夹存储预设后，可以在项目文件夹或预设窗口找到对应预设

  <img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913144546575.png" alt="image-20240913144546575" style="zoom:67%;" />

  <img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913144600057.png" alt="image-20240913144600057" style="zoom:50%;" />

+ 预设只是对图片素材的粗略处理，详细处理仍然需要每张图片进行针对性处理。

#### 图片切割（Slice）

##### 为什么要对图片进行切割？

对于一些单位较小的素材，作者一般不会每个素材单独处理而会将其绘制到一张图片中，在这种情况下我们如果不对图片进行切割将会很难使用这些素材，例如一个地面的素材，我们拿到的可能是下图这样：

![image-20240913155423956](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913155423956.png)

而我们使用时则需要单独去使用他的不同部分（如绘制边缘、绘制正常地面），这种时候，像图片中那样按照一定比例对图片进行分割将会更加便于我们使用。

##### 如何分割图片？

点击导入设置窗口中的`Sprite Editor`进入图片编辑界面，在编辑界面点击`Slice`可以对图片进行切割设置并切割图片。

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913152611400.png" alt="image-20240913152611400" style="zoom:50%;" />

其中分割类型`Type`有以下几种：

+ **自动切割Automatic**：将会根据素材像素进行自动切割，将周围是透明的背景的对象切割为单独的素材。

+ **通过单元格大小进行切割Grid By Cell Size**：通过手动设置单元格大小进行切割，Unity将会依次将单元格进行排序，对于不足一个单元格的素材进行舍弃。同时会有额外的设置选项，其中`Offset`为图片切割边界偏移量，`Padding`则为每一个单元格的间隔。

  ![image-20240913161228804](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913161228804.png)

+ **通过单元格数量进行切割Grid By Cell Count**：与按照大小进行切割类似，需要手动进行设置每行每列的单元格数量，将会根据数量平均分割图片素材，他的额外设置项与按大小切割相同。

+ **等距网格lsometric Grid**：将图片按照等距图片素材进行切割，通常用于2.5D游戏。[【Unity】使用 Tilemap 创建等距视角 (Isometric) 的 2D 环境](https://zhuanlan.zhihu.com/p/91186217)

切割的方法有以下三种：

+ **Delete Existing**：删除现有的所有切片，将新切割的切片加入进去。
+ **Smart**：只添加与原来切片重叠的新切片，替换掉旧切片。
+ **Safe**：保留所有旧切片，如果遇到重叠的会删除新切片。

#### 锚点Povit设置

##### 什么是锚点？

锚点是代表图片对齐中心的一个基准点，在Unity中一张图片的坐标往往指的锚点的坐标，锚点位置的不同图片的展示会出现极大不同。

##### 为什么要专门设置锚点？

与前面为什么要专门切割图片类似，锚点默认会在图片的正中心，而我们使用图片时中心点可能并不显得特别重要，更重要的是符合我们处理逻辑的位置，例如对于一棵树我们会将锚点设置在靠近树根的位置。

##### 如何设置锚点？

在切割图片时，可以对切割完成的图片进行批量设置，通过选择`Povit`中对应位置即可，对于自定义锚点`Custom`选项，需要手动书写锚点位置坐标：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913165858046.png" alt="image-20240913165858046" style="zoom:50%;" />

除此之外，还可以单独对某一对象进行设置，只需要选中对象后，手动拖动锚点（空心蓝色小圆）或在右下角进行选择：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913170056985.png" alt="image-20240913170056985" style="zoom:50%;" />

## Sprite渲染器Sprite Render

### 什么是Sprite？

简单通俗的讲，`Sprite`就是我们所使用的图片，他是一个图片对象，里面存储了对应图片的所有信息如图片大小，锚点位置等等，方便我们处理。

### 什么是Sprite Render？

Sprite Render是Unity提供的用于在场景中渲染图片的组件，它拥有许多非常强大的功能，如改变图片渲染层级、更改图片色调等等。

### 为什么使用Sprite Render？

Unity中图片想要进行显示就必须要有渲染器，Sprite Render就是Unity引擎提供的用于显示Sprite图片对象的渲染器组件，如果该组件出现问题或没有该组件，图片将无法正常显示出来。

### 如何使用Sprite Render？

如果将图片直接拖入场景中，场景中生成的对应`Game Object`会自动添加`Sprite Render`并将`Sprite`属性设置为该图片。

对于一个没有该渲染器组件的物体，也可以进行手动添加组件并设置其`Sprite`默认属性值。

除了显示图片，`Sprite Render`还提供了很多其他有用的功能。

#### Color属性

`Sprite Render`提供了`Color`属性，我们可以对其进行更改以改变图片原本的颜色。如下图一个灰白色的头发：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913175727259.png" alt="image-20240913175727259" style="zoom:50%;" />

我们通过点击`Color`属性打开调色盘来修改组件中对应属性，调整他头发的显示为蓝绿色：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913175924625.png" alt="image-20240913175924625" style="zoom:50%;" />

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240913180017939.png" alt="image-20240913180017939" style="zoom:50%;" />

#### Flip属性

Flip属性设置效果为对图片进行翻转，其中有两个可勾选的选项，`X`为水平翻转，`Y`为竖直翻转（竖直翻转通常以图片下边界为准进行翻转）：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914142931102.png" alt="image-20240914142931102" style="zoom: 50%;" />

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914143115974.png" alt="image-20240914143115974" style="zoom: 50%;" />

#### Mask Interaction遮罩交互属性

该属性有三个选项，默认为`None`，即不进行任何交互。

`Visible Inside Mask`设置：使该图片在遮罩内可见，如下图一个较小方形遮罩和一个设置了该属性的红色圆形重叠在一起的显示效果：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914150022211.png" alt="image-20240914150022211" style="zoom:50%;" />

`Visible Outside Mask`设置：是图片在遮罩外部显示，内部不进行显示，如将上面的圆形属性进行修改后，效果如下：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914150152376.png" alt="image-20240914150152376" style="zoom:50%;" />

#### Sprite Sort Point排序点

用于设置图片在场景当中渲染排序的基准点，默认为`center`，即图片中心，另一选项为`povit`，即按照我们手动设置的锚点进行排序。

#### Material材质

设置该对象的渲染纹理，默认为` Sprites - Default`。

#### Sorting Layer渲染层级

用于设置渲染时所处层级，不同层级之间有渲染时的遮盖效果，默认为`Default`，可以在下拉菜单中选择`Add Sorting Layer...`创建新的渲染层并可以对现有层级进行排序，调整遮盖顺序。

#### Order in Layer层级序号

设置同一层级中的遮盖效果，默认为0，范围为`short`的范围，数字越大则显示在越前面，数字越小则会被更多的对象遮盖。

如将红色的圆层级中序号设置为0，白色圆设置为1，那么白色圆将会永远在红色圆前面显示。

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914151957378.png" alt="image-20240914151957378" style="zoom:25%;" />

### Sorting Group排序组

#### 什么是排序组？

排序组是用于设置子物体的渲染层级分组，使得他们成为一个整体进行渲染而不会被其他同层级物体进行切割渲染。

#### 为什么要使用排序组？

使用排序组可以让物体作为一个整体进行渲染排序，而不会对单个子物体进行分开渲染，避免出现渲染显示错误。

如我们有两个均为圆形和方形组成的物体，圆形的渲染层级为`Default 1`，方形为`Default 0`：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914153449996.png" alt="image-20240914153449996" style="zoom: 33%;" />

当我们将两个物体重叠时，发现圆形始终显示在方形之前，两个物体被进行了拆分：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914153557905.png" alt="image-20240914153557905" style="zoom:33%;" />

而当我们为他设置分组后，由圆和方形组成的物体可以成为一个整体进行显示与实现覆盖效果：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914153723336.png" alt="image-20240914153723336" style="zoom:25%;" />

#### 如何使用渲染组Sorting Group

需要在父物体上添加该组件并进行设置，设置选项包含`Sorting Layer`、`Order in Layer`、`Sort At Root`，前两项与Sprite Render相同，第三项设置后将会忽略父物体的排序分组，使得他们可以按照需要进行额外分组划分。

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240914153832263.png" alt="image-20240914153832263" style="zoom: 67%;" />