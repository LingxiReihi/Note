## Unity编辑器界面

### 编辑器默认界面布局

打开Unity编辑器，初次启动后看见的界面如下图所示：

![image-20240925145638800](C:/Users/YimuZ/AppData/Roaming/Typora/typora-user-images/image-20240925145638800.png)

将会发现整个屏幕被分为了不同的标签页（Tabs）进行显示，这里也可以称为视图（View）、窗口（Window）、编辑器（Editor）。

### 打开和关闭标签页



## 素材导入

### Unity官网购买素材或插件导入方法

点击编辑器上方`Window`窗口，点击`Package Manager`打开包管理界面：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240912174541569.png" alt="image-20240912174541569" style="zoom:50%;" />

在Package Manager中点击`Packages`选择`My Assets`，进入个人已购买素材库：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240912175058545.png" alt="image-20240912175058545" style="zoom:50%;" />

在左侧列表选中需要的素材或插件，点击右上角`Download`进行下载：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240912175409980.png" alt="image-20240912175409980" style="zoom:50%;" />

下载完成后，点击`Import`进行素材导入：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240912175509305.png" alt="image-20240912175509305" style="zoom:50%;" />

### 非官网素材导入

直接将文件拖入编辑器内`Assets`文件夹或其他新建的文件夹即可。

### 非官网插件导入

打开`Package Manager`界面后，点击左上角`+`，选择对应导入方式即可：

<img src="https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20240912175755871.png" alt="image-20240912175755871" style="zoom:50%;" />

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