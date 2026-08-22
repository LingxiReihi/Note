# 如何用Shader Graph创建水面倒影效果

在游戏开发中，我们有些时候会需要一面镜子或者一个水面的效果，这些效果通常是基于shader来实现，但对于很多初学者来讲，别说直接去写shader相关代码，连看懂别人写好的代码都非常困难，那么，有没有一种方法可以让我们不用写代码就实现这种效果呢？答案是有的，Unity官方提供了内置插件Shader Graph，它可以让我们零代码实现各种各样我们需要的效果~~（但是需要付出相对应的性能牺牲）~~，下面的水面倒影效果也是基于Shader Graph来进行实现。

<video src="https://gitee.com/LingxiReihi/pico-go/raw/master/video/QQ20241023-173244-HD.mp4"></video>

## 1. 创建Render Texture

创建方式为`右键->Create->Render Textrue`，将名字更改为想要的名字，这里我取名为`Water Render Textrue`。

![image-20241015170724705](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241015170724705.png)

在创建完成后，我们可以看见目前的Render Texture是黑色的，因为我们暂时没有对他进行任何的设置。

![image-20241015170830771](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241015170830771.png)

## 2. 创建并设置观察相机

这里的相机是非常关键的组件，它是用于获取我们对需要倒影的对象的观察结果并输出到之前创建的Render Texture上。

在`Hierarchy`窗口`右键->Camera`进行创建：

![image-20241015172151302](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241015172151302.png)

创建完成后，可以按照个人需求对其进行命名，这里我就不对其进行修改。

![image-20241015172342937](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241015172342937.png)

创建完成后，首先要删除掉自带的`Audio Listener`组件，否则运行时将会报错（详情见[音频监听器 - Unity 手册](https://docs.unity.cn/cn/2020.3/Manual/class-AudioListener.html)），然后需要保证观察相机与我们的`Main Camera`设置相同，这里可以直接到`Main Camera`中点击`Camera`组件左边的三个点并选择`Copy Component`选项，他将复制这个组建的所有信息：

![image-20241015172825042](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241015172825042.png)

随后到我们的观察相机中，同样点击右侧三个点，选择`Paste Component Values`，它会将刚刚复制的组件中的设置粘贴到当前组件中。

![image-20241015173007074](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241015173007074.png)

（这是可能有些小伙伴会发现选中观察相机后右下角并没有显示场景中的任何物体，这是因为创建时相机坐标出现了问题，建议同样也可以复制`Main Camera`的坐标信息到观察相机，之后再进行调整）。

## 3. 设置相机输出到`Water Render Texture`（在第一部创建的Texture）中，并简单进行配置

在观察相机中，找到`Output`一栏，找到`Ouput Texture`，将`Water Render Texture`拖入进去（或点击右侧圆点进行选择）：

![image-20241015173802461](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241015173802461.png)

我们马上就可以在窗口中看见`Water Render Texture`不再是黑色，而是变成了场景中观察相机范围内的物体的图像，并且相机观察范围也发生了改变（变为在`Water Render Texture`中的默认大小）：

![image-20241023141127798](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023141127798.png)

这个大小可能并不是我们所需要的大小，这时我们可以点击`Water Render Texture`，修改右侧的`Size`属性直到大小合适：

![image-20241015174616795](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241015174616795.png)

然后在对观察相机进行修改，同样也是修改他的`size`属性到一个合适的范围：

![image-20241015175828340](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241015175828340.png)

## 4. Shader Graph启动！

基础的准备工作完成后，终于迎来了重头戏——Shader Graph！我们先选择一个合适的位置创建文件夹，来存储我们后续编写的Shader Graph文件，接下来我们将一步一步实现水面效果。

### 4.1 创建`Shader Graph`文件

在Project窗口右键，选择`Create->Shader Graph->URP->Unlit Shader Graph`创建Shader Graph文件，并给它取名为合适的值，双击可以打开如下所示的编辑界面，这就是我们后续编写Shader Graph的工作界面，其中已经包含有节点`Fragment`，它将是我们渲染结果的输出节点；右下方的`Main Preview`则是最终效果的预览图，可以右键他更改为需要展示的效果。

![image-20241016110737530](https://gitee.com/yimuzhexi/pico-go/raw/master/imgs/image-20241016110737530.png)

### 4.2 先将原图渲染出来

#### 在Shader Graph中进行设置

在正式编写前，我们可以先将观测相机的画面输出到场景中来看看目前的观察效果，通过观察效果可以再次对相机观察范围等进行微调。

右键空界面，选择`Create Node`，在输入框中输入`Texture`，选择`Sample Texture 2D`将节点添加到场景中：

![image-20241023141624763](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023141624763.png)

在左侧的`Texture`属性中选择刚刚创建好的`Water Render Texture`，可以看见下面那已经变成了与`Texture`相同的样子：

![image-20241023141830406](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023141830406.png)

再将`RGBA(4)`输出到`Fragment`节点中的`Base Color(3)`，可以看见右下方`Main Preview`已经变成相同的样子：

![image-20241023142149920](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023142149920.png)

为了方便后续更改使用，我们也可以单独创建一个`Texture 2D`属性节点，方法为在左下角与这个文件同名的窗口中点击`+`号，选择`Texture 2D`，命名为合适的名称，再拖入主窗口连接到`Texture`上，选中该节点设置默认值为`Water Render Texture`,：

![image-20241023162051474](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023162051474.png)

#### 创建材质球输出渲染结果并将材质球添加到水面上

在`Project`窗口右键，依次点击`Create->Material`创建材质球，为材质球取上一个名字（这里我命名为`Water Material`：

![image-20241023142557156](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023142557156.png)

直接将`Shader Graph`文件拖到材质球上，可以看见材质球图标变成了`Shader Graph`中`Main Preview`的样子（如果没有改变重新进入该文件夹刷新即可）：

![image-20241023142950954](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023142950954.png)

最后将材质球拖放到显示水面的位置或者他的`Sprite`组件中的`Material`一栏：

![image-20241023143101368](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023143101368.png)

最终效果：

![QQ20241023-143135 00_00_00-00_00_30](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/QQ20241023-143135%2000_00_00-00_00_30.gif)

### 4.3 实现水面倒影的上下颠倒

实现上下颠倒的效果需要添加一个新的节点，名为`Tiling And Offset`，他可以设置图片平铺范围和显示偏移，最终输出UV坐标（用于控制图片在显示器上显示位置的已经进行归一化了的坐标）。

所以第一步，先添加一个`Tiling And Offset`节点（添加节点方式在前面写过就不再赘述），在节点中可以看见三个属性值，分别是`UV`、`Tiling`和`Offset`，其中，`Tiling`控制图片的平铺方向和范围，`Offset`则控制图片显示偏移值

其中我们主要对`Tiling`和`Offset`进行修改，为了更直观看见修改效果，我们可以直接将他的输出连接到`Sample Texture 2D`中的`UV(2)`。

![image-20241023145429978](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023145429978.png)

在水面中的倒影主要实现上下颠倒，左右不进行改变，所以首先要改变`Tiling`中的y值为-1让他反向平铺，在更改`Offset`中的y值为1，让其向上偏移显示出反向平铺后的图像：

![image-20241023151002225](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023151002225.png)

在场景中也直接进行了自动更改：

![image-20241023151043366](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023151043366.png)

### 4.4 实现水面波纹

一般而言，睡眠不会绝对静止，有风吹过等等原因都会有波纹产生，所以为了更加真实，为其添加动态波纹效果。

#### 通过添加噪点模拟水面波纹偏移

为了实现波纹效果，可以使用噪点来改变`Offset`的偏移值，添加一个噪声节点，输入`noise`，选择`Sample Noise`。

![image-20241023154845127](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023154845127.png)

但是普通噪声节点无法动态改变，为了实现动态功能，我们需要一个时间节点`Time`和`Gradient Noise`节点：

![image-20241023160205981](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023160205981.png)

将`Time`和`Gradient Noise`进行加法运算，输出到`Sample Noise`节点中，可以看见`Sample Noise`节点下方开始运动，但是速度过快：

![QQ20241023-16516 00_00_00-00_00_30](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/QQ20241023-16516%2000_00_00-00_00_30.gif)

因此我们将时间先乘以一个浮点型影响因子，给他命名为`Speed`，默认值设置为0.05f，可以看见变换明显变缓了许多：

![QQ20241023-16105 00_00_00-00_00_30](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/QQ20241023-16105%2000_00_00-00_00_30.gif)

而对于变换的大小，我们也可以添加一个名为`Wave Scale`的浮点数属性，便于后续设置变化大小，这里默认值设置为3，此时的效果为：

![QQ20241023-161417 00_00_00-00_00_30](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/QQ20241023-161417%2000_00_00-00_00_30.gif)

#### 将偏移运用到图像上

如果直接将`Sample Noise`输出到`Sample Texture`中的`Offset`，会发现图片偏移到了一个过于离谱的程度，这是因为同时对x轴和y轴进行了更改，导致图片扭曲过大，同时还因为边界没有任何像素导致出现较大的黑块，实际上需要修改的仅为x轴即可，让他只在x轴有部分偏移，这样可以避免出现大量的黑块。

直接输出时的效果：

![QQ20241023-162428 00_00_00-00_00_30](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/QQ20241023-162428%2000_00_00-00_00_30.gif)

如果只需要修改x轴，我们需要一个二维向量，设置他的y轴永远为1，x轴随噪声进行改变，此时可以看见图片偏移变得稍显合理，但是偏移量还是非常大：

![QQ20241023-163522-HD 00_00_00-00_00_30](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/QQ20241023-163522-HD%2000_00_00-00_00_30.gif)

![QQ20241023-163711-HD 00_00_00-00_00_30](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/QQ20241023-163711-HD%2000_00_00-00_00_30.gif)

这是因为x轴偏移过多造成的图像偏移范围变大，只需要更改一下偏移的范围即可，具体做法即为用一个相对较小的数值与原本偏移的值进行乘法运算，修正偏移量，这里我使用的值为0.05：

![image-20241023164119226](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023164119226.png)

此时他的效果就仿佛像微风吹拂水面一样：

![QQ20241023-16425 00_00_00-00_00_30](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/QQ20241023-16425%2000_00_00-00_00_30.gif)

### 4.5 实现更加“真实”的水

通常而言，海水会偏向于蓝色，要实现这个效果我们可以用对应的颜色与这张图片进行叠加，例如这里我使用颜色比较深的蓝绿色与设置好的图片进行叠加：

![image-20241023164957301](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023164957301.png)

![image-20241023165026028](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/image-20241023165026028.png)

此时场景中水面便会有蓝绿色元素存在：

![QQ20241023-165310 00_00_00-00_00_30](https://gitee.com/LingxiReihi/pico-go/raw/master/imgs/QQ20241023-165310%2000_00_00-00_00_30.gif)